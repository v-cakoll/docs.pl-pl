---
title: 'Instrukcje: Pisanie rozszerzenia dla elementu ServiceContractGenerator'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c62aa9ac582e93bb86399472e47c41fdb6fad2d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="efaac-102">Instrukcje: Pisanie rozszerzenia dla elementu ServiceContractGenerator</span><span class="sxs-lookup"><span data-stu-id="efaac-102">How to: Write an Extension for the ServiceContractGenerator</span></span>
<span data-ttu-id="efaac-103">W tym temacie opisano sposób pisanie rozszerzenia dla <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span><span class="sxs-lookup"><span data-stu-id="efaac-103">This topic describes how to write an extension for the <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span></span> <span data-ttu-id="efaac-104">Można to zrobić z zastosowaniem <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interfejsu na zachowanie operacji lub implementacja <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interfejsu na zachowanie kontraktu.</span><span class="sxs-lookup"><span data-stu-id="efaac-104">This can be done by implementing the <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interface on an operation behavior or implementing the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span> <span data-ttu-id="efaac-105">W tym temacie przedstawiono sposób wykonania <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interfejsu na zachowanie kontraktu.</span><span class="sxs-lookup"><span data-stu-id="efaac-105">This topic shows how to implement the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span>  
  
 <span data-ttu-id="efaac-106"><xref:System.ServiceModel.Description.ServiceContractGenerator> Generuje kontraktów usług, typy klientów i konfiguracji klienta z <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, i <xref:System.ServiceModel.Channels.Binding> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="efaac-106">The <xref:System.ServiceModel.Description.ServiceContractGenerator> generates service contracts, client types, and client configurations from <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances.</span></span> <span data-ttu-id="efaac-107">Zazwyczaj należy zaimportować <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, i <xref:System.ServiceModel.Channels.Binding> wystąpień z metadanych usługi, a następnie użyć tych obiektów do generowania kodu do wywołania tej usługi.</span><span class="sxs-lookup"><span data-stu-id="efaac-107">Typically, you import <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances from service metadata and then use these instances to generate code to call the service.</span></span> <span data-ttu-id="efaac-108">W tym przykładzie <xref:System.ServiceModel.Description.IWsdlImportExtension> implementacji służy do przetwarzania adnotacje WSDL, a następnie dodaj rozszerzenia generacji kodu do następującą liczbę zaimportowanych kontraktów do generowania komentarzy w wygenerowanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="efaac-108">In this example, an <xref:System.ServiceModel.Description.IWsdlImportExtension> implementation is used to process WSDL annotations and then add code generation extensions to the imported contracts to generate comments on the generated code.</span></span>  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="efaac-109">Aby pisanie rozszerzenia dla elementu ServiceContractGenerator</span><span class="sxs-lookup"><span data-stu-id="efaac-109">To write an extension for the ServiceContractGenerator</span></span>  
  
1.  <span data-ttu-id="efaac-110">Implementowanie <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span><span class="sxs-lookup"><span data-stu-id="efaac-110">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="efaac-111">Aby zmodyfikować kontraktu usługi wygenerowanego, użyj <xref:System.ServiceModel.Description.ServiceContractGenerationContext> przekazany wystąpienia <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> metody.</span><span class="sxs-lookup"><span data-stu-id="efaac-111">To modify the generated service contract, use the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instance passed into the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> method.</span></span>  
  
    ```  
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2.  <span data-ttu-id="efaac-112">Implementowanie <xref:System.ServiceModel.Description.IWsdlImportExtension> na tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="efaac-112">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension> on the same class.</span></span> <span data-ttu-id="efaac-113"><xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> Metody może przetwarzać określonego rozszerzenia WSDL (WSDL adnotacje w tym przypadku), dodając rozszerzenie generowania kodu do importowanego <xref:System.ServiceModel.Description.ContractDescription> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="efaac-113">The <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method can process a specific WSDL extension (WSDL annotations in this case) by adding a code generation extension to the imported <xref:System.ServiceModel.Description.ContractDescription> instance.</span></span>  
  
    ```  
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
    ```  
  
3.  <span data-ttu-id="efaac-114">Do konfiguracji klienta, należy dodać importerów WSDL.</span><span class="sxs-lookup"><span data-stu-id="efaac-114">Add the WSDL importer to your client configuration.</span></span>  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4.  <span data-ttu-id="efaac-115">W kodzie klienta, tworzenie `MetadataExchangeClient` i Wywołaj `GetMetadata`.</span><span class="sxs-lookup"><span data-stu-id="efaac-115">In the client code, create a `MetadataExchangeClient` and call `GetMetadata`.</span></span>  
  
    ```  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5.  <span data-ttu-id="efaac-116">Utwórz `WsdlImporter` i Wywołaj `ImportAllContracts`.</span><span class="sxs-lookup"><span data-stu-id="efaac-116">Create a `WsdlImporter` and call `ImportAllContracts`.</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6.  <span data-ttu-id="efaac-117">Utwórz `ServiceContractGenerator` i Wywołaj `GenerateServiceContractType` dla każdej umowy.</span><span class="sxs-lookup"><span data-stu-id="efaac-117">Create a `ServiceContractGenerator` and call `GenerateServiceContractType` for each contract.</span></span>  
  
    ```  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7.  <span data-ttu-id="efaac-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>jest wywoływana automatycznie dla każdej umowy zachowanie na danego kontraktu, który implementuje <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span><span class="sxs-lookup"><span data-stu-id="efaac-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> is called automatically for each contract behavior on a given contract that implements <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="efaac-119">Tej metody można następnie zmodyfikować <xref:System.ServiceModel.Description.ServiceContractGenerationContext> przekazany.</span><span class="sxs-lookup"><span data-stu-id="efaac-119">This method can then modify the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passed in.</span></span> <span data-ttu-id="efaac-120">Komentarze są dodawane w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="efaac-120">In this example comments are added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efaac-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="efaac-121">See Also</span></span>  
 [<span data-ttu-id="efaac-122">Metadane</span><span class="sxs-lookup"><span data-stu-id="efaac-122">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="efaac-123">Instrukcje: importowanie niestandardowych informacji w formacie WSDL</span><span class="sxs-lookup"><span data-stu-id="efaac-123">How to: Import Custom WSDL</span></span>](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
