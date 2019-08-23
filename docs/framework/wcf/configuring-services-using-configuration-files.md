---
title: Konfigurowanie usług za pomocą plików konfiguracji
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 68b427a81104d0f5102915002025103ef8d35dc4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928590"
---
# <a name="configuring-services-using-configuration-files"></a>Konfigurowanie usług za pomocą plików konfiguracji
Skonfigurowanie usługi Windows Communication Foundation (WCF) z plikiem konfiguracji zapewnia elastyczność udostępniania punktów końcowych i danych zachowania usługi w punkcie wdrożenia, a nie w czasie projektowania. W tym temacie opisano dostępne podstawowe techniki.  
  
 Usługę WCF można skonfigurować za pomocą technologii konfiguracji .NET Framework. Najczęściej elementy XML są dodawane do pliku Web. config dla witryny Internet Information Services (IIS), która hostuje usługę WCF. Elementy umożliwiają zmianę szczegółów, takich jak adresy punktów końcowych (rzeczywiste adresy używane do komunikowania się z usługą) na poszczególnych komputerach. Ponadto program WCF zawiera kilka elementów dostępnych w systemie, które umożliwiają szybkie wybieranie najbardziej podstawowych funkcji usługi. Począwszy od [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)]programu, platforma WCF udostępnia nowy domyślny model konfiguracji, który upraszcza wymagania dotyczące konfiguracji programu WCF. Jeśli nie podasz żadnej konfiguracji WCF dla określonej usługi, środowisko uruchomieniowe automatycznie skonfiguruje usługę przy użyciu standardowych punktów końcowych oraz domyślnego powiązania/zachowania. W tym przypadku Zapisywanie konfiguracji jest główną częścią programowania aplikacji WCF.  
  
 Aby uzyskać więcej informacji, zobacz [Konfigurowanie powiązań dla usług](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md). Aby uzyskać listę najczęściej używanych elementów, zobacz [powiązania dostarczone przez system](../../../docs/framework/wcf/system-provided-bindings.md). Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
> [!IMPORTANT]
> W przypadku wdrażania w wielu różnych wersjach usługi, należy określić częściowe nazwy zestawów, do których istnieją odwołania w plikach konfiguracji. Wynika to z faktu, że plik konfiguracji jest współużytkowany przez wszystkie wersje usługi i może być uruchomiony w różnych wersjach .NET Framework.  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a>System.Configuration: Web. config i App. config  
 Usługa WCF używa systemu konfiguracji system. Configuration .NET Framework.  
  
 Podczas konfigurowania usługi w programie Visual Studio należy określić ustawienia za pomocą pliku Web. config lub pliku App. config. Wybór nazwy pliku konfiguracji jest określany przez środowisko hostingu wybrane dla usługi. Jeśli używasz usług IIS do hostowania usługi, użyj pliku Web. config. Jeśli używasz innego środowiska hostingu, użyj pliku App. config.  
  
 W programie Visual Studio plik o nazwie App. config jest używany do tworzenia końcowego pliku konfiguracji. Końcowa nazwa aktualnie używana na potrzeby konfiguracji zależy od nazwy zestawu. Na przykład zestaw o nazwie "cohowinery. exe" ma ostateczną nazwę pliku konfiguracji "cohowinery. exe. config". Jednak wystarczy zmodyfikować plik App. config. Zmiany wprowadzone w tym pliku są automatycznie wprowadzane do ostatecznego pliku konfiguracji aplikacji w czasie kompilacji.  
  
 W przypadku korzystania z pliku App. config system konfiguracji Scala plik App. config z zawartością pliku Machine. config, gdy aplikacja zostanie uruchomiona, a konfiguracja zostanie zastosowana. Ten mechanizm umożliwia zdefiniowanie ustawień całego komputera w pliku Machine. config. Plik App. config może służyć do zastępowania ustawień pliku Machine. config; Możesz również zablokować ustawienia w pliku Machine. config, tak aby były używane. W pliku Web. config system konfiguracji scala pliki Web. config we wszystkich katalogach, które pomogą do katalogu aplikacji, do konfiguracji, która zostanie zastosowana. Aby uzyskać więcej informacji na temat konfiguracji i priorytetów ustawień, zobacz tematy w <xref:System.Configuration> przestrzeni nazw.  
  
