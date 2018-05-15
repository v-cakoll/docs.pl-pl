---
title: 'Porady: importowanie niestandardowych WSDL'
ms.date: 03/30/2017
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
ms.openlocfilehash: 33762afffca6e90cb32c358bee6d9f29ca609994
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-import-custom-wsdl"></a><span data-ttu-id="a22dc-102">Porady: importowanie niestandardowych WSDL</span><span class="sxs-lookup"><span data-stu-id="a22dc-102">How to: Import Custom WSDL</span></span>
<span data-ttu-id="a22dc-103">W tym temacie opisano sposób importu WSDL niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="a22dc-103">This topic describes how to import custom WSDL.</span></span> <span data-ttu-id="a22dc-104">Aby obsługiwać niestandardowe WSDL, musisz zaimplementować <xref:System.ServiceModel.Description.IWsdlImportExtension> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a22dc-104">To handle the custom WSDL, you must implement the <xref:System.ServiceModel.Description.IWsdlImportExtension> interface.</span></span>  
  
### <a name="to-import-custom-wsdl"></a><span data-ttu-id="a22dc-105">Aby zaimportować niestandardowy WSDL</span><span class="sxs-lookup"><span data-stu-id="a22dc-105">To import custom WSDL</span></span>  
  
1.  <span data-ttu-id="a22dc-106">Implementowanie <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span><span class="sxs-lookup"><span data-stu-id="a22dc-106">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span></span> <span data-ttu-id="a22dc-107">Implementowanie <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> metodą zmiany metadanych przed ich zaimportowaniem.</span><span class="sxs-lookup"><span data-stu-id="a22dc-107">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> method to modify the metadata before it is imported.</span></span> <span data-ttu-id="a22dc-108">Implementowanie <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> i <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> metody w celu zmodyfikowania kontrakty i zaimportowane z metadanych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="a22dc-108">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> and <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> methods to modify contracts and endpoints imported from the metadata.</span></span> <span data-ttu-id="a22dc-109">Dostępu do importowanych kontraktu lub punktu końcowego, należy użyć odpowiedniego obiektu kontekstu (<xref:System.ServiceModel.Description.WsdlContractConversionContext> lub <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):</span><span class="sxs-lookup"><span data-stu-id="a22dc-109">To access the imported contract or endpoint, use the corresponding context object (<xref:System.ServiceModel.Description.WsdlContractConversionContext> or <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):</span></span>  
  
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
  
2.  <span data-ttu-id="a22dc-110">Konfigurowanie aplikacji klienta do używania niestandardowej importerów WSDL.</span><span class="sxs-lookup"><span data-stu-id="a22dc-110">Configure the client application to use the custom WSDL importer.</span></span> <span data-ttu-id="a22dc-111">Należy pamiętać, że jeśli używasz Svcutil.exe, należy dodać tę konfigurację do pliku konfiguracji dla Svcutil.exe (Svcutil.exe.config):</span><span class="sxs-lookup"><span data-stu-id="a22dc-111">Note that if you are using Svcutil.exe, you should add this configuration to the configuration file for Svcutil.exe (Svcutil.exe.config):</span></span>  
  
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
  
3.  <span data-ttu-id="a22dc-112">Utwórz nową <xref:System.ServiceModel.Description.WsdlImporter> wystąpienia (przekazując <xref:System.ServiceModel.Description.MetadataSet> wystąpienia, które zawiera dokumentów WSDL, które chcesz zaimportować) i Wywołaj <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:</span><span class="sxs-lookup"><span data-stu-id="a22dc-112">Create a new <xref:System.ServiceModel.Description.WsdlImporter> instance (passing in the <xref:System.ServiceModel.Description.MetadataSet> instance that contains the WSDL documents that you want to import), and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);          System.Collections.ObjectModel.Collection<ContractDescription> contracts  = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a22dc-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a22dc-113">See Also</span></span>  
 [<span data-ttu-id="a22dc-114">Metadane</span><span class="sxs-lookup"><span data-stu-id="a22dc-114">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="a22dc-115">Eksportowanie i importowanie metadanych</span><span class="sxs-lookup"><span data-stu-id="a22dc-115">Exporting and Importing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)  
 [<span data-ttu-id="a22dc-116">Niestandardowa publikacja WSDL</span><span class="sxs-lookup"><span data-stu-id="a22dc-116">Custom WSDL Publication</span></span>](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)
