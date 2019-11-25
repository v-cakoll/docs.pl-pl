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
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a>Instrukcje: Pisanie rozszerzenia dla elementu ServiceContractGenerator
W tym temacie opisano sposób pisania rozszerzenia dla <xref:System.ServiceModel.Description.ServiceContractGenerator>. Można to zrobić, implementując interfejs <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> w przypadku działania operacji lub implementując interfejs <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> na podstawie zachowania kontraktu. W tym temacie pokazano, jak zaimplementować interfejs <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> na zachowanie kontraktu.  
  
 <xref:System.ServiceModel.Description.ServiceContractGenerator> generuje kontrakty usługi, typy klientów i konfiguracje klientów z wystąpień <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>i <xref:System.ServiceModel.Channels.Binding>. Zazwyczaj można zaimportować wystąpienia <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>i <xref:System.ServiceModel.Channels.Binding> z metadanych usługi, a następnie użyć tych wystąpień do wygenerowania kodu w celu wywołania usługi. W tym przykładzie implementacja <xref:System.ServiceModel.Description.IWsdlImportExtension> jest używana do przetwarzania adnotacji WSDL, a następnie dodawania rozszerzeń generowania kodu do importowanych kontraktów w celu generowania komentarzy dotyczących wygenerowanego kodu.  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a>Aby napisać rozszerzenie ServiceContractGenerator  
  
1. Zaimplementuj <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Aby zmodyfikować wygenerowany kontrakt usługi, użyj wystąpienia <xref:System.ServiceModel.Description.ServiceContractGenerationContext> przekazaną do metody <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>.  
  
    ```csharp
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
        context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. Zaimplementuj <xref:System.ServiceModel.Description.IWsdlImportExtension> w tej samej klasie. Metoda <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> może przetwarzać określone rozszerzenie WSDL (w tym przypadku adnotacje WSDL) przez dodanie rozszerzenia generowania kodu do zaimportowanego wystąpienia <xref:System.ServiceModel.Description.ContractDescription>.  
  
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
  
3. Dodaj importera WSDL do konfiguracji klienta.  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. W kodzie klienta Utwórz `MetadataExchangeClient` i Wywołaj `GetMetadata`.  
  
    ```csharp
    var mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. Utwórz `WsdlImporter` i Wywołaj `ImportAllContracts`.  
  
    ```csharp
    var importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. Utwórz `ServiceContractGenerator` i Wywołaj `GenerateServiceContractType` dla każdego kontraktu.  
  
    ```csharp
    var generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> jest automatycznie wywoływana dla każdego zachowania kontraktu dla danego kontraktu, który implementuje <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. W tej metodzie można następnie zmodyfikować przekazaną <xref:System.ServiceModel.Description.ServiceContractGenerationContext>. W tym przykładzie Komentarze są dodawane.  
  
## <a name="see-also"></a>Zobacz także

- [Metadane](../feature-details/metadata.md)
- [Instrukcje: importowanie niestandardowych informacji w formacie WSDL](how-to-import-custom-wsdl.md)
