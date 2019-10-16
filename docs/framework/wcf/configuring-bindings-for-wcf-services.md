---
title: Konfigurowanie wiązań dla usług WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: 92f9457dd0c118c9a7c578a7088f66cdea1e5ad0
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320665"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a>Konfigurowanie wiązań dla usług WCF (Windows Communication Foundation)
Podczas tworzenia aplikacji często chcesz odroczyć decyzje administratora po wdrożeniu aplikacji. Na przykład często nie ma możliwości znajomości informacji o adresie usługi lub Uniform Resource Identifier (URI). Zamiast kodowania adresu, preferowane jest umożliwienie administratorowi wykonania tej czynności po utworzeniu usługi. Ta elastyczność jest realizowana przy użyciu konfiguracji.  
  
> [!NOTE]
> Użyj [Narzędzia do przesyłania metadanych ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) z przełącznikiem `/config`, aby szybko utworzyć pliki konfiguracyjne.  
  
## <a name="major-sections"></a>Sekcje główne  
 Schemat konfiguracji Windows Communication Foundation (WCF) zawiera następujące trzy główne sekcje (`serviceModel`, `bindings` i `services`):  
  
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
 Możesz użyć sekcji podzielonej przez element `system.ServiceModel`, aby skonfigurować typ usługi z co najmniej jednym punktem końcowym, a także ustawieniami usługi. Każdy punkt końcowy można następnie skonfigurować przy użyciu adresu, kontraktu i powiązania. Aby uzyskać więcej informacji na temat punktów końcowych, zobacz [Omówienie tworzenia punktów końcowych](endpoint-creation-overview.md). Jeśli nie określono żadnych punktów końcowych, środowisko uruchomieniowe dodaje domyślne punkty końcowe. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](./samples/simplified-configuration-for-wcf-services.md).  
  
 Powiązanie określa transporty (HTTP, TCP, potoki, kolejkowanie komunikatów) i protokoły (zabezpieczenia, niezawodność, przepływy transakcji) i składa się z elementów powiązania, z których każdy określa aspekt komunikacji punktu końcowego z światem.  
  
 Na przykład określenie elementu [\<basicHttpBinding >](../configure-apps/file-schema/wcf/basichttpbinding.md) wskazuje na użycie protokołu HTTP jako transportu dla punktu końcowego. Jest on używany do naprowadzenia łączności punktu końcowego w czasie wykonywania, gdy zostanie otwarta usługa korzystająca z tego punktu końcowego.  
  
 Istnieją dwa rodzaje powiązań: wstępnie zdefiniowane i niestandardowe. Wstępnie zdefiniowane powiązania zawierają przydatne kombinacje elementów, które są używane w typowych scenariuszach. Aby zapoznać się z listą wstępnie zdefiniowanych typów powiązań udostępnianych przez funkcję WCF, zobacz [powiązania dostarczone przez system](system-provided-bindings.md). Jeśli żadna wstępnie zdefiniowana kolekcja powiązań nie ma poprawnej kombinacji funkcji wymaganych przez aplikację usługi, można skonstruować niestandardowe powiązania w celu spełnienia wymagań aplikacji. Aby uzyskać więcej informacji na temat powiązań niestandardowych, zobacz [\<customBinding >](../configure-apps/file-schema/wcf/custombinding.md).  
  
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
  
 W tym przykładzie atrybut `name` wskazuje typ usługi, dla której jest konfiguracja. Podczas tworzenia usługi w kodzie przy użyciu kontraktu `HelloWorld` zostanie on zainicjowany ze wszystkimi punktami końcowymi zdefiniowanymi w przykładowej konfiguracji. Jeśli zestaw implementuje tylko jeden kontrakt usługi, atrybut `name` może zostać pominięty, ponieważ usługa używa jedynego dostępnego typu. Atrybut przyjmuje ciąg, który musi mieć format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`  
  
 Atrybut `address` Określa identyfikator URI używany przez inne punkty końcowe do komunikowania się z usługą. Identyfikator URI może być ścieżką bezwzględną lub względną. Jeśli zostanie podany adres względny, host powinien podać adres podstawowy, który jest odpowiedni dla schematu transportu używanego w powiązaniu. Jeśli adres nie jest skonfigurowany, zakłada się, że adres podstawowy jest adresem dla tego punktu końcowego.  
  
 Atrybut `contract` określa kontrakt ujawniany przez ten punkt końcowy. Typ implementacji usługi musi implementować typ kontraktu. Jeśli implementacja usługi implementuje pojedynczy typ kontraktu, ta właściwość może zostać pominięta.  
  
 Atrybut `binding` wybiera wstępnie zdefiniowane lub niestandardowe powiązanie do użycia dla tego określonego punktu końcowego. Punkt końcowy, który nie wybiera jawnie powiązania używa domyślnego wyboru powiązania, który jest `BasicHttpBinding`.  
  
#### <a name="modifying-a-predefined-binding"></a>Modyfikowanie wstępnie zdefiniowanego powiązania  
 W poniższym przykładzie modyfikowane jest wstępnie zdefiniowane powiązanie. Można go następnie użyć do skonfigurowania dowolnego punktu końcowego w usłudze. Powiązanie jest modyfikowane przez ustawienie wartości <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> na 1 sekundę. Należy zauważyć, że właściwość zwraca obiekt <xref:System.TimeSpan>.  
  
 To zmienione powiązanie można znaleźć w sekcji powiązań. To zmienione powiązanie może być teraz używane podczas tworzenia dowolnego punktu końcowego przez ustawienie atrybutu `binding` w elemencie `endpoint`.  
  
> [!NOTE]
> W przypadku nadania określonej nazwy powiązaniem wartość `bindingConfiguration` określona w punkcie końcowym usługi musi być zgodna z tym elementem.  
  
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
 W poniższym przykładzie określone zachowanie jest skonfigurowane dla typu usługi. Element `ServiceMetadataBehavior` służy do włączenia narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) w celu wysyłania zapytań do usługi i generowania dokumentów Web Services Description Language (WSDL) z metadanych.  
  
> [!NOTE]
> W przypadku nadania określonej nazwy zachowaniem wartość `behaviorConfiguration` określona w sekcji Service lub Endpoint musi być zgodna.  
  
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
 W tym ostatnim przykładzie dla typu usługi `HelloWorld` skonfigurowano dwa punkty końcowe. Każdy punkt końcowy używa innego niestandardowego atrybutu `bindingConfiguration` tego samego typu powiązania (każda modyfikuje `basicHttpBinding`).  
  
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
  
 Możesz uzyskać takie samo zachowanie przy użyciu konfiguracji domyślnej, dodając sekcję `protocolMapping` i konfigurując powiązania, jak pokazano w poniższym przykładzie.  
  
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

- [Uproszczona konfiguracja](simplified-configuration.md)
- [Powiązania dostarczane przez system](system-provided-bindings.md)
- [Przegląd tworzenia punktów końcowych](endpoint-creation-overview.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](using-bindings-to-configure-services-and-clients.md)
