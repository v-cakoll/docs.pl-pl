---
title: Konfiguracja i obsługa metadanych
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 4dfeeba6db220e03ad981b13e2bb093bedcd43c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="configuration-and-metadata-support"></a>Konfiguracja i obsługa metadanych
W tym temacie opisano sposób włączania obsługi konfiguracji i metadanych dla powiązania i elementy powiązań.  
  
## <a name="overview-of-configuration-and-metadata"></a>Przegląd konfiguracji i metadane  
 W tym temacie omówiono czynności, które są elementy opcjonalne 1, 2 i 4 w [rozwijających się kanałów](../../../../docs/framework/wcf/extending/developing-channels.md) listy zadań.  
  
-   Włączanie obsługę element powiązania w pliku konfiguracji.  
  
-   Włączanie obsługi pliku konfiguracji dla powiązania.  
  
-   Eksportowanie WSDL i zasady potwierdzenia dla elementu powiązania.  
  
-   Identyfikowanie potwierdzeń WSDL i zasady, aby wstawić i skonfigurować powiązanie lub element powiązania.  
  
 Uzyskać informacji o sposobie tworzenia powiązań zdefiniowanych przez użytkownika i elementy wiązania, zobacz [powiązania Creating User-Defined](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) i [Tworzenie elementu BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)odpowiednio.  
  
## <a name="adding-configuration-support"></a>Dodawanie obsługi konfiguracji  
 Aby włączyć obsługę pliku konfiguracji dla kanału, musi implementować dwie sekcje konfiguracji <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, który umożliwia obsługę konfiguracji powiązania elementów i <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> i <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, umożliwiające obsługę konfiguracji powiązania.  
  
 Łatwiejszy sposób, w tym celu jest użycie [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) przykładowe narzędzie do generowania kodu konfiguracji dla powiązania i elementy wiązania.  
  
