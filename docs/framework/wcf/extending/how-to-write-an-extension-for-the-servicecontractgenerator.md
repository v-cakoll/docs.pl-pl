---
title: 'Instrukcje: pisanie rozszerzenia dla typu ServiceContractGenerator'
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: c9e10efccf0d51e6b78aace1296d227a78a9f91d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340623"
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a>Instrukcje: pisanie rozszerzenia dla typu ServiceContractGenerator
W tym temacie opisano sposób pisania rozszerzenie <xref:System.ServiceModel.Description.ServiceContractGenerator>. Można to zrobić poprzez implementację <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interfejsu na zachowaniu operacji lub implementacji <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interfejsu na zachowanie kontraktu. W tym temacie pokazano, jak zaimplementować <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interfejsu na zachowanie kontraktu.  
  
 <xref:System.ServiceModel.Description.ServiceContractGenerator> Generuje kontraktów usług, typy klientów i konfiguracji klienta z <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, i <xref:System.ServiceModel.Channels.Binding> wystąpień. Zazwyczaj zaimportować <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, i <xref:System.ServiceModel.Channels.Binding> wystąpień usługi metadanych i następnie korzystać z tych wystąpień do generowania kodu do wywołania tej usługi. W tym przykładzie <xref:System.ServiceModel.Description.IWsdlImportExtension> implementacji służy do przetwarzania adnotacje WSDL, a następnie dodaj rozszerzenia do generowania kodu do zaimportowanych kontraktów do generowania komentarzy w wygenerowanym kodzie.  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a>Do napisania rozszerzenia dla elementu ServiceContractGenerator  
  
1. Implementowanie <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Aby zmodyfikować umowy serwisowej wygenerowane, użyj <xref:System.ServiceModel.Description.ServiceContractGenerationContext> wystąpienia przekazane do <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> metody.  
  
    ```  
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. Implementowanie <xref:System.ServiceModel.Description.IWsdlImportExtension> na tej samej klasy. <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> Metoda może przetwarzać określonego rozszerzenia WSDL (WSDL adnotacje w tym przypadku) przez dodanie rozszerzenia generacji kodu do zaimportowanych <xref:System.ServiceModel.Description.ContractDescription> wystąpienia.  
  
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
  
3. Dodaj importerów WSDL do konfiguracji klienta.  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. W kodzie klienta, należy utworzyć `MetadataExchangeClient` i wywołać `GetMetadata`.  
  
    ```  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. Tworzenie `WsdlImporter` i wywołać `ImportAllContracts`.  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. Tworzenie `ServiceContractGenerator` i wywołać `GenerateServiceContractType` dla każdej umowy.  
  
    ```  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> jest wywoływana automatycznie dla każdego zachowanie kontraktu na danego kontraktu, który implementuje <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Następnie można zmodyfikować tej metody <xref:System.ServiceModel.Description.ServiceContractGenerationContext> przekazany. W tym przykładzie komentarze są dodawane.  
  
## <a name="see-also"></a>Zobacz także

- [Metadane](../../../../docs/framework/wcf/feature-details/metadata.md)
- [Instrukcje: Import Custom WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
