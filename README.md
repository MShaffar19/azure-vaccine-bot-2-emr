# Abstract

As the COVID-19 Vaccine rollout increases in volume, providers are preparing for a massive influx of patient registrations. Many of these provider's EMR (Electronic Medical Records) systems are already heavily burdened from daily work and cannot handle a spike in record entries or new patients, which will be the case with vaccine registration. Many of these individuals will not already be patients of that particular Medical Provider and may never visit them again.  

This is why we're creating an "eventual consistency" model for patient scheduling, record creation and entry. With this design, the Medical Provider can decide at what frequency they can ingest new records from the cloud-scale Vaccine Eligibility Azure Health Bot. Whether they can handle 1 new record per second, or batch loading them between certain hours, this system will use HIPPA and HITRUST certified Azure services to complete the scheduling and become eventually consistent with the EMR by way of Azure API for FHIR, and in-turn respect the rate limiting requirements of the Provider to ensure uptime and functionality for their daily operations.

<img src="images\vaccine-bot-2-emr.png" width="100%"/>

# Solution Assumptions/Guardrails

Our basic architecture assumes some guardrails.

First, The Azure FHIR API is not the final system of record for the EMR.  The problem we are solving is to isolate the EMR from the load introduced by the sudden traffic generated by a healthbot instance.  

Second, the Azure Healthbot will perform real time interaction with a Azure FHIR Api instance

Third, The Azure FHIR Api instance will manage the calendar for vaccine appointments, with the information propagating back to the source of truth EMR.

Fourth, all information deemed needed will reach the source of truth EMR.
## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft 
trademarks or logos is subject to and must follow 
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
