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
# <a name="how-to-import-custom-wsdl"></a>Instrukcje: importowanie niestandardowych informacji w formacie WSDL
W tym temacie opisano sposób importowania niestandardowego WSDL. Aby obsłużyć niestandardowe WSDL, należy zaimplementować <xref:System.ServiceModel.Description.IWsdlImportExtension> interfejs.  
  
### <a name="to-import-custom-wsdl"></a>Aby zaimportować niestandardowe WSDL  
  
1. Zaimplementuj <xref:System.ServiceModel.Description.IWsdlImportExtension>plik . Zaimplementuj <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> metodę modyfikowania metadanych przed zaimportowaniem. Zaimplementuj <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> metody modyfikowania <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> kontraktów i punktów końcowych zaimportowanych z metadanych. Aby uzyskać dostęp do importowanego kontraktu lub punktu<xref:System.ServiceModel.Description.WsdlContractConversionContext> <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>końcowego, użyj odpowiedniego obiektu kontekstowego ( lub ):  
  
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
  
2. Skonfiguruj aplikację kliencką do używania niestandardowego importera WSDL. Należy zauważyć, że w przypadku korzystania z programu Svcutil.exe należy dodać tę konfigurację do pliku konfiguracyjnego programu Svcutil.exe (Svcutil.exe.config):  
  
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
  
3. Utwórz <xref:System.ServiceModel.Description.WsdlImporter> nowe wystąpienie <xref:System.ServiceModel.Description.MetadataSet> (przechodząc w wystąpieniu, które zawiera dokumenty WSDL, które chcesz zaimportować) i zadzwoń: <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [Metadane](../feature-details/metadata.md)
- [Eksportowanie i importowanie metadanych](../feature-details/exporting-and-importing-metadata.md)
- [Niestandardowa publikacja WSDL](../samples/custom-wsdl-publication.md)
