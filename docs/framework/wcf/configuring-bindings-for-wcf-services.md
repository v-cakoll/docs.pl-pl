---
title: Konfigurowanie powiązań dla usług WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: b91c8ff5a78ef2b2b2db5ea26ae7a1733a97ffd0
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a>Konfigurowanie powiązań dla usług WCF (Windows Communication Foundation)
Podczas tworzenia aplikacji, ma często mają być odroczone decyzje administratora po wdrożeniu aplikacji. Na przykład często istnieje żaden sposób uzyskać z wyprzedzeniem, co adres usługi lub identyfikator URI (Uniform Resource), będzie. Zamiast kodować adres, zaleca się pozwalają administratorowi zrobić po utworzeniu usługi. Tego rodzaju elastyczności odbywa się za pośrednictwem konfiguracji.  
  
> [!NOTE]
>  Użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z `/config` Przełącz na szybkie tworzenie plików konfiguracyjnych.  
  
## <a name="major-sections"></a>Sekcje główne  
 Schemat konfiguracji systemu Windows Communication Foundation (WCF) obejmuje następujące trzy sekcje główne (`serviceModel`, `bindings`, i `services`):  
  
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
 Korzystając z sekcji ograniczone przez `system.ServiceModel` element, aby skonfigurować typ usługi z jednego lub więcej punktów końcowych, a także ustawienia usługi. Następnie można skonfigurować za pomocą adresu, kontrakt i powiązanie każdego punktu końcowego. Aby uzyskać więcej informacji dotyczących punktów końcowych, zobacz [Przegląd tworzenia punktów końcowych](../../../docs/framework/wcf/endpoint-creation-overview.md). Jeśli nie określono żadnych punktów końcowych, środowisko uruchomieniowe dodaje domyślne punkty końcowe. Aby uzyskać więcej informacji na temat domyślne punkty końcowe, powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 Powiązanie określa transportów (potoki protokołu HTTP, TCP, kolejkowania) i protokołów (zabezpieczeń, niezawodności, przepływy transakcji) i składa się z elementów, z których każdy określa aspektów jak punkt końcowy komunikuje się z świecie wiązania.  
  
 Na przykład określenie [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) wskazuje element do obsługi protokołu HTTP jako transportu dla punktu końcowego. Ten element jest używany do przesyłania się punkt końcowy w czasie wykonywania, gdy jest otwarty przy użyciu tego punktu końcowego usługi.  
  
 Istnieją dwa rodzaje powiązań: wstępnie zdefiniowanych i niestandardowych. Wstępnie zdefiniowanych powiązań kombinację przydatne elementy, które są używane w typowych scenariuszy. Dla listy typów wstępnie zdefiniowanych powiązań, które zapewnia usługi WCF, zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md). Jeśli żadna kolekcja wstępnie zdefiniowanych powiązania ma poprawne kombinacja funkcji, które wymaga aplikacji usługi, można utworzyć powiązania niestandardowe, aby spełnić wymagania aplikacji. Aby uzyskać więcej informacji dotyczących powiązań niestandardowych, zobacz [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
 Cztery następujące przykłady przedstawiają najbardziej typowe konfiguracje powiązania, używany do konfigurowania usługi WCF.  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a>Określający typ powiązania punktu końcowego  
 Pierwszym przykładzie przedstawiono sposób określić punkt końcowy skonfigurowany adres, kontrakt i powiązania.  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!—- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
```  
  
 W tym przykładzie `name` atrybut wskazuje typ usługi, których konfiguracja jest ustawiona na. Po utworzeniu usługi kodu za pomocą `HelloWorld` kontraktu, został zainicjowany z wszystkich punktów końcowych zdefiniowanych w przykładowej konfiguracji. Jeśli zestaw implementuje tylko jeden kontrakt usługi, `name` atrybut może zostać pominięty, ponieważ usługa korzysta z typu dostępne tylko. Atrybut przyjmuje ciąg, który musi być w formacie `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`  
  
 `address` Atrybut określa identyfikator URI, który innych punktów końcowych używają do komunikowania się z usługą. Identyfikator URI może być ścieżką bezwzględną ani względną. Jeśli zostanie podany adres względny, hosta powinien podać adres podstawowy, który jest odpowiedni dla używany w powiązaniu schemat transportu. Jeśli nie skonfigurowano adres podstawowy adres zakłada się, że adres dla tego punktu końcowego.  
  
 `contract` Atrybut określa kontrakt jest ujawniany przez ten punkt końcowy. Typ implementacji usługi musi implementować typ kontraktu. Jeśli implementacji usługi implementuje typu jeden kontrakt, tej właściwości można pominąć.  
  
 `binding` Atrybut wybiera powiązania wstępnie zdefiniowanych lub niestandardowych w celu użycia dla tego określonego punktu końcowego. Domyślny wybór powiązania, który jest korzysta z punktu końcowego, który nie wybierze jawnie powiązanie `BasicHttpBinding`.  
  
#### <a name="modifying-a-predefined-binding"></a>Modyfikowanie wstępnie zdefiniowanych powiązań  
 W poniższym przykładzie są modyfikowane wstępnie zdefiniowanych powiązań. Następnie można go skonfigurować dowolnego punktu końcowego w usłudze. Powiązanie jest modyfikowany przez ustawienie <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> wartość na 1 sekundę. Należy pamiętać, że właściwość zwraca <xref:System.TimeSpan> obiektu.  
  
 Który zmienić powiązania znajduje się w sekcji powiązania. To zmienić powiązania można teraz używać podczas tworzenia dowolnego punktu końcowego ustawiając `binding` atrybutu w `endpoint` elementu.  
  
> [!NOTE]
>  Jeśli można podać nazwę określonego powiązanie, `bindingConfiguration` określony w usłudze punktu końcowego musi być zgodna z nim.  
  
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
 W poniższym przykładzie określone zachowanie jest skonfigurowany dla typu usługi. `ServiceMetadataBehavior` Element służy do włączenia [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) wysłać zapytania do usługi i Generowanie dokumentów sieci Web Services Description Language (WSDL) z metadanych.  
  
> [!NOTE]
>  Jeśli nadaj nazwę określonego zachowania, `behaviorConfiguration` określony w usłudze lub punkt końcowy musi odpowiadać sekcji.  
  
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
  
 Poprzedniego umożliwia konfiguracji, kiedy klient wywołania w celu uzyskania metadanych "HelloWorld" wpisana usługi.  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a>Określanie usługi przy użyciu dwa punkty końcowe przy użyciu wartości inne powiązanie  
 W tym przykładzie ostatniego dwa punkty końcowe są skonfigurowane do `HelloWorld` typ usługi. Każdy punkt końcowy korzysta z innej dostosowane `bindingConfiguration` atrybut ten sam typ powiązania (każdego modyfikuje `basicHttpBinding`).  
  
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
  
 Możesz uzyskać takie samo zachowanie używa konfiguracji domyślnej, dodając `protocolMapping` sekcji i konfigurowania powiązań, jak pokazano w poniższym przykładzie.  
  
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
 [Uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md)  
 [Powiązania dostarczane przez system](../../../docs/framework/wcf/system-provided-bindings.md)  
 [Przegląd tworzenia punktów końcowych](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Konfigurowanie usług i klientów za pomocą powiązań](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
