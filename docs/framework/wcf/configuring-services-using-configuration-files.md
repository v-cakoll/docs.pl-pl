---
title: Konfigurowanie usług za pomocą plików konfiguracji
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: caf6e238ca286e5e712c0273e10502655fd7ff4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174800"
---
# <a name="configuring-services-using-configuration-files"></a>Konfigurowanie usług za pomocą plików konfiguracji
Konfigurowanie usługi Windows Communication Foundation (WCF) za pomocą pliku konfiguracji zapewnia elastyczność dostarczania danych o zachowaniu punktu końcowego i usługi w punkcie wdrożenia, a nie w czasie projektowania. W tym temacie opisano podstawowe techniki dostępne.  
  
 Usługa WCF można konfigurować przy użyciu technologii konfiguracji programu .NET Framework. Najczęściej elementy XML są dodawane do pliku Web.config dla witryny internetowych usług informacyjnych (IIS), która obsługuje usługę WCF. Elementy umożliwiają zmianę szczegółów, takich jak adresy punktów końcowych (rzeczywiste adresy używane do komunikowania się z usługą) na podstawie komputera po komputerze. Ponadto WCF zawiera kilka elementów dostarczonych przez system, które pozwalają szybko wybrać najbardziej podstawowe funkcje usługi. Począwszy od programu .NET Framework 4, WCF jest wyposażony w nowy domyślny model konfiguracji, który upraszcza wymagania konfiguracyjne WCF. Jeśli nie podasz żadnej konfiguracji WCF dla określonej usługi, środowisko wykonawcze automatycznie konfiguruje usługę z niektórymi standardowymi punktami końcowymi i domyślnym powiązaniem/zachowaniem. W praktyce pisanie konfiguracji jest główną częścią programowania aplikacji WCF.  
  
 Aby uzyskać więcej informacji, zobacz [Konfigurowanie powiązań dla usług](configuring-bindings-for-wcf-services.md). Aby uzyskać listę najczęściej używanych elementów, zobacz [Powiązania dostarczone przez system](system-provided-bindings.md). Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](simplified-configuration.md) i [uproszczona konfiguracja usług WCF](./samples/simplified-configuration-for-wcf-services.md).  
  
> [!IMPORTANT]
> Podczas wdrażania scenariuszy obok siebie, w których są wdrażane dwie różne wersje usługi, konieczne jest określenie częściowych nazw zestawów, do których odwołuje się pliki konfiguracyjne. Dzieje się tak, ponieważ plik konfiguracji jest współużytkowane przez wszystkie wersje usługi i mogą być uruchomione w różnych wersjach programu .NET Framework.  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a>System.Configuration: Web.config i App.config  
 WCF używa systemu konfiguracji System.Configuration programu .NET Framework.  
  
 Podczas konfigurowania usługi w programie Visual Studio należy użyć pliku Web.config lub pliku App.config, aby określić ustawienia. Wybór nazwy pliku konfiguracji zależy od środowiska hostingu wybranego dla usługi. Jeśli do obsługi usługi są używane usługi, użyj pliku Web.config. Jeśli używasz innego środowiska hostingowego, użyj pliku App.config.  
  
 W programie Visual Studio plik o nazwie App.config jest używany do tworzenia ostatecznego pliku konfiguracyjnego. Ostateczna nazwa faktycznie używana dla konfiguracji zależy od nazwy zestawu. Na przykład zestaw o nazwie "Cohowinery.exe" ma ostateczną nazwę pliku konfiguracji "Cohowinery.exe.config". Jednak wystarczy tylko zmodyfikować plik App.config. Zmiany wprowadzone w tym pliku są automatycznie wprowadzane do ostatecznego pliku konfiguracji aplikacji w czasie kompilacji.  
  
 Korzystając z app.config, plik system konfiguracji scala plik App.config z zawartością pliku Machine.config po uruchomieniu aplikacji i zastosowaniu konfiguracji. Mechanizm ten umożliwia zdefiniowanie ustawień dla całego komputera w pliku Machine.config. Plik App.config może służyć do zastępowania ustawień pliku Machine.config; można również zablokować w ustawieniach pliku Machine.config, tak aby się przyzwyczaić. W przypadku witryny Web.config system konfiguracji scala pliki Web.config we wszystkich katalogach prowadzących do katalogu aplikacji do konfiguracji, która zostanie zastosowana. Aby uzyskać więcej informacji na temat konfiguracji i <xref:System.Configuration> priorytetów ustawień, zobacz tematy w obszarze nazw.  
  