## <a name="major-sections-of-the-configuration-file"></a>Główne sekcje pliku konfiguracji  
 Główne sekcje w pliku konfiguracji obejmują następujące elementy.  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!-- Define the service endpoints. This section is optional in the new  
    default configuration model in .NET Framework 4. -->  
      <service>  
         <endpoint/>  
      </service>  
   </services>  
  
   <bindings>  
   <!-- Specify one or more of the system-provided binding elements,  
    for example, <basicHttpBinding> -->   
   <!-- Alternatively, <customBinding> elements. -->  
      <binding>  
      <!-- For example, a <BasicHttpBinding> element. -->  
      </binding>  
   </bindings>  
  
   <behaviors>  
   <!-- One or more of the system-provided or custom behavior elements. -->  
      <behavior>  
      <!-- For example, a <throttling> element. -->  
      </behavior>  
   </behaviors>  
  
</system.ServiceModel>  
```  
  
> [!NOTE]
> Sekcje powiązania i zachowania są opcjonalne i są uwzględniane tylko w razie potrzeby.  
  
### <a name="the-services-element"></a>Element \<> usług  
 `services` Element zawiera specyfikacje dla wszystkich usług, które są obsługiwane przez aplikację. Począwszy od uproszczonego modelu konfiguracji w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]programie, ta sekcja jest opcjonalna.  
  
 [\<> usług](../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a>Element \<> usługi  
 Każda usługa ma następujące atrybuty:  
  
- `name`. Określa typ, który zapewnia implementację kontraktu usługi. Jest to w pełni kwalifikowana nazwa, która składa się z przestrzeni nazw, kropki, a następnie nazwy typu. Na przykład `"MyNameSpace.myServiceType"`.  
  
- `behaviorConfiguration`. Określa nazwę jednego z `behavior` elementów znalezionych `behaviors` w elemencie. Określone zachowanie zarządza akcjami, takimi jak czy usługa zezwala na personifikację. Jeśli wartość jest wartością pustą lub nie `behaviorConfiguration` jest podana, do usługi zostanie dodany domyślny zestaw zachowań usługi.  
  
- [\<> usługi](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a>Element \<> punktu końcowego  
 Każdy punkt końcowy wymaga adresu, powiązania i kontraktu, które są reprezentowane przez następujące atrybuty:  
  
- `address`. Określa Uniform Resource Identifier usługi (URI), który może być adresem bezwzględnym lub taki, który jest określony względem adresu podstawowego usługi. W przypadku wybrania pustego ciągu wskazuje, że punkt końcowy jest dostępny pod adresem podstawowym określonym podczas tworzenia <xref:System.ServiceModel.ServiceHost> dla usługi.  
  
- `binding`. Zwykle określa powiązanie dostarczone z systemem, takie <xref:System.ServiceModel.WSHttpBinding>jak, ale może również określać powiązanie zdefiniowane przez użytkownika. Określone powiązanie określa typ transportu, używanego zabezpieczenia i kodowanie oraz to, czy niezawodne sesje, transakcje lub przesyłanie strumieniowe są obsługiwane lub włączone.  
  
- `bindingConfiguration`. Jeśli wartości domyślne powiązania muszą być modyfikowane, można to zrobić przez skonfigurowanie odpowiedniego `binding` elementu `bindings` w elemencie. Ten atrybut powinien mieć taką samą wartość jak `name` atrybut `binding` elementu, który jest używany do zmiany wartości domyślnych. Jeśli nie podano nazwy lub nie `bindingConfiguration` określono w powiązaniu, to domyślne powiązanie typu powiązania jest używane w punkcie końcowym.  
  
- `contract`. Określa interfejs, który definiuje kontrakt. Jest to interfejs zaimplementowany w typie środowiska uruchomieniowego języka wspólnego (CLR) określony przez `name` atrybut `service` elementu.  
  
- [\<> punktu końcowego](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a>Element \<powiązań >  
 `bindings` Element zawiera specyfikacje dla wszystkich powiązań, które mogą być używane przez dowolny punkt końcowy zdefiniowany w dowolnej usłudze.  
  
 [\<> powiązań](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a>Element \<> powiązania  
 Elementy zawarte [](../../../docs/framework/wcf/extending/custom-bindings.md)w elemencie mogą być jednym z powiązań dostarczonych przez system (zobacz [powiązania dostarczone z systemem](../../../docs/framework/wcf/system-provided-bindings.md)) lub powiązaniem niestandardowym (zobacz powiązania niestandardowe). `bindings` `binding` Element ma atrybut, który skorelowanie powiązania z punktem końcowym określonym `endpoint` w `bindingConfiguration` atrybucie elementu. `name` `binding` Jeśli nazwa nie zostanie określona, to powiązanie odnosi się do wartości domyślnej tego typu powiązania.  
  
Aby uzyskać więcej informacji na temat konfigurowania usług i klientów, zobacz [Konfigurowanie usług WCF](configuring-services.md).
  
 [\<> powiązania](../../../docs/framework/misc/binding.md)  
  
### <a name="the-behaviors-element"></a>Elementy \<> zachowań  
 Jest to element kontenera dla `behavior` elementów, które definiują zachowania dla usługi.  
  
 [\<> zachowań](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a>\<Zachowanie > elementu  
 Każdy `behavior` element jest identyfikowany `name` przez atrybut i zapewnia zachowanie dostarczone przez system, takie jak <`throttling`> lub niestandardowe zachowanie. Jeśli nazwa nie zostanie określona, ten element zachowania odnosi się do domyślnego zachowania usługi lub punktu końcowego.  
  
 [\<> zachowania](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a>Jak używać konfiguracji powiązań i zachowań  
 Program WCF ułatwia udostępnianie konfiguracji między punktami końcowymi przy użyciu systemu odniesienia w konfiguracji. Zamiast bezpośrednio przypisywać wartości konfiguracyjne do punktu końcowego, wartości konfiguracyjne powiązane z powiązaniem `bindingConfiguration` są pogrupowane `<binding>` w elementach w sekcji. Konfiguracja powiązania to nazwana grupa ustawień dla powiązania. Punkty końcowe mogą następnie odwoływać się do `bindingConfiguration` nazwy.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!-- Default binding for basicHttpBinding -->  
    </basicHttpBinding>  
     </bindings>  
     <services>  
      <service name="MyNamespace.myServiceType">  
       <endpoint   
          address="myAddress" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration1"  
          contract="MyContract"  />  
       <endpoint   
          address="myAddress2" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration2"  
          contract="MyContract" />  
       <endpoint   
          address="myAddress3" binding="basicHttpBinding"   
          contract="MyContract" />  
       </service>  
      </services>  
    </system.serviceModel>  
</configuration>  
```  
  
 `name` Element`bindingConfiguration` jest ustawiony w`<binding>` elemencie. Musi być unikatowym ciągiem w zakresie typu powiązania — w tym przypadku [< BasicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)lub pustej wartości, aby odwołać się do powiązania domyślnego. `name` Punkt końcowy łączy się z konfiguracją przez ustawienie `bindingConfiguration` atrybutu na ten ciąg.  
  
 `behaviorConfiguration` Jest zaimplementowana w taki sam sposób, jak pokazano w poniższym przykładzie.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myBehavior">  
           <callbackDebug includeExceptionDetailInFaults="true" />  
         </behavior>  
      </endpointBehaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
  
    </behaviors>  
    <services>  
     <service name="NewServiceType">  
       <endpoint   
          address="myAddress3" behaviorConfiguration="myBehavior"  
          binding="basicHttpBinding"  
          contract="MyContract" />  
      </service>  
    </services>  
   </system.serviceModel>  
