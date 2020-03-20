---
title: 'Instrukcje: importowanie niestandardowych informacji w formacie WSDL'
ms.date: 03/30/2017
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
ms.openlocfilehash: 614842f2d77d967e0a6d4841e5e5e4fcc8805580
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185546"
---
# <a name="how-to-import-custom-wsdl"></a><span data-ttu-id="e0cfe-102">Instrukcje: importowanie niestandardowych informacji w formacie WSDL</span><span class="sxs-lookup"><span data-stu-id="e0cfe-102">How to: Import Custom WSDL</span></span>
<span data-ttu-id="e0cfe-103">W tym temacie opisano sposób importowania niestandardowego WSDL.</span><span class="sxs-lookup"><span data-stu-id="e0cfe-103">This topic describes how to import custom WSDL.</span></span> <span data-ttu-id="e0cfe-104">Aby obsłużyć niestandardowe WSDL, należy zaimplementować <xref:System.ServiceModel.Description.IWsdlImportExtension> interfejs.</span><span class="sxs-lookup"><span data-stu-id="e0cfe-104">To handle the custom WSDL, you must implement the <xref:System.ServiceModel.Description.IWsdlImportExtension> interface.</span></span>  
  
### <a name="to-import-custom-wsdl"></a><span data-ttu-id="e0cfe-105">Aby zaimportować niestandardowe WSDL</span><span class="sxs-lookup"><span data-stu-id="e0cfe-105">To import custom WSDL</span></span>  
  
1. <span data-ttu-id="e0cfe-106">Zaimplementuj <xref:System.ServiceModel.Description.IWsdlImportExtension>plik .</span><span class="sxs-lookup"><span data-stu-id="e0cfe-106">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span></span> <span data-ttu-id="e0cfe-107">Zaimplementuj <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> metodę modyfikowania metadanych przed zaimportowaniem.</span><span class="sxs-lookup"><span data-stu-id="e0cfe-107">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> method to modify the metadata before it is imported.</span></span> <span data-ttu-id="e0cfe-108">Zaimplementuj <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> metody modyfikowania <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> kontraktów i punktów końcowych zaimportowanych z metadanych.</span><span class="sxs-lookup"><span data-stu-id="e0cfe-108">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> and <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> methods to modify contracts and endpoints imported from the metadata.</span></span> <span data-ttu-id="e0cfe-109">Aby uzyskać dostęp do importowanego kontraktu lub punktu<xref:System.ServiceModel.Description.WsdlContractConversionContext> <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>końcowego, użyj odpowiedniego obiektu kontekstowego ( lub ):</span><span class="sxs-lookup"><span data-stu-id="e0cfe-109">To access the imported contract or endpoint, use the corresponding context object (<xref:System.ServiceModel.Description.WsdlContractConversionContext> or <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):</span></span>  
  
    ```csharp
    public class WsdlDocumentationImporter : IWsdlImportExtension
    {
        public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)
        {
            // Contract documentation
            if (context.WsdlPortType.Documentation != null)
            {
                context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));
            }
            // Operation documentation
            foreach (Operation operation in context.WsdlPortType.Operations)
            {
                if (operation.Documentation != null)
                {
                    OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);
                    if (operationDescription != null)
                    {
                        operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));
                    }
                }
            }
        }

        public void BeforeImport(ServiceDescriptionCollection wsdlDocuments, XmlSchemaSet xmlSchemas, ICollection<XmlElement> policy)
        {
            Console.WriteLine("BeforeImport called.");
        }

        public void ImportEndpoint(WsdlImporter importer, WsdlEndpointConversionContext context)
        {
            Console.WriteLine("ImportEndpoint called.");
        }
    }
    ```
  
2. <span data-ttu-id="e0cfe-110">Skonfiguruj aplikację kliencką do używania niestandardowego importera WSDL.</span><span class="sxs-lookup"><span data-stu-id="e0cfe-110">Configure the client application to use the custom WSDL importer.</span></span> <span data-ttu-id="e0cfe-111">Należy zauważyć, że w przypadku korzystania z programu Svcutil.exe należy dodać tę konfigurację do pliku konfiguracyjnego programu Svcutil.exe (Svcutil.exe.config):</span><span class="sxs-lookup"><span data-stu-id="e0cfe-111">Note that if you are using Svcutil.exe, you should add this configuration to the configuration file for Svcutil.exe (Svcutil.exe.config):</span></span>  
  
    ```xml  
    <system.serviceModel>  
          <client>  
            <endpoint
              address="http://localhost:8000/Fibonacci"
              binding="wsHttpBinding"  
              contract="IFibonacci"  
            />  
            <metadata>  
              <wsdlImporters>  
                <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
              </wsdlImporters>  
            </metadata>  
          </client>  
        </system.serviceModel>  
    ```  
  
3. <span data-ttu-id="e0cfe-112">Utwórz <xref:System.ServiceModel.Description.WsdlImporter> nowe wystąpienie <xref:System.ServiceModel.Description.MetadataSet> (przechodząc w wystąpieniu, które zawiera dokumenty WSDL, które chcesz zaimportować) i zadzwoń: <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A></span><span class="sxs-lookup"><span data-stu-id="e0cfe-112">Create a new <xref:System.ServiceModel.Description.WsdlImporter> instance (passing in the <xref:System.ServiceModel.Description.MetadataSet> instance that contains the WSDL documents that you want to import), and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:</span></span>  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e0cfe-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0cfe-113">See also</span></span>

- [<span data-ttu-id="e0cfe-114">Metadane</span><span class="sxs-lookup"><span data-stu-id="e0cfe-114">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="e0cfe-115">Eksportowanie i importowanie metadanych</span><span class="sxs-lookup"><span data-stu-id="e0cfe-115">Exporting and Importing Metadata</span></span>](../feature-details/exporting-and-importing-metadata.md)
- [<span data-ttu-id="e0cfe-116">Niestandardowa publikacja WSDL</span><span class="sxs-lookup"><span data-stu-id="e0cfe-116">Custom WSDL Publication</span></span>](../samples/custom-wsdl-publication.md)
