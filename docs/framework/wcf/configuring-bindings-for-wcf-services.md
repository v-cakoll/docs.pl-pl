---
title: Konfigurowanie wiązań dla usług WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: bfcdcd172d96660c3351926a9c42d298ac3fa654
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928567"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a>Konfigurowanie wiązań dla usług WCF (Windows Communication Foundation)
Podczas tworzenia aplikacji często chcesz odroczyć decyzje administratora po wdrożeniu aplikacji. Na przykład często nie ma możliwości znajomości informacji o adresie usługi lub Uniform Resource Identifier (URI). Zamiast kodowania adresu, preferowane jest umożliwienie administratorowi wykonania tej czynności po utworzeniu usługi. Ta elastyczność jest realizowana przy użyciu konfiguracji.  
  
> [!NOTE]
> Użyj [Narzędzia do przesyłania metadanych ServiceModel (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z przełącznikiem, `/config` aby szybko utworzyć pliki konfiguracyjne.  
  
## <a name="major-sections"></a>Sekcje główne  
 Schemat konfiguracji programu Windows Communication Foundation (WCF) zawiera następujące trzy główne sekcje (`serviceModel`, `bindings`i `services`):  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <bindings>  
        </bindings>  
        <services>  
        </services>  
        <behaviors>  
        </behaviors>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="servicemodel-elements"></a>Elementy ServiceModel  
 Możesz użyć sekcji powiązanej przez element, `system.ServiceModel` aby skonfigurować typ usługi z co najmniej jednym punktem końcowym, a także ustawieniami usługi. Każdy punkt końcowy można następnie skonfigurować przy użyciu adresu, kontraktu i powiązania. Aby uzyskać więcej informacji na temat punktów końcowych, zobacz [Omówienie tworzenia punktów końcowych](../../../docs/framework/wcf/endpoint-creation-overview.md). Jeśli nie określono żadnych punktów końcowych, środowisko uruchomieniowe dodaje domyślne punkty końcowe. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 Powiązanie określa transporty (HTTP, TCP, potoki, kolejkowanie komunikatów) i protokoły (zabezpieczenia, niezawodność, przepływy transakcji) i składa się z elementów powiązania, z których każdy określa aspekt komunikacji punktu końcowego z światem.  
  
 Na przykład określenie [ \<elementu BasicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) wskazuje na użycie protokołu HTTP jako transportu dla punktu końcowego. Jest on używany do naprowadzenia łączności punktu końcowego w czasie wykonywania, gdy zostanie otwarta usługa korzystająca z tego punktu końcowego.  
  
 Istnieją dwa rodzaje powiązań: wstępnie zdefiniowane i niestandardowe. Wstępnie zdefiniowane powiązania zawierają przydatne kombinacje elementów, które są używane w typowych scenariuszach. Aby zapoznać się z listą wstępnie zdefiniowanych typów powiązań udostępnianych przez funkcję WCF, zobacz [powiązania dostarczone przez system](../../../docs/framework/wcf/system-provided-bindings.md). Jeśli żadna wstępnie zdefiniowana kolekcja powiązań nie ma poprawnej kombinacji funkcji wymaganych przez aplikację usługi, można skonstruować niestandardowe powiązania w celu spełnienia wymagań aplikacji. Aby uzyskać więcej informacji na temat powiązań niestandardowych, zobacz [ \<CustomBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
 Poniższe cztery przykłady ilustrują najczęstsze konfiguracje powiązań używane do konfigurowania usługi WCF.  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a>Określanie punktu końcowego w celu użycia typu powiązania  
 Pierwszy przykład ilustruje sposób określania punktu końcowego skonfigurowanego za pomocą adresu, kontraktu i powiązania.  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!-- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
```  
  
 W tym przykładzie `name` atrybut wskazuje typ usługi, dla której jest konfiguracja. Podczas tworzenia usługi w kodzie przy użyciu `HelloWorld` kontraktu zostanie on zainicjowany ze wszystkimi punktami końcowymi zdefiniowanymi w przykładowej konfiguracji. Jeśli zestaw implementuje tylko jeden kontrakt usługi, `name` atrybut może zostać pominięty, ponieważ usługa używa jedynego dostępnego typu. Atrybut przyjmuje ciąg, który musi mieć format`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`  
  
 Ten `address` atrybut określa identyfikator URI używany przez inne punkty końcowe do komunikowania się z usługą. Identyfikator URI może być ścieżką bezwzględną lub względną. Jeśli zostanie podany adres względny, host powinien podać adres podstawowy, który jest odpowiedni dla schematu transportu używanego w powiązaniu. Jeśli adres nie jest skonfigurowany, zakłada się, że adres podstawowy jest adresem dla tego punktu końcowego.  
  
 Ten `contract` atrybut określa kontrakt ujawniany przez ten punkt końcowy. Typ implementacji usługi musi implementować typ kontraktu. Jeśli implementacja usługi implementuje pojedynczy typ kontraktu, ta właściwość może zostać pominięta.  
  
 Ten `binding` atrybut wybiera wstępnie zdefiniowane lub niestandardowe powiązanie do użycia dla tego określonego punktu końcowego. Punkt końcowy, który nie wybiera jawnie powiązania, `BasicHttpBinding`używa domyślnego wyboru powiązania.  
  
#### <a name="modifying-a-predefined-binding"></a>Modyfikowanie wstępnie zdefiniowanego powiązania  
 W poniższym przykładzie modyfikowane jest wstępnie zdefiniowane powiązanie. Można go następnie użyć do skonfigurowania dowolnego punktu końcowego w usłudze. Powiązanie jest modyfikowane przez ustawienie <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> wartości na 1 sekundę. Należy zauważyć, że właściwość zwraca <xref:System.TimeSpan> obiekt.  
  
 To zmienione powiązanie można znaleźć w sekcji powiązań. To zmienione powiązanie może być teraz używane podczas tworzenia dowolnego punktu końcowego przez ustawienie `binding` atrybutu `endpoint` w elemencie.  
  
> [!NOTE]
> W przypadku nadania określonej nazwy powiązaniem `bindingConfiguration` określone w punkcie końcowym usługi muszą być zgodne z tym elementem.  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
<bindings>  
    <basicHttpBinding   
        receiveTimeout="00:00:01"  
    />  
</bindings>  
```  
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a>Konfigurowanie zachowania do zastosowania do usługi  
 W poniższym przykładzie określone zachowanie jest skonfigurowane dla typu usługi. Element jest używany do włączenia narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) w celu wysyłania zapytań do usługi i generowania dokumentów Web Services Description Language (WSDL) z metadanych. `ServiceMetadataBehavior`  
  
> [!NOTE]
> W przypadku nadania określonej nazwy zachowaniem `behaviorConfiguration` określone w sekcji Service lub Endpoint muszą być zgodne.  
  
```xml  
<behaviors>  
    <behavior>  
        <ServiceMetadata httpGetEnabled="true" />   
    </behavior>  
</behaviors>  
<services>  
    <service   
       name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">
       <endpoint   
          address="http://computer:8080/Hello"  
          contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
          binding="basicHttpBinding" />
    </service>  
</services>  
```  
  
 Poprzednia konfiguracja pozwala klientowi na wywołanie i Pobieranie metadanych usługi typu "HelloWorld".  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a>Określanie usługi z dwoma punktami końcowymi przy użyciu różnych wartości powiązania  
 W tym ostatnim przykładzie skonfigurowano dwa punkty końcowe dla `HelloWorld` typu usługi. Każdy punkt końcowy używa innego niestandardowego `bindingConfiguration` atrybutu tego samego typu powiązania (każda `basicHttpBinding`modyfikuje).  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
    <endpoint  
        address="http://computer:8080/Hello1"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="shortTimeout" />
    <endpoint  
        address="http://computer:8080/Hello2"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="Secure" />
</service>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure">  
        <Security mode="Transport" />  
     </basicHttpBinding>
</bindings>  
```  
  
 Takie samo zachowanie można uzyskać, korzystając z konfiguracji domyślnej, dodając `protocolMapping` sekcję i konfigurując powiązania, jak pokazano w poniższym przykładzie.  
  
```xml  
<protocolMapping>  
    <add scheme="http" binding="basicHttpBinding" bindingConfiguration="shortTimeout" />  
    <add scheme="https" binding="basicHttpBinding" bindingConfiguration="Secure" />  
</protocolMapping>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md)
- [Powiązania dostarczane przez system](../../../docs/framework/wcf/system-provided-bindings.md)
- [Przegląd tworzenia punktów końcowych](../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
