---
title: 'Instrukcje: importowanie niestandardowych plików WSDL'
ms.date: 03/30/2017
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
ms.openlocfilehash: 790fee1b798db1c1c2b0b37b0f48b93dd44bc5e1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164284"
---
# <a name="how-to-import-custom-wsdl"></a>Instrukcje: importowanie niestandardowych plików WSDL
W tym temacie opisano sposób importowania niestandardowych plików WSDL. Aby obsłużyć niestandardowych plików WSDL, należy zaimplementować <xref:System.ServiceModel.Description.IWsdlImportExtension> interfejsu.  
  
### <a name="to-import-custom-wsdl"></a>Aby zaimportować niestandardowych plików WSDL  
  
1.  Implementowanie <xref:System.ServiceModel.Description.IWsdlImportExtension>. Implementowanie <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> metodą zmiany metadanych przed ich zaimportowaniem. Implementowanie <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> i <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> metody służące do modyfikowania kontrakty i zaimportowane z metadanych punktów końcowych. Dostęp do importowanych kontraktu lub punkt końcowy, użyj odpowiedniego obiektu kontekstu (<xref:System.ServiceModel.Description.WsdlContractConversionContext> lub <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):  
  
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
  
2.  Konfigurowanie aplikacji klienta do korzystania z niestandardowych importerów WSDL. Należy zwrócić uwagę na to, że jeśli używasz Svcutil.exe, należy dodać tę konfigurację do pliku konfiguracji dla Svcutil.exe (Svcutil.exe.config):  
  
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
  
3.  Utwórz nową <xref:System.ServiceModel.Description.WsdlImporter> wystąpienia (przekazując <xref:System.ServiceModel.Description.MetadataSet> wystąpienia, które zawiera dokumenty WSDL, które chcesz zaimportować) i wywoływać <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);          System.Collections.ObjectModel.Collection<ContractDescription> contracts  = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Metadane](../../../../docs/framework/wcf/feature-details/metadata.md)
- [Eksportowanie i importowanie metadanych](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
- [Niestandardowa publikacja WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)
