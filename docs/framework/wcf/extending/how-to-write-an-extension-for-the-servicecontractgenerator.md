---
title: 'Instrukcje: pisanie rozszerzenia dla typu ServiceContractGenerator'
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: af23babd9255c45b9fa89b5c167de6960f0f690e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855722"
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a>Instrukcje: pisanie rozszerzenia dla typu ServiceContractGenerator
W tym temacie opisano sposób pisania rozszerzenia dla programu <xref:System.ServiceModel.Description.ServiceContractGenerator>. Można to zrobić przez implementację <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interfejsu na zachowanie operacji lub <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> implementację interfejsu zgodnie z zachowaniem kontraktu. W tym temacie pokazano, <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> jak zaimplementować interfejs na zachowanie kontraktu.  
  
 Program generuje kontrakty usługi, typy klientów i konfiguracje klienta z <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>i <xref:System.ServiceModel.Channels.Binding> wystąpień. <xref:System.ServiceModel.Description.ServiceContractGenerator> Zazwyczaj można importować <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>i <xref:System.ServiceModel.Channels.Binding> wystąpienia z metadanych usługi, a następnie użyć tych wystąpień do wygenerowania kodu w celu wywołania usługi. W tym przykładzie <xref:System.ServiceModel.Description.IWsdlImportExtension> implementacja służy do przetwarzania adnotacji WSDL, a następnie dodawania rozszerzeń generowania kodu do importowanych kontraktów w celu generowania komentarzy dotyczących wygenerowanego kodu.  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a>Aby napisać rozszerzenie ServiceContractGenerator  
  
1. Implementacja <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Aby zmodyfikować wygenerowany kontrakt usługi, użyj <xref:System.ServiceModel.Description.ServiceContractGenerationContext> wystąpienia przekazaną <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> do metody.  
  
    ```csharp
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. Zaimplementuj <xref:System.ServiceModel.Description.IWsdlImportExtension> dla tej samej klasy. Metoda może przetwarzać określone rozszerzenie WSDL (w tym przypadku adnotacje WSDL) przez dodanie rozszerzenia generowania kodu do zaimportowanego <xref:System.ServiceModel.Description.ContractDescription> wystąpienia. <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29>  
  
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
  
4. W kodzie klienta Utwórz `MetadataExchangeClient` wywołanie `GetMetadata`i.  
  
    ```csharp  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. Utwórz wywołanie `WsdlImporter` `ImportAllContracts`i.  
  
    ```csharp  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. Utwórz wywołanie `ServiceContractGenerator` `GenerateServiceContractType` i dla każdego kontraktu.  
  
    ```csharp  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>jest automatycznie wywoływana dla każdego zachowania kontraktu dla danego kontraktu, który implementuje <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Następnie można zmodyfikować <xref:System.ServiceModel.Description.ServiceContractGenerationContext> przekazaną metodę. W tym przykładzie Komentarze są dodawane.  
  
## <a name="see-also"></a>Zobacz także

- [Metadane](../feature-details/metadata.md)
- [Instrukcje: Importuj niestandardowe WSDL](how-to-import-custom-wsdl.md)
