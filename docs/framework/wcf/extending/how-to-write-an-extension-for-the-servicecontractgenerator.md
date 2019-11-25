---
title: 'Instrukcje: Pisanie rozszerzenia dla elementu ServiceContractGenerator'
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: 68b380a40448f21ba770aa47c7188b818fa8f9e7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975879"
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="1ce77-102">Instrukcje: Pisanie rozszerzenia dla elementu ServiceContractGenerator</span><span class="sxs-lookup"><span data-stu-id="1ce77-102">How to: Write an Extension for the ServiceContractGenerator</span></span>
<span data-ttu-id="1ce77-103">W tym temacie opisano sposób pisania rozszerzenia dla <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span><span class="sxs-lookup"><span data-stu-id="1ce77-103">This topic describes how to write an extension for the <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span></span> <span data-ttu-id="1ce77-104">Można to zrobić, implementując interfejs <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> w przypadku działania operacji lub implementując interfejs <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> na podstawie zachowania kontraktu.</span><span class="sxs-lookup"><span data-stu-id="1ce77-104">This can be done by implementing the <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interface on an operation behavior or implementing the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span> <span data-ttu-id="1ce77-105">W tym temacie pokazano, jak zaimplementować interfejs <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> na zachowanie kontraktu.</span><span class="sxs-lookup"><span data-stu-id="1ce77-105">This topic shows how to implement the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span>  
  
 <span data-ttu-id="1ce77-106"><xref:System.ServiceModel.Description.ServiceContractGenerator> generuje kontrakty usługi, typy klientów i konfiguracje klientów z wystąpień <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>i <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="1ce77-106">The <xref:System.ServiceModel.Description.ServiceContractGenerator> generates service contracts, client types, and client configurations from <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances.</span></span> <span data-ttu-id="1ce77-107">Zazwyczaj można zaimportować wystąpienia <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>i <xref:System.ServiceModel.Channels.Binding> z metadanych usługi, a następnie użyć tych wystąpień do wygenerowania kodu w celu wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="1ce77-107">Typically, you import <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances from service metadata and then use these instances to generate code to call the service.</span></span> <span data-ttu-id="1ce77-108">W tym przykładzie implementacja <xref:System.ServiceModel.Description.IWsdlImportExtension> jest używana do przetwarzania adnotacji WSDL, a następnie dodawania rozszerzeń generowania kodu do importowanych kontraktów w celu generowania komentarzy dotyczących wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="1ce77-108">In this example, an <xref:System.ServiceModel.Description.IWsdlImportExtension> implementation is used to process WSDL annotations and then add code generation extensions to the imported contracts to generate comments on the generated code.</span></span>  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="1ce77-109">Aby napisać rozszerzenie ServiceContractGenerator</span><span class="sxs-lookup"><span data-stu-id="1ce77-109">To write an extension for the ServiceContractGenerator</span></span>  
  
1. <span data-ttu-id="1ce77-110">Zaimplementuj <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span><span class="sxs-lookup"><span data-stu-id="1ce77-110">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="1ce77-111">Aby zmodyfikować wygenerowany kontrakt usługi, użyj wystąpienia <xref:System.ServiceModel.Description.ServiceContractGenerationContext> przekazaną do metody <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>.</span><span class="sxs-lookup"><span data-stu-id="1ce77-111">To modify the generated service contract, use the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instance passed into the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> method.</span></span>  
  
    ```csharp
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
        context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. <span data-ttu-id="1ce77-112">Zaimplementuj <xref:System.ServiceModel.Description.IWsdlImportExtension> w tej samej klasie.</span><span class="sxs-lookup"><span data-stu-id="1ce77-112">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension> on the same class.</span></span> <span data-ttu-id="1ce77-113">Metoda <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> może przetwarzać określone rozszerzenie WSDL (w tym przypadku adnotacje WSDL) przez dodanie rozszerzenia generowania kodu do zaimportowanego wystąpienia <xref:System.ServiceModel.Description.ContractDescription>.</span><span class="sxs-lookup"><span data-stu-id="1ce77-113">The <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method can process a specific WSDL extension (WSDL annotations in this case) by adding a code generation extension to the imported <xref:System.ServiceModel.Description.ContractDescription> instance.</span></span>  
  
    ```csharp
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
  
3. <span data-ttu-id="1ce77-114">Dodaj importera WSDL do konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="1ce77-114">Add the WSDL importer to your client configuration.</span></span>  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. <span data-ttu-id="1ce77-115">W kodzie klienta Utwórz `MetadataExchangeClient` i Wywołaj `GetMetadata`.</span><span class="sxs-lookup"><span data-stu-id="1ce77-115">In the client code, create a `MetadataExchangeClient` and call `GetMetadata`.</span></span>  
  
    ```csharp
    var mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. <span data-ttu-id="1ce77-116">Utwórz `WsdlImporter` i Wywołaj `ImportAllContracts`.</span><span class="sxs-lookup"><span data-stu-id="1ce77-116">Create a `WsdlImporter` and call `ImportAllContracts`.</span></span>  
  
    ```csharp
    var importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. <span data-ttu-id="1ce77-117">Utwórz `ServiceContractGenerator` i Wywołaj `GenerateServiceContractType` dla każdego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="1ce77-117">Create a `ServiceContractGenerator` and call `GenerateServiceContractType` for each contract.</span></span>  
  
    ```csharp
    var generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <span data-ttu-id="1ce77-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> jest automatycznie wywoływana dla każdego zachowania kontraktu dla danego kontraktu, który implementuje <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span><span class="sxs-lookup"><span data-stu-id="1ce77-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> is called automatically for each contract behavior on a given contract that implements <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="1ce77-119">W tej metodzie można następnie zmodyfikować przekazaną <xref:System.ServiceModel.Description.ServiceContractGenerationContext>.</span><span class="sxs-lookup"><span data-stu-id="1ce77-119">This method can then modify the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passed in.</span></span> <span data-ttu-id="1ce77-120">W tym przykładzie Komentarze są dodawane.</span><span class="sxs-lookup"><span data-stu-id="1ce77-120">In this example comments are added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce77-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ce77-121">See also</span></span>

- [<span data-ttu-id="1ce77-122">Metadane</span><span class="sxs-lookup"><span data-stu-id="1ce77-122">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="1ce77-123">Instrukcje: importowanie niestandardowych informacji w formacie WSDL</span><span class="sxs-lookup"><span data-stu-id="1ce77-123">How to: Import Custom WSDL</span></span>](how-to-import-custom-wsdl.md)
