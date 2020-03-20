---
title: Konfigurowanie wiązań dla usług WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: e7ee1a8ce358c77e46db39af67bd9dc20114fb3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174826"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a>Konfigurowanie wiązań dla usług WCF (Windows Communication Foundation)
Podczas tworzenia aplikacji często chcesz odroczyć decyzje do administratora po wdrożeniu aplikacji. Na przykład często nie ma możliwości poznania z wyprzedzeniem, jaki będzie adres usługi lub jednolity identyfikator zasobu (URI). Zamiast twardego kodowania adresu, zaleca się, aby zezwolić administratorowi to zrobić po utworzeniu usługi. Ta elastyczność jest osiągana poprzez konfigurację.  
  
> [!NOTE]
> Użyj [narzędzia Narzędzia do metadanych ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) z przełącznikiem, `/config` aby szybko utworzyć pliki konfiguracyjne.  
  
## <a name="major-sections"></a>Sekcje główne  
 Schemat konfiguracji Windows Communication Foundation (WCF) obejmuje następujące`serviceModel` `bindings`trzy `services`główne sekcje ( , , , i):  
  
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
 Można użyć sekcji ograniczonej `system.ServiceModel` przez element, aby skonfigurować typ usługi z co najmniej jednym punktem końcowym, a także ustawienia dla usługi. Każdy punkt końcowy można następnie skonfigurować z adresem, umową i powiązaniem. Aby uzyskać więcej informacji na temat punktów końcowych, zobacz [Omówienie tworzenia punktów końcowych](endpoint-creation-overview.md). Jeśli nie określono żadnych punktów końcowych, środowisko wykonawcze dodaje domyślne punkty końcowe. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](simplified-configuration.md) i [uproszczona konfiguracja usług WCF](./samples/simplified-configuration-for-wcf-services.md).  
  
 Powiązanie określa transporty (HTTP, TCP, potoki, Usługi kolejkowania wiadomości) i protokoły (Zabezpieczenia, Niezawodność, Przepływy transakcji) i składa się z elementów wiązania, z których każdy określa aspekt komunikacji punktu końcowego ze światem.  
  
 Na przykład określenie [ \<podstawowego elementu>httpbinding](../configure-apps/file-schema/wcf/basichttpbinding.md) wskazuje, aby używać protokołu HTTP jako transportu dla punktu końcowego. Służy do przewodów punktu końcowego w czasie wykonywania, gdy usługa przy użyciu tego punktu końcowego jest otwarty.  
  
 Istnieją dwa rodzaje powiązań: wstępnie zdefiniowane i niestandardowe. Wstępnie zdefiniowane powiązania zawierają przydatne kombinacje elementów, które są używane w typowych scenariuszach. Aby uzyskać listę wstępnie zdefiniowanych typów powiązań, które zapewnia WCF, zobacz [Powiązania dostarczone przez system](system-provided-bindings.md). Jeśli żadna wstępnie zdefiniowana kolekcja powiązań ma poprawną kombinację funkcji, których potrzebuje aplikacja usługi, można utworzyć niestandardowe powiązania, aby spełnić wymagania aplikacji. Aby uzyskać więcej informacji na temat powiązań niestandardowych, zobacz [ \<customBinding>](../configure-apps/file-schema/wcf/custombinding.md).  
  
 Poniższe cztery przykłady ilustrują najbardziej typowe konfiguracje powiązania używane do konfigurowania usługi WCF.  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a>Określanie punktu końcowego do użycia typu powiązania  
 Pierwszy przykład ilustruje sposób określania punktu końcowego skonfigurowanego z adresem, umową i powiązaniem.  
  
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
  
 W tym przykładzie `name` atrybut wskazuje, jaki typ usługi jest dla konfiguracji. Podczas tworzenia usługi w kodzie `HelloWorld` z umową, jest inicjowany ze wszystkimi punktami końcowymi zdefiniowanymi w przykładowej konfiguracji. Jeśli zestaw implementuje tylko jeden `name` kontrakt serwisowy, atrybut można pominąć, ponieważ usługa używa tylko dostępny typ. Atrybut przyjmuje ciąg, który musi być w formacie`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`  
  
 Atrybut `address` określa identyfikator URI, który inne punkty końcowe używają do komunikowania się z usługą. Identyfikator URI może być ścieżką bezwzględną lub względną. Jeśli podany jest adres względny, oczekuje się, że host poda adres podstawowy, który jest odpowiedni dla schematu transportu używanego w powiązaniu. Jeśli adres nie jest skonfigurowany, przyjmuje się, że adres podstawowy jest adresem dla tego punktu końcowego.  
  
 Atrybut `contract` określa kontrakt, który ujawnia ten punkt końcowy. Typ implementacji usługi musi implementować typ kontraktu. Jeśli implementacja usługi implementuje jeden typ kontraktu, można pominąć tę właściwość.  
  
 Atrybut `binding` wybiera wstępnie zdefiniowane lub niestandardowe powiązanie do użycia dla tego określonego punktu końcowego. Punkt końcowy, który jawnie nie wybiera powiązania, używa domyślnego zaznaczenia powiązania, którym jest `BasicHttpBinding`.  
  
#### <a name="modifying-a-predefined-binding"></a>Modyfikowanie wstępnie zdefiniowanego powiązania  
 W poniższym przykładzie wstępnie zdefiniowane powiązanie jest modyfikowany. Następnie można użyć do skonfigurowania dowolnego punktu końcowego w usłudze. Powiązanie jest modyfikowany <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> przez ustawienie wartości na 1 sekundę. Należy zauważyć, że <xref:System.TimeSpan> właściwość zwraca obiekt.  
  
 To zmienione powiązanie znajduje się w sekcji powiązania. To zmienione powiązanie może być teraz używane podczas `binding` tworzenia dowolnego `endpoint` punktu końcowego przez ustawienie atrybutu w elemencie.  
  
> [!NOTE]
> Jeśli nadasz określoną nazwę do `bindingConfiguration` powiązania, określony w punkcie końcowym usługi musi być zgodny z nim.  
  
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
 W poniższym przykładzie określone zachowanie jest skonfigurowane dla typu usługi. Element `ServiceMetadataBehavior` ten jest używany do włączania [Narzędzia narzędzia Do metadanych ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) w celu wykonywania zapytań do usługi i generowania dokumentów języka WSDL (Web Services Description Language) z metadanych.  
  
> [!NOTE]
> Jeśli nadasz określoną nazwę do `behaviorConfiguration` zachowania, określone w sekcji usługi lub punktu końcowego musi być zgodna z nim.  
  
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
  
 Poprzednia konfiguracja umożliwia klientowi wywołanie i uzyskanie metadanych usługi wpisanej przez "HelloWorld".  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a>Określanie usługi z dwoma punktami końcowymi przy użyciu różnych wartości wiązania  
 W tym ostatnim przykładzie dwa punkty końcowe są skonfigurowane dla typu `HelloWorld` usługi. Każdy punkt końcowy używa innego `bindingConfiguration` atrybutu dostosowanego tego samego typu `basicHttpBinding`powiązania (każdy modyfikuje ).  
  
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
  
 Takie samo zachowanie można uzyskać przy użyciu `protocolMapping` konfiguracji domyślnej, dodając sekcję i konfigurując powiązania, jak pokazano w poniższym przykładzie.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Uproszczona konfiguracja](simplified-configuration.md)
- [Powiązania dostarczane przez system](system-provided-bindings.md)
- [Przegląd tworzenia punktów końcowych](endpoint-creation-overview.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](using-bindings-to-configure-services-and-clients.md)
