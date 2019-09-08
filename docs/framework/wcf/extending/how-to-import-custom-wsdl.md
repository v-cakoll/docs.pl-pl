---
title: 'Instrukcje: importowanie niestandardowych plików WSDL'
ms.date: 03/30/2017
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
ms.openlocfilehash: 930cb92d8193ba3ffc1f62191f2012e104091190
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796989"
---
# <a name="how-to-import-custom-wsdl"></a><span data-ttu-id="17f04-102">Instrukcje: importowanie niestandardowych plików WSDL</span><span class="sxs-lookup"><span data-stu-id="17f04-102">How to: Import Custom WSDL</span></span>
<span data-ttu-id="17f04-103">W tym temacie opisano sposób importowania niestandardowego WSDL.</span><span class="sxs-lookup"><span data-stu-id="17f04-103">This topic describes how to import custom WSDL.</span></span> <span data-ttu-id="17f04-104">Aby obsłużyć niestandardowy WSDL, należy zaimplementować <xref:System.ServiceModel.Description.IWsdlImportExtension> interfejs.</span><span class="sxs-lookup"><span data-stu-id="17f04-104">To handle the custom WSDL, you must implement the <xref:System.ServiceModel.Description.IWsdlImportExtension> interface.</span></span>  
  
### <a name="to-import-custom-wsdl"></a><span data-ttu-id="17f04-105">Aby zaimportować niestandardowy element WSDL</span><span class="sxs-lookup"><span data-stu-id="17f04-105">To import custom WSDL</span></span>  
  
1. <span data-ttu-id="17f04-106">Implementacja <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span><span class="sxs-lookup"><span data-stu-id="17f04-106">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span></span> <span data-ttu-id="17f04-107">Zaimplementuj <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> metodę, aby zmodyfikować metadane przed zaimportowaniem.</span><span class="sxs-lookup"><span data-stu-id="17f04-107">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> method to modify the metadata before it is imported.</span></span> <span data-ttu-id="17f04-108">Zaimplementuj metody <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29>i, aby zmodyfikować kontrakty i punkty końcowe zaimportowane z metadanych. <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29></span><span class="sxs-lookup"><span data-stu-id="17f04-108">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> and <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> methods to modify contracts and endpoints imported from the metadata.</span></span> <span data-ttu-id="17f04-109">Aby uzyskać dostęp do zaimportowanego kontraktu lub punktu końcowego, użyj odpowiedniego<xref:System.ServiceModel.Description.WsdlContractConversionContext> obiektu <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>kontekstu (lub):</span><span class="sxs-lookup"><span data-stu-id="17f04-109">To access the imported contract or endpoint, use the corresponding context object (<xref:System.ServiceModel.Description.WsdlContractConversionContext> or <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):</span></span>  
  
    ```  
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
  
2. <span data-ttu-id="17f04-110">Skonfiguruj aplikację kliencką tak, aby korzystała z niestandardowego importera WSDL.</span><span class="sxs-lookup"><span data-stu-id="17f04-110">Configure the client application to use the custom WSDL importer.</span></span> <span data-ttu-id="17f04-111">Należy pamiętać, że jeśli używasz programu Svcutil. exe, należy dodać tę konfigurację do pliku konfiguracji programu Svcutil. exe (Svcutil. exe. config):</span><span class="sxs-lookup"><span data-stu-id="17f04-111">Note that if you are using Svcutil.exe, you should add this configuration to the configuration file for Svcutil.exe (Svcutil.exe.config):</span></span>  
  
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
  
3. <span data-ttu-id="17f04-112">Utwórz nowe <xref:System.ServiceModel.Description.WsdlImporter> wystąpienie (przekazanie <xref:System.ServiceModel.Description.MetadataSet> wystąpienia zawierającego dokumenty WSDL, które chcesz zaimportować) i Wywołaj <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:</span><span class="sxs-lookup"><span data-stu-id="17f04-112">Create a new <xref:System.ServiceModel.Description.WsdlImporter> instance (passing in the <xref:System.ServiceModel.Description.MetadataSet> instance that contains the WSDL documents that you want to import), and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);          System.Collections.ObjectModel.Collection<ContractDescription> contracts  = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="17f04-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="17f04-113">See also</span></span>

- [<span data-ttu-id="17f04-114">Metadane</span><span class="sxs-lookup"><span data-stu-id="17f04-114">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="17f04-115">Eksportowanie i importowanie metadanych</span><span class="sxs-lookup"><span data-stu-id="17f04-115">Exporting and Importing Metadata</span></span>](../feature-details/exporting-and-importing-metadata.md)
- [<span data-ttu-id="17f04-116">Niestandardowa publikacja WSDL</span><span class="sxs-lookup"><span data-stu-id="17f04-116">Custom WSDL Publication</span></span>](../samples/custom-wsdl-publication.md)
