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
# <a name="how-to-import-custom-wsdl"></a>Instrukcje: importowanie niestandardowych plików WSDL
W tym temacie opisano sposób importowania niestandardowego WSDL. Aby obsłużyć niestandardowy WSDL, należy zaimplementować <xref:System.ServiceModel.Description.IWsdlImportExtension> interfejs.  
  
### <a name="to-import-custom-wsdl"></a>Aby zaimportować niestandardowy element WSDL  
  
1. Implementacja <xref:System.ServiceModel.Description.IWsdlImportExtension>. Zaimplementuj <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> metodę, aby zmodyfikować metadane przed zaimportowaniem. Zaimplementuj metody <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29>i, aby zmodyfikować kontrakty i punkty końcowe zaimportowane z metadanych. <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> Aby uzyskać dostęp do zaimportowanego kontraktu lub punktu końcowego, użyj odpowiedniego<xref:System.ServiceModel.Description.WsdlContractConversionContext> obiektu <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>kontekstu (lub):  
  
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
  
2. Skonfiguruj aplikację kliencką tak, aby korzystała z niestandardowego importera WSDL. Należy pamiętać, że jeśli używasz programu Svcutil. exe, należy dodać tę konfigurację do pliku konfiguracji programu Svcutil. exe (Svcutil. exe. config):  
  
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
  
3. Utwórz nowe <xref:System.ServiceModel.Description.WsdlImporter> wystąpienie (przekazanie <xref:System.ServiceModel.Description.MetadataSet> wystąpienia zawierającego dokumenty WSDL, które chcesz zaimportować) i Wywołaj <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);          System.Collections.ObjectModel.Collection<ContractDescription> contracts  = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Metadane](../feature-details/metadata.md)
- [Eksportowanie i importowanie metadanych](../feature-details/exporting-and-importing-metadata.md)
- [Niestandardowa publikacja WSDL](../samples/custom-wsdl-publication.md)
