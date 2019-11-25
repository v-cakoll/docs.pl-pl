---
title: Konfigurowanie usług za pomocą plików konfiguracji
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 29792726567373c907898cf6ced9891577f11588
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141628"
---
# <a name="configuring-services-using-configuration-files"></a>Konfigurowanie usług za pomocą plików konfiguracji
Skonfigurowanie usługi Windows Communication Foundation (WCF) z plikiem konfiguracji zapewnia elastyczność udostępniania punktów końcowych i danych zachowania usługi w punkcie wdrożenia, a nie w czasie projektowania. W tym temacie opisano dostępne podstawowe techniki.  
  
 Usługę WCF można skonfigurować za pomocą technologii konfiguracji .NET Framework. Najczęściej elementy XML są dodawane do pliku Web. config dla witryny Internet Information Services (IIS), która hostuje usługę WCF. Elementy umożliwiają zmianę szczegółów, takich jak adresy punktów końcowych (rzeczywiste adresy używane do komunikowania się z usługą) na poszczególnych komputerach. Ponadto program WCF zawiera kilka elementów dostępnych w systemie, które umożliwiają szybkie wybieranie najbardziej podstawowych funkcji usługi. Począwszy od .NET Framework 4, platforma WCF udostępnia nowy domyślny model konfiguracji, który upraszcza wymagania dotyczące konfiguracji programu WCF. Jeśli nie podasz żadnej konfiguracji WCF dla określonej usługi, środowisko uruchomieniowe automatycznie skonfiguruje usługę przy użyciu standardowych punktów końcowych oraz domyślnego powiązania/zachowania. W tym przypadku Zapisywanie konfiguracji jest główną częścią programowania aplikacji WCF.  
  
 Aby uzyskać więcej informacji, zobacz [Konfigurowanie powiązań dla usług](configuring-bindings-for-wcf-services.md). Aby uzyskać listę najczęściej używanych elementów, zobacz [powiązania dostarczone przez system](system-provided-bindings.md). Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](./samples/simplified-configuration-for-wcf-services.md).  
  
> [!IMPORTANT]
> W przypadku wdrażania w wielu różnych wersjach usługi, należy określić częściowe nazwy zestawów, do których istnieją odwołania w plikach konfiguracji. Wynika to z faktu, że plik konfiguracji jest współużytkowany przez wszystkie wersje usługi i może być uruchomiony w różnych wersjach .NET Framework.  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a>System. Configuration: Web. config i App. config  
 Usługa WCF używa systemu konfiguracji system. Configuration .NET Framework.  
  
 Podczas konfigurowania usługi w programie Visual Studio należy określić ustawienia za pomocą pliku Web. config lub pliku App. config. Wybór nazwy pliku konfiguracji jest określany przez środowisko hostingu wybrane dla usługi. Jeśli używasz usług IIS do hostowania usługi, użyj pliku Web. config. Jeśli używasz innego środowiska hostingu, użyj pliku App. config.  
  
 W programie Visual Studio plik o nazwie App. config jest używany do tworzenia końcowego pliku konfiguracji. Końcowa nazwa aktualnie używana na potrzeby konfiguracji zależy od nazwy zestawu. Na przykład zestaw o nazwie "cohowinery. exe" ma ostateczną nazwę pliku konfiguracji "cohowinery. exe. config". Jednak wystarczy zmodyfikować plik App. config. Zmiany wprowadzone w tym pliku są automatycznie wprowadzane do ostatecznego pliku konfiguracji aplikacji w czasie kompilacji.  
  
 W przypadku korzystania z pliku App. config system konfiguracji Scala plik App. config z zawartością pliku Machine. config, gdy aplikacja zostanie uruchomiona, a konfiguracja zostanie zastosowana. Ten mechanizm umożliwia zdefiniowanie ustawień całego komputera w pliku Machine. config. Plik App. config może służyć do zastępowania ustawień pliku Machine. config; Możesz również zablokować ustawienia w pliku Machine. config, tak aby były używane. W pliku Web. config system konfiguracji scala pliki Web. config we wszystkich katalogach, które pomogą do katalogu aplikacji, do konfiguracji, która zostanie zastosowana. Aby uzyskać więcej informacji na temat konfiguracji i priorytetów ustawień, zobacz tematy w przestrzeni nazw <xref:System.Configuration>.  
  
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
  
