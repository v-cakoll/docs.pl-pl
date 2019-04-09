---
title: Konfigurowanie wiązań dla usług WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: 009011100af86e315aa41beb822b1448e2f21b25
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150452"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a>Konfigurowanie wiązań dla usług WCF (Windows Communication Foundation)
Podczas tworzenia aplikacji, często zachodzi potrzeba Odrocz decyzji dla administratora po wdrożeniu aplikacji. Na przykład często nie ma możliwości informacji z wyprzedzeniem o tym, jaki jest adres usługi lub identyfikator (URI), będzie. Zamiast kodować adresu, jest bardziej pożądane, aby umożliwić administratorowi to zrobić po utworzeniu usługi. Ta elastyczność odbywa się za pośrednictwem konfiguracji.  
  
> [!NOTE]
>  Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z `/config` Przełącz na szybkie tworzenie plików konfiguracyjnych.  
  
## <a name="major-sections"></a>Główne sekcje  
 Schemat konfiguracji usług Windows Communication Foundation (WCF) obejmuje następujące trzy główne sekcje (`serviceModel`, `bindings`, i `services`):  
  
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
  
### <a name="servicemodel-elements"></a>Elementy modelu ServiceModel  
 Można użyć sekcji poprowadzoną `system.ServiceModel` element, aby skonfigurować typ usługi z jedną lub więcej punktów końcowych, a także ustawienia usługi. Każdy punkt końcowy, można skonfigurować za pomocą adresu, kontrakt i powiązania. Aby uzyskać więcej informacji na temat punktów końcowych, zobacz [Przegląd tworzenia punktów końcowych](../../../docs/framework/wcf/endpoint-creation-overview.md). Jeśli nie określono żadnych punktów końcowych, środowiska uruchomieniowego dodaje domyślne punkty końcowe. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 Powiązanie określa transportów (potoki protokołu TCP protokołu HTTP usługi kolejkowania komunikatów) i protokołów (bezpieczeństwo, niezawodność, przepływy transakcji) i składa się z elementów, z których każdy określa aspektów jak punkt końcowy komunikuje się ze światem wiązania.  
  
 Na przykład określenie [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) wskazuje element, aby korzystać z protokołu HTTP jako transportu dla punktu końcowego. Służy to do przewodowy punkt końcowy w czasie wykonywania, po otwarciu usługi przy użyciu tego punktu końcowego.  
  
 Istnieją dwa rodzaje powiązań: wstępnie zdefiniowanych i niestandardowych. Wstępnie zdefiniowanych powiązań kombinację przydatne elementy, które są używane w typowych scenariuszach. Aby uzyskać listę typów wstępnie zdefiniowanych powiązań, które oferuje usługi WCF, zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md). Jeśli nie kolekcji wstępnie zdefiniowanych powiązań ma poprawną kombinacją funkcje, których potrzebuje aplikacja usługi, można utworzyć powiązań niestandardowych w celu spełnienia wymagań aplikacji. Aby uzyskać więcej informacji na temat powiązania niestandardowej zobacz [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
 Cztery następujące przykłady przedstawiają najbardziej typowe konfiguracje powiązania, używany do konfigurowania usługi WCF.  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a>Określanie punktu końcowego do użycia typ powiązania  
 Pierwszy przykład przedstawia sposób określić punkty końcowe skonfigurowane za pomocą adresu, kontrakt i powiązania.  
  
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
  
 W tym przykładzie `name` atrybut wskazuje typ usługi, których konfiguracja jest ustawiona na. Podczas tworzenia usługi w kodzie za pomocą `HelloWorld` kontrakt jest inicjowany za pomocą wszystkich punktów końcowych zdefiniowanych w przykładowej konfiguracji. Jeśli zestaw implementuje tylko jedną umowę serwisową, `name` atrybut można pominąć, ponieważ usługa korzysta jedynie dostępnych typów. Atrybut przyjmuje ciąg, który musi być w formacie `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`  
  
 `address` Atrybut określa identyfikator URI, który inne punkty końcowe używają do komunikacji z usługą. Identyfikator URI może być ścieżką bezwzględną lub względną. Jeśli nie podano adresu względnego, host powinien zapewniać adres podstawowy, który jest odpowiedni dla używany w wiązaniu schemat transportu. Jeśli adres nie jest skonfigurowany, adres bazowy zakłada się, że adres dla tego punktu końcowego.  
  
 `contract` Atrybut określa kontrakt jest ujawniany przez ten punkt końcowy. Typ implementacji usługi musi implementować typ kontraktu. Jeśli implementacji usługi implementuje typ kontraktu pojedynczego, tej właściwości można pominąć.  
  
 `binding` Atrybut wybiera powiązania wstępnie zdefiniowaną lub niestandardową w celu użycia dla tego określonego punktu końcowego. Punkt końcowy, który nie wybierze jawnie powiązanie używa domyślny wybór powiązania, który jest `BasicHttpBinding`.  
  
#### <a name="modifying-a-predefined-binding"></a>Modyfikowanie wstępnie zdefiniowanych powiązań  
 W poniższym przykładzie są modyfikowane wstępnie zdefiniowanych powiązań. Następnie można go skonfigurować z dowolnego punktu końcowego w usłudze. Powiązanie jest modyfikowany przez ustawienie <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> wartość na 1 sekundę. Należy zauważyć, że właściwość ta zwraca <xref:System.TimeSpan> obiektu.  
  
 Który zmienić powiązania znajduje się w sekcji wiązania. To zmienić powiązania można teraz używać podczas tworzenia dowolnego punktu końcowego, ustawiając `binding` atrybutu w `endpoint` elementu.  
  
> [!NOTE]
>  Nadaj nazwę określonego do powiązania, `bindingConfiguration` określone w usłudze punktu końcowego musi być zgodna z nim.  
  
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
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a>Konfigurowanie zachowania do zastosowania do usług  
 W poniższym przykładzie określone zachowanie jest skonfigurowany dla typu usługi. `ServiceMetadataBehavior` Element służy do włączania [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) zapytań do usługi i Generowanie dokumentów sieci Web Services Description Language (WSDL) z metadanych.  
  
> [!NOTE]
>  Nadaj nazwę określonego z zachowaniem `behaviorConfiguration` określone w usłudze lub punkt końcowy sekcji musi zapewnić zgodność.  
  
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
  
 Poprzedni umożliwia konfigurację klienta w celu wywołania i Pobierz metadane nazwę "HelloWorld" wpisane usługi.  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a>Określanie usługi przy użyciu dwóch punktów końcowych przy użyciu wartości inne powiązanie  
 W tym przykładzie ostatnie dwa punkty końcowe są konfigurowane dla `HelloWorld` typ usługi. Każdy punkt końcowy korzysta z różnych dostosowane `bindingConfiguration` atrybutu typu powiązania (każda modyfikuje `basicHttpBinding`).  
  
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
  
 Możesz uzyskać takie samo zachowanie za pomocą konfiguracji domyślnej, dodając `protocolMapping` sekcji i konfigurowanie powiązania, jak pokazano w poniższym przykładzie.  
  
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
- [Wiązania dostarczane przez system](../../../docs/framework/wcf/system-provided-bindings.md)
- [Przegląd tworzenia punktów końcowych](../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Konfigurowanie usług i klientów za pomocą wiązań](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
