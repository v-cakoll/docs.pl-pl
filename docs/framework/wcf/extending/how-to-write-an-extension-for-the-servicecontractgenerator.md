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
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a>Instrukcje: Pisanie rozszerzenia dla elementu ServiceContractGenerator
W tym temacie opisano sposób pisanie rozszerzenia dla <xref:System.ServiceModel.Description.ServiceContractGenerator>. Można to zrobić z zastosowaniem <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interfejsu na zachowanie operacji lub implementacja <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interfejsu na zachowanie kontraktu. W tym temacie przedstawiono sposób wykonania <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interfejsu na zachowanie kontraktu.  
  
 <xref:System.ServiceModel.Description.ServiceContractGenerator> Generuje kontraktów usług, typy klientów i konfiguracji klienta z <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, i <xref:System.ServiceModel.Channels.Binding> wystąpień. Zazwyczaj należy zaimportować <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, i <xref:System.ServiceModel.Channels.Binding> wystąpień z metadanych usługi, a następnie użyć tych obiektów do generowania kodu do wywołania tej usługi. W tym przykładzie <xref:System.ServiceModel.Description.IWsdlImportExtension> implementacji służy do przetwarzania adnotacje WSDL, a następnie dodaj rozszerzenia generacji kodu do następującą liczbę zaimportowanych kontraktów do generowania komentarzy w wygenerowanym kodzie.  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a>Aby pisanie rozszerzenia dla elementu ServiceContractGenerator  
  
1.  Implementowanie <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Aby zmodyfikować kontraktu usługi wygenerowanego, użyj <xref:System.ServiceModel.Description.ServiceContractGenerationContext> przekazany wystąpienia <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> metody.  
  
    ```  
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2.  Implementowanie <xref:System.ServiceModel.Description.IWsdlImportExtension> na tej samej klasy. <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> Metody może przetwarzać określonego rozszerzenia WSDL (WSDL adnotacje w tym przypadku), dodając rozszerzenie generowania kodu do importowanego <xref:System.ServiceModel.Description.ContractDescription> wystąpienia.  
  
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
  
3.  Do konfiguracji klienta, należy dodać importerów WSDL.  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4.  W kodzie klienta, tworzenie `MetadataExchangeClient` i Wywołaj `GetMetadata`.  
  
    ```  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5.  Utwórz `WsdlImporter` i Wywołaj `ImportAllContracts`.  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6.  Utwórz `ServiceContractGenerator` i Wywołaj `GenerateServiceContractType` dla każdej umowy.  
  
    ```  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7.  <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>jest wywoływana automatycznie dla każdej umowy zachowanie na danego kontraktu, który implementuje <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Tej metody można następnie zmodyfikować <xref:System.ServiceModel.Description.ServiceContractGenerationContext> przekazany. Komentarze są dodawane w tym przykładzie.  
  
## <a name="see-also"></a>Zobacz też  
 [Metadane](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [Instrukcje: importowanie niestandardowych informacji w formacie WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