</configuration>  
```  
  
 Należy zauważyć, że domyślny zestaw zachowań usługi jest dodawany do usługi. Ten system umożliwia używanie punktów końcowych do udostępniania wspólnych konfiguracji bez ponownego definiowania ustawień. Jeśli wymagany jest zakres całego komputera, należy utworzyć konfigurację powiązania lub zachowania w pliku Machine. config. Ustawienia konfiguracji są dostępne we wszystkich plikach App. config. [Narzędzie edytora konfiguracji (SvcConfigEditor. exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) ułatwia tworzenie konfiguracji.  
  
## <a name="behavior-merge"></a>Scalanie zachowań  
 Funkcja scalania zachowań ułatwia zarządzanie zachowaniami, gdy istnieje potrzeba spójnego stosowania zestawu typowych zachowań. Ta funkcja umożliwia określenie zachowań na różnych poziomach w hierarchii konfiguracji, a usługi dziedziczą zachowania z wielu poziomów hierarchii konfiguracji. Aby zilustrować, jak to działa, Załóżmy, że w usługach IIS znajduje się następujący układ katalogu wirtualnego:  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 `~\Web.config` A plik ma następującą zawartość:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Istnieje natomiast plik Web. config znajdujący się w lokalizacji ~ \Child\Web.config z następującą zawartością:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Usługa znajdująca się w lokalizacji ~ \Child\Service.svc będzie zachowywać się tak, jakby miała zarówno zachowanie serviceDebug, jak i ServiceMetadata. Usługa zlokalizowana w lokalizacji ~ \Service.svc będzie miała tylko zachowanie serviceDebug. Dzieje się tak, aby dwie kolekcje zachowań o tej samej nazwie (w tym przypadku pusty ciąg) zostały scalone.  
  
 Możesz również wyczyścić kolekcje zachowań przy użyciu \<tagu Clear > i usunąć pojedyncze zachowania z kolekcji przy \<użyciu tagu Remove >. Na przykład następujące dwie wyniki konfiguracji w usłudze podrzędnej mają tylko zachowanie usługi ServiceMetadata:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <remove name="serviceDebug"/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <clear/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Scalanie zachowań odbywa się dla kolekcji zachowań pustego, jak pokazano powyżej i nazwanych kolekcji zachowań.  
  
 Scalanie zachowań działa w środowisku hostingu usług IIS, w którym pliki Web. config są scalane hierarchicznie z głównym plikiem Web. config i Machine. config. Działa również w środowisku aplikacji, gdzie Machine. config można scalić z plikiem app. config.  
  
 Scalanie zachowań dotyczy zarówno zachowań punktu końcowego, jak i zachowań usługi w konfiguracji.  
  
 Jeśli kolekcja zachowań podrzędnych zawiera zachowanie, które jest już obecne w kolekcji zachowań nadrzędnych, zachowanie podrzędne zastępuje element nadrzędny. Tak więc, jeśli kolekcja zachowań nadrzędnych miała `<serviceMetadata httpGetEnabled="False" />` , a kolekcja zachowań podrzędnych miała `<serviceMetadata httpGetEnabled="True" />`wartość, zachowanie potomne przesłoni zachowanie nadrzędne w kolekcji zachowań i HttpGetEnabled będzie "true".  
  
## <a name="see-also"></a>Zobacz także

- [Uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md)
- [Konfigurowanie usług WCF](configuring-services.md)
- [\<> usługi](../../../docs/framework/configure-apps/file-schema/wcf/service.md)
- [\<> powiązania](../../../docs/framework/misc/binding.md)
