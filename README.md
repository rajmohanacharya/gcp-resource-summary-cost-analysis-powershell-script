# GCP Resource Summary & Cost Analysis Script

A comprehensive PowerShell script that provides detailed insights into your Google Cloud Platform (GCP) resources, including real-time cost analysis with multi-currency support.

![PowerShell](https://img.shields.io/badge/PowerShell-5.1%2B-blue)
![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey)
![License](https://img.shields.io/badge/License-MIT-green)
![GCP](https://img.shields.io/badge/GCP-Compatible-orange)

## 🌟 Features

- **📊 Complete Resource Inventory**
  - GKE Clusters and Kubernetes workloads
  - Compute instances (VMs/Nodes) with detailed specifications
  - Network resources (VPC, Subnets, Load Balancers, Firewall rules)
  - Storage resources (Persistent Disks, Cloud Storage, PVCs)
  
- **💰 Real-Time Cost Analysis**
  - Automatic USD to INR currency conversion using live exchange rates
  - Detailed cost breakdown by resource type
  - Monthly, daily, and hourly cost projections
  - Free trial credit burn rate calculation

- **📈 Resource Utilization Metrics**
  - CPU and memory allocation tracking
  - Node resource usage monitoring
  - Available vs allocated resources visualization

- **🔌 Access Guide**
  - External IP addresses and connection endpoints
  - kubectl commands for cluster access
  - Load balancer access URLs with curl examples
  - Direct links to GCP Console

- **💳 Billing Information**
  - Billing account status and details
  - Free trial timeline tracking
  - Budget alert threshold configuration
  - Days since project creation

## 📋 Prerequisites

Before running this script, ensure you have:

- **Google Cloud SDK** (`gcloud`) installed and authenticated
- **kubectl** installed and configured (for GKE cluster analysis)
- **PowerShell 5.1+** (Windows) or **PowerShell Core 7+** (Linux/macOS)
- Active **GCP project** with appropriate IAM permissions
- Internet connection (for live exchange rate API)

### Required GCP Permissions

Your account needs the following IAM roles:
- `roles/viewer` (Project-level read access)
- `roles/container.viewer` (GKE cluster access)
- `roles/billing.viewer` (Billing information access)

## 🚀 Installation

### Option 1: Clone the Repository

- git clone https://github.com/rajmohanacharya/gcp-resource-summary-cost-analysis-powershell-script.git
- cd gcp-resource-summary

### Option 2: Direct Download

Download the `Get-GCPResourceSummary.ps1` file directly from this repository.

## 💻 Usage

### Basic Usage (Current Active Project)
.\Get-GCPResourceSummary.ps1


### Specify a Project
.\Get-GCPResourceSummary.ps1 -ProjectId "my-gcp-project-123"


### Linux/macOS
pwsh ./Get-GCPResourceSummary.ps1

## 📖 Output Sections

The script generates a comprehensive report with the following sections:

1. **GCP Project & Billing Information**
   - Project ID, Number, Name
   - High-level resource count
   - Billing account details
   - Free trial status and timeline
   - Budget alerts configuration

2. **GKE Cluster Details**
   - Cluster name, location, and status
   - Kubernetes version information
   - Node count and configuration

3. **Compute Resources**
   - Node specifications (CPU, Memory, Disk)
   - IP addresses (Internal and External)
   - Container runtime details
   - Pods running per node

4. **Network Resources**
   - VPC networks and subnets
   - Cloud NAT configuration
   - Firewall rules
   - Load balancers with ports
   - External IP addresses

5. **Storage Resources**
   - Persistent disks
   - Cloud Storage buckets
   - Kubernetes PVCs

6. **Kubernetes Workloads**
   - Pods, Deployments, Services count
   - Pod status and resource requests

7. **Resource Utilization**
   - CPU and memory allocation
   - Available resources

8. **Cost Analysis**
   - Compute, storage, and network costs
   - USD and INR pricing
   - Monthly, daily, hourly projections
   - Free trial burn rate

9. **Resource Access Guide**
   - External IP access instructions
   - kubectl connection commands
   - Load balancer URLs
   - GCP Console quick links

## 🔧 Configuration

### Customize Exchange Rate

To use a different exchange rate or currency, modify the API endpoint:

$response = Invoke-RestMethod -Uri "https://open.er-api.com/v6/latest/USD"
$usdToInr = [math]::Round($response.rates.INR, 2)

Replace `INR` with your desired currency code (e.g., `EUR`, `GBP`, `JPY`).

### Adjust Cost Estimates

Cost calculations are based on standard GCP pricing. Update these variables in the script:

$computeCostPerNode = 24.50 # e2-medium cost
$diskCostPerGB = 0.040 # Standard persistent disk
$lbMonthlyCost = 18.00 # Per forwarding rule


## 📊 Sample Output

<img width="615" height="927" alt="image" src="https://github.com/user-attachments/assets/b41ce13f-5ebb-413d-9078-4bc7300a4de3" />
<img width="570" height="746" alt="image" src="https://github.com/user-attachments/assets/45cac64d-2bcc-4149-9439-1bf62ed81f3f" />
<img width="480" height="750" alt="image" src="https://github.com/user-attachments/assets/4cb16019-597c-4960-b0f7-debd8cbac732" />
<img width="1194" height="741" alt="image" src="https://github.com/user-attachments/assets/1bfbb540-16bd-4b0e-8602-508cb1fe79a4" />


## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🐛 Known Issues

- Budget information requires `gcloud beta billing` commands
- Some network metrics may not be available in all GCP regions
- Free trial detection is approximate based on project creation date

## 📮 Support

If you encounter any issues or have questions:

- Open an [Issue](https://github.com/yourusername/gcp-resource-summary/issues)
- Check existing [Discussions](https://github.com/yourusername/gcp-resource-summary/discussions)

## 🙏 Acknowledgments

- Exchange rate data provided by [ExchangeRate-API](https://www.exchangerate-api.com/)
- Inspired by GCP cost management best practices
- Community feedback and contributions

## 📚 Additional Resources

- [Google Cloud SDK Documentation](https://cloud.google.com/sdk/docs)
- [GCP Pricing Calculator](https://cloud.google.com/products/calculator)
- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [PowerShell Documentation](https://docs.microsoft.com/en-us/powershell/)

---

**⭐ If you find this script helpful, please consider giving it a star!**