### <a name="the-services-element"></a>Element > \<Services  
 Element `services` zawiera specyfikacje dla wszystkich usług, które są obsługiwane przez aplikację. Począwszy od uproszczonego modelu konfiguracji w .NET Framework 4, ta sekcja jest opcjonalna.  
  
 [> usługi \<](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a>Element > \<Service  
 Każda usługa ma następujące atrybuty:  
  
- `name`., Określa typ, który zapewnia implementację kontraktu usługi. Jest to w pełni kwalifikowana nazwa, która składa się z przestrzeni nazw, kropki, a następnie nazwy typu. Na przykład `"MyNameSpace.myServiceType"`.  
  
- `behaviorConfiguration`., Określa nazwę jednego z `behavior` elementów znalezionych w elemencie `behaviors`. Określone zachowanie zarządza akcjami, takimi jak czy usługa zezwala na personifikację. Jeśli wartość jest pustą nazwą lub nie `behaviorConfiguration` jest dostarczone, do usługi zostanie dodany domyślny zestaw zachowań usługi.  
  
- [> usługi \<](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a>Element > \<punkt końcowy  
 Każdy punkt końcowy wymaga adresu, powiązania i kontraktu, które są reprezentowane przez następujące atrybuty:  
  
- `address`., Określa Uniform Resource Identifier usługi (URI), który może być adresem bezwzględnym lub taki, który jest określony względem adresu podstawowego usługi. W przypadku wybrania pustego ciągu wskazuje, że punkt końcowy jest dostępny pod adresem podstawowym określonym podczas tworzenia <xref:System.ServiceModel.ServiceHost> dla usługi.  
  
- `binding`., Zwykle określa powiązanie dostarczone z systemem, takie jak <xref:System.ServiceModel.WSHttpBinding>, ale może również określać powiązanie zdefiniowane przez użytkownika. Określone powiązanie określa typ transportu, używanego zabezpieczenia i kodowanie oraz to, czy niezawodne sesje, transakcje lub przesyłanie strumieniowe są obsługiwane lub włączone.  
  
- `bindingConfiguration`., Jeśli wartości domyślne powiązania muszą być modyfikowane, można to zrobić przez skonfigurowanie odpowiedniego elementu `binding` w elemencie `bindings`. Ten atrybut powinien mieć taką samą wartość jak atrybut `name` elementu `binding`, który jest używany do zmiany wartości domyślnych. Jeśli nie podano nazwy lub w powiązaniu nie określono `bindingConfiguration`, to domyślne powiązanie typu powiązania jest używane w punkcie końcowym.  
  
- `contract`., Określa interfejs, który definiuje kontrakt. Jest to interfejs zaimplementowany w typie środowiska uruchomieniowego języka wspólnego (CLR) określony przez atrybut `name` elementu `service`.  
  
- [\<endpoint >](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a>\<powiązania > elementu  
 Element `bindings` zawiera specyfikacje dla wszystkich powiązań, które mogą być używane przez dowolny punkt końcowy zdefiniowany w dowolnej usłudze.  
  
 [> powiązań\<](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a>Element > powiązania \<  
 Elementy `binding` zawarte w elemencie `bindings` mogą być jednym z powiązań dostarczonych przez system (patrz [powiązania dostarczone z systemem](system-provided-bindings.md)) lub powiązaniem niestandardowym (patrz [powiązania niestandardowe](./extending/custom-bindings.md)). Element `binding` ma atrybut `name`, który skorelowanie powiązania z punktem końcowym określonym w atrybucie `bindingConfiguration` elementu `endpoint`. Jeśli nazwa nie zostanie określona, to powiązanie odnosi się do wartości domyślnej tego typu powiązania.  
  
Aby uzyskać więcej informacji na temat konfigurowania usług i klientów, zobacz [Konfigurowanie usług WCF](configuring-services.md).
  
 [> powiązań \<](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-behaviors-element"></a>\<zachowań > elementu  
 Jest to element kontenera dla elementów `behavior`, które definiują zachowania dla usługi.  
  
 [zachowania \<](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a>\<zachowanie > elementu  
 Każdy element `behavior` jest identyfikowany przez atrybut `name` i zapewnia zachowanie dostarczone przez system, takie jak <`throttling`> lub niestandardowe zachowanie. Jeśli nazwa nie zostanie określona, ten element zachowania odnosi się do domyślnego zachowania usługi lub punktu końcowego.  
  
 [zachowanie \<](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a>Jak używać konfiguracji powiązań i zachowań  
 Program WCF ułatwia udostępnianie konfiguracji między punktami końcowymi przy użyciu systemu odniesienia w konfiguracji. Zamiast bezpośredniego przypisywania wartości konfiguracji do punktu końcowego wartości konfiguracji powiązane z powiązaniem są pogrupowane w `bindingConfiguration` elementów w sekcji `<binding>`. Konfiguracja powiązania to nazwana grupa ustawień dla powiązania. Punkty końcowe mogą następnie odwoływać się do `bindingConfiguration` według nazwy.  
  
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
  
 `name` `bindingConfiguration` jest ustawiony w elemencie `<binding>`. `name` musi być unikatowym ciągiem w zakresie typu powiązania — w tym przypadku [< basicHttpBinding\>](../configure-apps/file-schema/wcf/basichttpbinding.md)lub pustej wartości, aby odwołać się do powiązania domyślnego. Punkt końcowy łączy się z konfiguracją, ustawiając atrybut `bindingConfiguration` na ten ciąg.  
  
 `behaviorConfiguration` jest zaimplementowana w taki sam sposób, jak pokazano w poniższym przykładzie.  
  
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
  
 Należy zauważyć, że domyślny zestaw zachowań usługi jest dodawany do usługi. Ten system umożliwia używanie punktów końcowych do udostępniania wspólnych konfiguracji bez ponownego definiowania ustawień. Jeśli wymagany jest zakres całego komputera, należy utworzyć konfigurację powiązania lub zachowania w pliku Machine. config. Ustawienia konfiguracji są dostępne we wszystkich plikach App. config. [Narzędzie edytora konfiguracji (SvcConfigEditor. exe)](configuration-editor-tool-svcconfigeditor-exe.md) ułatwia tworzenie konfiguracji.  
  
## <a name="behavior-merge"></a>Scalanie zachowań  
 Funkcja scalania zachowań ułatwia zarządzanie zachowaniami, gdy istnieje potrzeba spójnego stosowania zestawu typowych zachowań. Ta funkcja umożliwia określenie zachowań na różnych poziomach w hierarchii konfiguracji, a usługi dziedziczą zachowania z wielu poziomów hierarchii konfiguracji. Aby zilustrować, jak to działa, Załóżmy, że w usługach IIS znajduje się następujący układ katalogu wirtualnego:  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 A plik `~\Web.config` ma następującą zawartość:  
  
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
  
 Możesz również wyczyścić kolekcje zachowań przy użyciu tagu \<Clear > i usunąć poszczególne zachowania z kolekcji przy użyciu tagu \<Usuń >. Na przykład następujące dwie wyniki konfiguracji w usłudze podrzędnej mają tylko zachowanie usługi ServiceMetadata:  
  
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
  
 Jeśli kolekcja zachowań podrzędnych zawiera zachowanie, które jest już obecne w kolekcji zachowań nadrzędnych, zachowanie podrzędne zastępuje element nadrzędny. Dlatego jeśli nadrzędna kolekcja zachowań miała `<serviceMetadata httpGetEnabled="False" />`, a kolekcja zachowań podrzędnych miała `<serviceMetadata httpGetEnabled="True" />`, zachowanie potomne przesłoni zachowanie nadrzędne w kolekcji zachowań, a httpGetEnabled będzie "true".  
  
## <a name="see-also"></a>Zobacz także

- [Uproszczona konfiguracja](simplified-configuration.md)
- [Konfigurowanie usług WCF](configuring-services.md)
- [> usługi \<](../configure-apps/file-schema/wcf/service.md)
- [> powiązań \<](../configure-apps/file-schema/wcf/bindings.md)
