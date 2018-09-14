---
title: Konfigurowanie usług za pomocą plików konfiguracji
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 904abff4f3cae5873fe3cc9705dee84f73e2a523
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45591872"
---
# <a name="configuring-services-using-configuration-files"></a>Konfigurowanie usług za pomocą plików konfiguracji
Konfigurowanie usługi Windows Communication Foundation (WCF) z plikiem konfiguracyjnym zapewnia elastyczność związanych z udostępnianiem punktu końcowego i danych zachowanie usługi na miejscu wdrożenia, a nie w czasie projektowania. W tym temacie opisano dostępne metody podstawowej.  
  
 Usługa WCF jest konfigurowane za pomocą [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] technologia konfiguracji. Najczęściej XML elementy są dodawane do pliku Web.config dla witryny usług Internet Information Services (IIS), który hostuje usługę WCF. Elementy umożliwiają zmianę szczegóły, takie jak adresy punktów końcowych (rzeczywista adresy, używane do komunikacji z usługą) na podstawie maszyny według komputera. Ponadto WCF zawiera kilku elementów dostarczanych przez system, które pozwalają szybko wybrać najbardziej podstawowe funkcje dla usługi. Począwszy od [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF, który jest dostarczany z nowy model konfiguracji domyślnej, który upraszcza wymagania dotyczące konfiguracji usługi WCF. Jeśli nie podano żadnej konfiguracji programu WCF dla określonej usługi, środowisko wykonawcze automatycznie konfiguruje usługi przy użyciu niektóre standardowe punkty końcowe i zachowanie wiązania domyślne. W praktyce Zapisywanie konfiguracji jest poważnym należą do programowania aplikacji WCF.  
  
 Aby uzyskać więcej informacji, zobacz [konfigurowanie powiązań dla usług](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md). Zobacz listę najczęściej używanych powszechnie elementów, [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md). Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
> [!IMPORTANT]
>  Podczas wdrażania scenariuszy obok siebie, w których są wdrażane dwa różne wersje usługi, należy określić częściowych nazw zestawów, do których odwołuje się w plikach konfiguracji. Jest to spowodowane plik konfiguracji jest współużytkowany przez wszystkie wersje usługi i mogą być wykonywane w ramach różnych wersji programu .NET Framework.  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a>System.Configuration: Plik Web.config i App.config  
 WCF używa systemu konfiguracji System.Configuration [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 Podczas konfigurowania usługi w programie Visual Studio, należy użyć pliku Web.config lub pliku App.config do określania ustawień. Wybór nazwy pliku konfiguracji jest określany przez środowisko hostingu, wybrany dla usługi. Jeśli używasz usług IIS do hostowania usługi, należy użyć pliku Web.config. Jeśli używasz innego środowiska hostingu użycie pliku App.config.  
  
 W programie Visual Studio plik o nazwie pliku App.config służy do tworzenia pliku konfiguracji końcowej. Nazwa końcowego rzeczywiście używane dla konfiguracji zależy od nazwy zestawu. Na przykład zestaw o nazwie "Cohowinery.exe" ma nazwę pliku konfiguracji końcowej "Cohowinery.exe.config". Jednak tylko należy zmodyfikować plik App.config. Zmiany wprowadzone w tym pliku zostaną zastosowane automatycznie do pliku konfiguracyjnym ostateczny aplikacji w czasie kompilacji.  
  
 Korzystając z pliku App.config, pliku system konfiguracji scala pliku App.config przy użyciu zawartości pliku Machine.config podczas uruchamiania aplikacji i konfiguracja jest stosowana. Ten mechanizm pozwala ustawień komputera, które zostały określone w pliku Machine.config. Plik App.config może służyć do zastąpienia ustawień w pliku Machine.config. Możesz również blokować w ustawieniach w pliku Machine.config, aby mogły uzyskać używane. W przypadku pliku Web.config system konfiguracji scala plików Web.config we wszystkich katalogach prowadzących do katalogu aplikacji do konfiguracji, który zostanie zastosowany. Aby uzyskać więcej informacji o konfiguracji i priorytety ustawienie, zobacz Tematy w <xref:System.Configuration> przestrzeni nazw.  
  
## <a name="major-sections-of-the-configuration-file"></a>Głównych sekcji w pliku konfiguracji  
 Głównych sekcji w pliku konfiguracji obejmują następujące elementy.  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!—- Define the service endpoints. This section is optional in the new  
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
>  Powiązania i zachowania sekcje są opcjonalne i można je tylko w razie potrzeby.  
  
### <a name="the-services-element"></a>\<Usługi > — Element  
 `services` Element zawiera specyfikacje dotyczące wszystkich usług hostów aplikacji. Począwszy od modelu uproszczona konfiguracja w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], ta sekcja jest opcjonalna.  
  
 [\<usługi >](../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a>\<Usługi > — Element  
 Każda usługa ma następujące atrybuty:  
  
-   `name`. Określa typ, który dostarcza implementację kontraktu usługi. Jest to w pełni kwalifikowanej nazwy, która składa się z przestrzeni nazw, kropkę oraz nazwę typu. Na przykład `"MyNameSpace.myServiceType"`.  
  
-   `behaviorConfiguration`. Określa nazwę jednej z `behavior` elementy znalezione w `behaviors` elementu. Określonego zachowania Określa akcje, takie jak czy umożliwia personifikacji. Gdy jego wartość jest pusta nazwa lub nie `behaviorConfiguration` znajduje się na wybranie domyślnego zestawu zachowania usług jest dodawana do usługi.  
  
-   [\<usługi >](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a>\<Punktu końcowego > Element  
 Każdy punkt końcowy wymaga adresu, powiązanie i umowy, które są reprezentowane przez następujące atrybuty:  
  
-   `address`. Określa usługę identyfikator (URI), który może być adresem bezwzględnym lub taki, który otrzymuje względem podstawowego adresu usługi. Jeśli ustawiony na pusty ciąg, informuje, że punkt końcowy jest dostępny pod podstawowym adresem, który jest określony podczas tworzenia <xref:System.ServiceModel.ServiceHost> dla usługi.  
  
-   `binding`. Zazwyczaj określa powiązania dostarczane przez system, takich jak <xref:System.ServiceModel.WSHttpBinding>, ale można również określić powiązanie zdefiniowanych przez użytkownika. Określone powiązanie Określa typ transportu, zabezpieczeń i kodowanie używane i sesje niezawodne, transakcji lub przesyłania strumieniowego obsługiwany czy jest włączone.  
  
-   `bindingConfiguration`. Jeśli wartości domyślne powiązania, muszą zostać zmodyfikowane, można to zrobić, konfigurując odpowiednie `binding` element `bindings` elementu. Ten atrybut powinien być podawany taką samą wartość jak `name` atrybutu `binding` element, który służy do zmiany ustawień domyślnych. Jeśli nazwa nie jest określony, lub nie `bindingConfiguration` określono powiązanie, a następnie powiązanie domyślny typ powiązania jest używany w punkcie końcowym.  
  
-   `contract`. Określa interfejs, który definiuje kontrakt. Jest to interfejs zaimplementowane w typ języka wspólnego środowiska uruchomieniowego (języka wspólnego CLR) określonej przez `name` atrybutu `service` elementu.  
  
-   [\<punkt końcowy > odwołanie do elementu](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)  
  
### <a name="the-bindings-element"></a>\<Powiązania > Element  
 `bindings` Element zawiera specyfikacje dotyczące wszystkich powiązań, które mogą być używane przez dowolnego punktu końcowego zdefiniowana w każdej usługi.  
  
 [\<powiązania >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a>\<Powiązania > Element  
 `binding` Elementów zawartych w słowniku `bindings` element może być dowolny powiązania dostarczane przez system (zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md)) lub niestandardowego powiązania (zobacz [powiązań niestandardowych](../../../docs/framework/wcf/extending/custom-bindings.md)). `binding` Element ma `name` atrybut, który jest odwrotnie skorelowana powiązanie z punktu końcowego określonego w `bindingConfiguration` atrybutu `endpoint` elementu. Jeśli nazwa nie zostanie określona, a następnie to powiązanie odnosi się do domyślnego typu powiązania.  
  
 Aby uzyskać więcej informacji na temat konfigurowania usług i klientów, zobacz [Konfigurowanie aplikacji systemu Windows Communication Foundation](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).  
  
 [\<Powiązanie >](../../../docs/framework/misc/binding.md)  
  
### <a name="the-behaviors-element"></a>\<Zachowania > Element  
 Jest to element kontenera dla `behavior` elementy, które definiują zachowania usługi.  
  
 [\<zachowania >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a>\<Zachowanie > Element  
 Każdy `behavior` element jest identyfikowany przez `name` atrybutu i zawiera albo dostarczane przez system zachowania, takich jak <`throttling`>, lub niestandardowe zachowania. Jeśli nazwa nie jest określony element tego zachowania odnosi się do domyślnego zachowania usługi lub punktu końcowego.  
  
 [\<zachowanie >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a>Jak używać powiązania i konfiguracji zachowanie  
 Usługi WCF można łatwo udostępniać konfiguracje między punktami końcowymi za pomocą systemu odniesienia w konfiguracji. Zamiast bezpośrednio przypisywać wartości konfiguracji w punkcie końcowym, konfiguracji odnoszące się do powiązania wartości są grupowane w `bindingConfiguration` elementów w `<binding>` sekcji. Konfiguracja powiązania jest nazwaną grupę ustawień w powiązaniu. Następnie tworzyć odwołania do punktów końcowych `bindingConfiguration` według nazwy.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!—- Default binding for basicHttpBinding -->  
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
  
 `name` z `bindingConfiguration` jest ustawiana w `<binding>` elementu. `name` Musi być unikatowy ciąg w zakresie typ powiązania — w tym przypadku [< basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), lub wartość pustą, aby odwołać się do powiązania domyślne. Łączy punkt końcowy z konfiguracją, ustawiając `bindingConfiguration` atrybutu do tego ciągu.  
  
 A `behaviorConfiguration` zaimplementowano ten sam sposób, jak pokazano w następującym przykładzie.  
  
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
  
 Należy pamiętać, że domyślny zestaw zachowania usług są dodawane do usługi. Ten system umożliwia punktów końcowych udostępnić typowych konfiguracji bez ponownego definiowania ustawień. Jeśli zakres komputera jest wymagany, należy utworzyć powiązanie lub zachowanie konfiguracji w pliku Machine.config. Ustawienia konfiguracji są dostępne we wszystkich plikach w pliku App.config. [Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) można łatwo tworzyć konfiguracje.  
  
## <a name="behavior-merge"></a>Zachowanie scalania  
 Funkcja scalania zachowanie ułatwia zarządzanie zachowania, gdy chcesz, aby zestaw wspólny zbiór wykonywanych czynności zawsze korzystać. Ta funkcja pozwala określić zachowania na różnych poziomach hierarchii konfiguracji i usług, które dziedziczą zachowań na różnych poziomach hierarchii konfiguracji. Aby zilustrować, jak ta działa przyjęto założenie, że masz następujące układu katalogu wirtualnego w usługach IIS:  
  
 ~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc  
  
 I plik ~\Web.config ma następującą zawartość:  
  
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
  
 I ma element podrzędny, który plik Web.config znajduje się w ~\Child\Web.config z następującą zawartością:  
  
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
  
 Usługa znajdujący się w ~\Child\Service.svc będzie działać tak, jakby ma zachowania serviceDebug i serviceMetadata w pliku. Usługa znajdujący się w ~\Service.svc będzie miał tylko zachowanie serviceDebug. Co się stanie, jest scalania dwóch zachowanie kolekcji o tej samej nazwie (w tym przypadku ciąg pusty).  
  
 Można także wyczyścić zachowanie kolekcji za pomocą \<Wyczyść > tag i usunąć zachowania poszczególnych elementów z kolekcji przy użyciu \<Usuń > tag. Na przykład następujące dwa wyniki konfiguracji w podrzędnym usługi mających tylko zachowanie serviceMetadata w pliku:  
  
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
  
 Zachowanie scalania jest wykonywane dla pustego zachowania kolekcji, jak pokazano powyżej i nosi nazwę kolekcji zachowań, jak również.  
  
 Zachowanie scalania działa w usługach IIS, środowisko, w których scalania plików Web.config hierarchicznie z głównego pliku Web.config i machine.config hostingu. Jednak ta funkcja działa w środowisku aplikacji, gdzie machine.config można scalać z pliku App.config.  
  
 Scalanie zachowanie dotyczy zarówno zachowań punktu końcowego, jak i zachowania usługi w konfiguracji.  
  
 Jeśli kolekcja zachowanie podrzędnych zawiera zachowania, które znajduje się już w zbiorze zachowanie nadrzędnym, zachowanie podrzędnego zastępuje element nadrzędny. Tak, jeśli próba zawierała kolekcji nadrzędnej zachowanie `<serviceMetadata httpGetEnabled="False" />` i zachowanie kolekcji podrzędnej `<serviceMetadata httpGetEnabled="True" />`zachowanie podrzędnych przesłonić zachowanie nadrzędnego w kolekcji zachowanie i httpGetEnabled będzie "true".  
  
## <a name="see-also"></a>Zobacz też  
 [Uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md)  
 [Konfigurowanie aplikacji programu Windows Communication Foundation](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [\<usługi >](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
 [\<Powiązanie >](../../../docs/framework/misc/binding.md)