## <a name="major-sections-of-the-configuration-file"></a>Główne sekcje pliku konfiguracyjnego  
 Główne sekcje w pliku konfiguracyjnym zawierają następujące elementy.  
  
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
> Powiązania i zachowania sekcje są opcjonalne i są uwzględniane tylko w razie potrzeby.  
  
### <a name="the-services-element"></a>Usługi \<> Element  
 Element `services` zawiera specyfikacje dla wszystkich usług hostów aplikacji. Począwszy od uproszczonego modelu konfiguracji w programie .NET Framework 4, ta sekcja jest opcjonalna.  
  
 [\<usługi>](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a>Usługa \<> Element  
 Każda usługa ma następujące atrybuty:  
  
- `name`. Określa typ, który zapewnia implementację umowy serwisowej. Jest to w pełni kwalifikowana nazwa, która składa się z obszaru nazw, kropki, a następnie nazwy typu. Na przykład: `"MyNameSpace.myServiceType"`.  
  
- `behaviorConfiguration`. Określa nazwę jednego z `behavior` elementów znalezionych w elemencie. `behaviors` Określone zachowanie reguluje akcje, takie jak czy usługa zezwala na personifikacji. Jeśli jego wartość jest pusta nazwa lub nie `behaviorConfiguration` jest podana następnie domyślny zestaw zachowań usługi jest dodawany do usługi.  
  
- [\<>serwisowe](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a>Element \<> punktu końcowego  
 Każdy punkt końcowy wymaga adresu, powiązania i umowy, które są reprezentowane przez następujące atrybuty:  
  
- `address`. Określa jednolity identyfikator zasobu usługi (URI), który może być adresem bezwzględnym lub adresem podanym względem adresu podstawowego usługi. Jeśli ustawiono pusty ciąg, wskazuje, że punkt końcowy jest dostępny pod adresem <xref:System.ServiceModel.ServiceHost> podstawowym, który jest określony podczas tworzenia dla usługi.  
  
- `binding`. Zazwyczaj określa powiązanie dostarczone przez <xref:System.ServiceModel.WSHttpBinding>system, takie jak , ale można również określić powiązanie zdefiniowane przez użytkownika. Określone powiązanie określa typ transportu, zabezpieczeń i kodowania używane i czy niezawodne sesje, transakcje lub przesyłania strumieniowego jest obsługiwany lub włączone.  
  
- `bindingConfiguration`. Jeśli domyślne wartości powiązania muszą zostać zmodyfikowane, można to `binding` zrobić, `bindings` konfigurując odpowiedni element w elemencie. Ten atrybut powinien mieć taką samą wartość jak `name` atrybut `binding` elementu, który jest używany do zmiany wartości domyślnych. Jeśli nazwa nie jest `bindingConfiguration` podana lub nie jest określony w powiązaniu, a następnie domyślne powiązanie typu powiązania jest używany w punkcie końcowym.  
  
- `contract`. Określa interfejs definiujący kontrakt. Jest to interfejs zaimplementowany w typie środowiska wykonawczego `name` języka wspólnego `service` (CLR) określonym przez atrybut elementu.  
  
- [\<>punktu końcowego](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a>Wiązania \<> Element  
 Element `bindings` zawiera specyfikacje dla wszystkich powiązań, które mogą być używane przez dowolny punkt końcowy zdefiniowany w dowolnej usłudze.  
  
 [\<wiązania>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a>Element \<wiążący>  
 Elementy `binding` zawarte w `bindings` elemencie mogą być jednym z powiązań dostarczonych przez system (patrz [Powiązania dostarczone przez system)](system-provided-bindings.md)lub powiązaniem niestandardowym (patrz [Powiązania niestandardowe).](./extending/custom-bindings.md) Element `binding` ma `name` atrybut, który koreluje powiązanie z punktem końcowym określonym w `bindingConfiguration` atrybucie `endpoint` elementu. Jeśli nie nazwa jest określona, a następnie, że powiązanie odpowiada domyślnie tego typu powiązania.  
  
Aby uzyskać więcej informacji na temat konfigurowania usług i klientów, zobacz [Konfigurowanie usług WCF](configuring-services.md).
  
 [\<wiążące>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-behaviors-element"></a>Zachowania \<> Element  
 Jest to element kontenera dla `behavior` elementów, które definiują zachowania dla usługi.  
  
 [\<zachowania>](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a>Zachowanie \<> element  
 Każdy `behavior` element jest identyfikowany przez `name` atrybut i zapewnia zachowanie dostarczone przez `throttling` system, takie jak <> lub zachowanie niestandardowe. Jeśli nie podano nazwy, element tego zachowania odpowiada domyślnemu zachowaniu usługi lub punktu końcowego.  
  
 [\<>zachowania](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a>Jak używać konfiguracji wiązania i zachowania  
 WCF ułatwia udostępnianie konfiguracji między punktami końcowymi przy użyciu systemu odniesienia w konfiguracji. Zamiast bezpośrednio przypisywać wartości konfiguracji do punktu końcowego, wartości konfiguracji `bindingConfiguration` związane `<binding>` z powiązaniem są grupowane w elementy w sekcji. Konfiguracja powiązania jest nazwaną grupą ustawień dla powiązania. Punkty końcowe mogą `bindingConfiguration` następnie odwoływać się do nazwy według.  
  
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
  
 Element `name` `bindingConfiguration` jest ustawiony w `<binding>` elemencie. Musi `name` to być unikatowy ciąg w zakresie typu powiązania — w tym przypadku [<podstawowahttpbinowanie\>](../configure-apps/file-schema/wcf/basichttpbinding.md)lub pusta wartość, aby odwołać się do wiązania domyślnego. Punkt końcowy łączy się z `bindingConfiguration` konfiguracją, ustawiając atrybut do tego ciągu.  
  
 A `behaviorConfiguration` jest implementowana w ten sam sposób, jak pokazano w poniższej próbce.  
  
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
  
 Należy zauważyć, że domyślny zestaw zachowań usługi są dodawane do usługi. System ten umożliwia punktom końcowym udostępnianie typowych konfiguracji bez ponownego definiowania ustawień. Jeśli wymagany jest zakres dla całego komputera, utwórz konfigurację powiązania lub zachowania w pliku Machine.config. Ustawienia konfiguracji są dostępne we wszystkich plikach App.config. [Narzędzie Edytor konfiguracji (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) ułatwia tworzenie konfiguracji.  
  
## <a name="behavior-merge"></a>Scalanie zachowań  
 Funkcja scalania zachowań ułatwia zarządzanie zachowaniami, gdy chcesz, aby zestaw typowych zachowań był używany konsekwentnie. Ta funkcja umożliwia określenie zachowań na różnych poziomach hierarchii konfiguracji i mają usługi dziedziczą zachowania z wielu poziomów hierarchii konfiguracji. Aby zilustrować, jak to działa, założono, że masz następujący układ katalogu wirtualnego w usługach IIS:  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 A `~\Web.config` plik ma następującą zawartość:  
  
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
  
 I masz podrzędny Web.config znajduje się na ~\Dziecko\Web.config z następującą zawartością:  
  
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
  
 Usługa znajdująca się pod adresem ~\Child\Service.svc będzie zachowywać się tak, jakby miało zarówno zachowania serviceDebug, jak i serviceMetadata. Usługa znajdująca się w ~\Service.svc będzie miała tylko zachowanie serviceDebug. Co się dzieje, że dwie kolekcje zachowania o tej samej nazwie (w tym przypadku pusty ciąg) są scalane.  
  
 Można również wyczyścić zachowania kolekcji przy użyciu znacznika \<> i usunąć poszczególne \<zachowania z kolekcji przy użyciu tagu> remove. Na przykład następujące dwie wyniki konfiguracji w usłudze podrzędnej posiadające tylko zachowanie serviceMetadata:  
  
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
  
 Scalanie zachowań odbywa się dla bezimiennych kolekcji zachowań, jak pokazano powyżej i nazwane kolekcje zachowań, jak również.  
  
 Scalanie zachowania działa w środowisku hostingowym usług IIS, w którym pliki Web.config łączą się hierarchicznie z głównym plikiem Web.config i plikiem machine.config. Ale działa również w środowisku aplikacji, gdzie machine.config można scalić z plikiem App.config.  
  
 Scalanie zachowań dotyczy zarówno zachowań punktu końcowego, jak i zachowań usługi w konfiguracji.  
  
 Jeśli kolekcja zachowania podrzędnego zawiera zachowanie, które jest już obecne w kolekcji zachowania nadrzędnego, zachowanie podrzędne zastępuje nadrzędny. Więc jeśli kolekcja zachowania `<serviceMetadata httpGetEnabled="False" />` nadrzędnego miał `<serviceMetadata httpGetEnabled="True" />`i kolekcji zachowania podrzędnego miał, zachowanie podrzędne będzie zastąpić zachowanie nadrzędne w kolekcji zachowania i httpGetEnabled będzie "true".  
  
## <a name="see-also"></a>Zobacz też

- [Uproszczona konfiguracja](simplified-configuration.md)
- [Konfigurowanie usług WCF](configuring-services.md)
- [\<>serwisowe](../configure-apps/file-schema/wcf/service.md)
- [\<wiążące>](../configure-apps/file-schema/wcf/bindings.md)