### <a name="extending-bindingelementextensionelement"></a>Rozszerzanie BindingElementExtensionElement  
 Poniższy przykładowy kod jest pobierana z [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki. `UdpTransportElement` Jest <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> który uwidacznia `UdpTransportBindingElement` do konfiguracji systemu. Z kilku podstawowych zastąpień próbki definiuje nazwę sekcji konfiguracji, typ elementu powiązania i jak można utworzyć elementu powiązania. Użytkownicy mogą następnie rejestrować się w sekcji rozszerzeń w pliku konfiguracji w następujący sposób.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
      <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 Rozszerzenia mogą być przywoływane z niestandardowego powiązania do użycia jako transportu UDP.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="adding-configuration-for-a-binding"></a>Dodawanie konfiguracji dla powiązania  
 Sekcja `SampleProfileUdpBindingCollectionElement` jest <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> który uwidacznia `SampleProfileUdpBinding` do konfiguracji systemu. Delegowane do zbiorczego wdrożenia `SampleProfileUdpBindingConfigurationElement`, która jest pochodną <xref:System.ServiceModel.Configuration.StandardBindingElement>. `SampleProfileUdpBindingConfigurationElement` Ma właściwości, które odpowiadają właściwościom na `SampleProfileUdpBinding`i funkcji do mapowania z `ConfigurationElement` powiązania. Na koniec `OnApplyConfiguration` metoda zostanie przesłonięta w `SampleProfileUdpBinding`, jak pokazano w poniższym kodzie próbki.  
  
```  
protected override void OnApplyConfiguration(string configurationName)  
{  
            if (binding == null)  
                throw new ArgumentNullException("binding");  
  
            if (binding.GetType() != typeof(SampleProfileUdpBinding))  
            {  
                throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,  
                    "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",  
                    typeof(SampleProfileUdpBinding).AssemblyQualifiedName,  
                    binding.GetType().AssemblyQualifiedName));  
            }  
            SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;  
  
            udpBinding.OrderedSession = this.OrderedSession;  
            udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;  
            udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;  
            if (this.ClientBaseAddress != null)  
                   udpBinding.ClientBaseAddress = ClientBaseAddress;  
}  
```  
  
 Aby zarejestrować ten program obsługi przy użyciu systemu konfiguracji, Dodaj poniższą sekcję do pliku konfiguracyjnego odpowiedniego.  
  
```xml  
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
         <sectionGroup name="bindings">  
                 <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
         </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 Następnie mogą być przywoływane z [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) sekcji konfiguracji.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"   
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"   
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="adding-metadata-support-for-a-binding-element"></a>Dodawanie obsługi metadanych elementu powiązania  
 Kanał można zintegrować system metadanych, musi obsługiwać importu i eksportu zasad. Dzięki temu narzędzi takich jak [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania klientów elementu powiązania.  
  
### <a name="adding-wsdl-support"></a>Dodawanie obsługi WSDL  
 Element powiązania transportu w powiązaniu jest odpowiedzialny za eksportowanie i importowanie informacji o adresach w metadanych. Korzystając z powiązaniem SOAP, element powiązania transportu należy również eksportować poprawne transportu identyfikatora URI w metadanych. Poniższy przykładowy kod jest pobierana z [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.  
  
#### <a name="wsdl-export"></a>Eksportu WSDL  
 Aby wyeksportować informacje adresowania `UdpTransportBindingElement` implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interfejsu. <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> Metoda dodaje poprawne informacje adresowania do portu WSDL.  
  
```  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 `UdpTransportBindingElement` Implementacja <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> gdy punkt końcowy korzysta z powiązaniem SOAP metody również eksportuje transportu identyfikatora URI:  
  
```  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>Importu WSDL  
 Aby rozszerzyć system importu WSDL do obsługi importowanie adresów, dodaj następującą konfigurację do pliku konfiguracji dla Svcutil.exe jak pokazano w pliku Svcutil.exe.config:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Podczas uruchamiania Svcutil.exe, istnieją dwa sposoby uzyskania Svcutil.exe można załadować rozszerzenia importu WSDL:  
  
1.  Punkt Svcutil.exe do pliku konfiguracji przy użyciu /SvcutilConfig:\<pliku >.  
  
2.  Dodaj sekcję konfiguracyjną do Svcutil.exe.config w tym samym katalogu co Svcutil.exe.  
  
 `UdpBindingElementImporter` Typ implementuje <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interfejsu. `ImportEndpoint` Metoda importuje adres z portu WSDL:  
  
```  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Dodawanie obsługi zasad  
 Element powiązania niestandardowego można wyeksportować potwierdzenia zasad w powiązaniu WSDL dla punktu końcowego usługi Express możliwości tego elementu powiązania. Poniższy przykładowy kod jest pobierana z [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.  
  
#### <a name="policy-export"></a>Eksportowanie zasad  
 `UdpTransportBindingElement` Typ implementuje ''<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> Aby dodać obsługę eksportowania zasady. W związku z tym <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> obejmuje `UdpTransportBindingElement` generacji zasady dla żadnego powiązania, która go zawiera.  
  
 W <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, dodawanie potwierdzenie dla protokołów UDP i innym potwierdzenia, jeśli kanał jest w trybie multiemisji. Wynika to tryb multiemisji ma wpływ na sposób stosu komunikacji jest tworzony i w związku z tym musi być między obie strony.  
  
```  
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.MulticastAssertion,     UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 Ponieważ elementy powiązania transportu niestandardowy jest odpowiedzialny za obsługę adresowania, <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementacji na `UdpTransportBindingElement` również musi obsługiwać eksportowanie zasad potwierdzenia WS-Addressing odpowiednie wskazująca wersji WS-Addressing używana.  
  
```  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Importowanie zasad  
 Aby rozszerzyć systemu importu zasad, dodaj następującą konfigurację do pliku konfiguracji dla Svcutil.exe jak pokazano w pliku Svcutil.exe.config:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Następnie wdrożymy <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> z naszych zarejestrowanych klasy (`UdpBindingElementImporter`). W <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, sprawdź potwierdzenia w odpowiedniej przestrzeni nazw i przetworzyć te generowania transportu i sprawdzanie, czy jest multiemisji. Ponadto należy usunąć potwierdzenia, które obsługuje importera z listy powiązania potwierdzenia. Ponownie uruchamiając Svcutil.exe, dostępne są dwie opcje do integracji:  
  
1.  Punkt Svcutil.exe naszych pliku konfiguracji za pomocą /SvcutilConfig:\<pliku >.  
  
2.  Dodaj sekcję konfiguracyjną do Svcutil.exe.config w tym samym katalogu co Svcutil.exe.  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Dodawanie niestandardowego powiązania importera Standard  
 Svcutil.exe i <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> typu, domyślnie rozpoznaje i zaimportować powiązania dostarczane przez system. W przeciwnym razie zaimportowany, ponieważ pobiera powiązania <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> wystąpienia. Aby włączyć Svcutil.exe i <xref:System.ServiceModel.Description.WsdlImporter> do zaimportowania `SampleProfileUdpBinding` `UdpBindingElementImporter` działa również jako importer niestandardowe Powiązanie standardowe.  
  
 Implementuje importera niestandardowe Powiązanie standardowe `ImportEndpoint` metoda <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interfejs do sprawdzenia <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> wystąpienia zaimportowane z metadanych, aby zobaczyć, jeśli może on zostać wygenerowane przez określone powiązanie standardowe.  
  
```  
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 Ogólnie rzecz biorąc importera niestandardowego powiązania standardowa implementacja polega na sprawdzanie właściwości elementów importowanych powiązanie, aby sprawdzić, czy zostały zmienione tylko właściwości, które można ustawić przez powiązanie standardowe i inne właściwości są ich wartości domyślne. Podstawowe strategię implementowania importera Powiązanie standardowe jest do utworzenia wystąpienia Powiązanie standardowe, propagowanie powiązania właściwości z elementów wiążących wystąpienie Powiązanie standardowe obsługującej Powiązanie standardowe i porównania elementy z Powiązanie standardowe elementami importowanych powiązania.
