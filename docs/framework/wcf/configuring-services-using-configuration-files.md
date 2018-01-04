---
title: "Konfigurowanie usług za pomocą plików konfiguracji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 11229a5677341db05223116c932f13b1f567e712
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-services-using-configuration-files"></a>Konfigurowanie usług za pomocą plików konfiguracji
Konfigurowanie [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usługi przy użyciu pliku konfiguracji zapewnia elastyczność udostępniania punktu końcowego i Usługa danych zachowanie w punkcie wdrożenia, a nie w czasie projektowania. W tym temacie przedstawiono podstawowe metody dostępne.  
  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługa jest można skonfigurować przy użyciu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] technologia konfiguracji. Najczęściej, elementy XML są dodawane do pliku Web.config dla witryny Internet Information Services (IIS), który jest hostem [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi. Elementy umożliwiają zmianę szczegółowe informacje, takie jak adresy punktów końcowych (rzeczywiste adresy używane do komunikacji z usługą) na komputerze przez komputer. Ponadto [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zawiera kilka elementów dostarczane przez system, które umożliwiają szybkie wybranie najbardziej podstawowych funkcji usługi. Począwszy od [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] jest dostarczany z nowy model konfiguracji domyślne, które upraszcza [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] wymagania dotyczące konfiguracji. Jeśli nie podano żadnego [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] konfiguracji dla określonej usługi, środowisko uruchomieniowe automatycznie konfiguruje usługi z niektórymi standardowych punktów końcowych i zachowanie wiązania domyślnego. W praktyce, zapisywanie konfiguracji to główne programowania [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacji.  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Konfigurowanie powiązań dla usług](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md). [!INCLUDE[crlist](../../../includes/crlist-md.md)]najczęściej używane elementów, zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)]domyślne punkty końcowe, powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
> [!IMPORTANT]
>  Podczas wdrażania scenariuszy dla siebie wdrożonym dwie różne wersje usługi, jest niezbędne do określenia częściowych nazw zestawów, do których odwołuje się w plikach konfiguracji. Jest tak, ponieważ plik konfiguracji jest współużytkowana przez wszystkie wersje usługi i mogą być wykonywane w różnych wersji programu .NET Framework.  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a>System.Configuration: Plik Web.config i App.config  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]używa systemu konfiguracji System.Configuration [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 Podczas konfigurowania usługi [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], użyj pliku Web.config lub pliku App.config, aby określić ustawienia. Wybór nazwy pliku konfiguracji jest określana przez środowisko macierzyste, wybranych dla usługi. Jeśli używane są usługi IIS do obsługi usługi, należy użyć pliku Web.config. Jeśli używane są inne środowiska macierzystego, należy użyć pliku App.config.  
  
 W [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], plik o nazwie App.config służy do tworzenia pliku konfiguracji końcowej. Nazwa końcowej faktycznie używana dla konfiguracji zależy od nazwy zestawu. Na przykład zestaw o nazwie "Cohowinery.exe" ma nazwę konfiguracji końcowej "Cohowinery.exe.config". Jednak tylko musisz zmodyfikować plik App.config. Zmiany wprowadzone w tym pliku zostaną zastosowane do pliku konfiguracji aplikacji końcowego automatycznie w czasie kompilacji.  
  
 Korzystając z pliku App.config, pliku system konfiguracji scala pliku App.config z zawartością pliku Machine.config podczas uruchamiania aplikacji i konfiguracja zostanie zastosowana. Mechanizm ten umożliwia ustawień komputera, które zostały określone w pliku Machine.config. Plik App.config może służyć do zastąpienia ustawień pliku Machine.config. można również zablokować w ustawieniach w pliku Machine.config, aby mogły uzyskać używane. W przypadku pliku Web.config system konfiguracji scala plików Web.config we wszystkich katalogach prowadzących do katalogu aplikacji do konfiguracji, który zostanie zastosowany. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Konfiguracja i ustawienia priorytetów, zobacz Tematy w <xref:System.Configuration> przestrzeni nazw.  
  
## <a name="major-sections-of-the-configuration-file"></a>Główna sekcji w pliku konfiguracji  
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
>  Powiązania i zachowania sekcje są opcjonalne i są tylko jeśli jest to wymagane.  
  
### <a name="the-services-element"></a>\<Usługi > — Element  
 `services` Element zawiera wymagania dotyczące wszystkich usług hostów aplikacji. Począwszy od modelu uproszczona konfiguracja w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], ta sekcja jest opcjonalna.  
  
 [\<usługi >](../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a>\<Usługi > — Element  
 Każda usługa ma następujące atrybuty:  
  
-   `name`., Określa typ, który zawiera implementację kontraktu usługi. Jest to pełna nazwa, która składa się z przestrzeni nazw, okres, a następnie nazwę typu. Na przykład `"MyNameSpace.myServiceType"`.  
  
-   `behaviorConfiguration`., Określa nazwę jednego z `behavior` elementy znalezione w `behaviors` elementu. Zachowanie określonego reguluje akcje, takie jak określa, czy usługa umożliwia personifikacji. Jeśli wartość jest pusta nazwa lub nie `behaviorConfiguration` podano domyślny zestaw zachowań usługi jest dodawana do usługi.  
  
-   [\<usługi >](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a>\<Punktu końcowego > — Element  
 Każdy punkt końcowy wymaga adresu, powiązania i kontraktu, które są reprezentowane przez następujące atrybuty:  
  
-   `address`., Określa usługi identyfikator URI (Uniform Resource), może to adres bezwzględny lub taki, który znajduje się względem adres podstawowy usługi. Jeśli wartość pustego ciągu, informuje, że punkt końcowy jest dostępny na adres podstawowy, który został określony podczas tworzenia <xref:System.ServiceModel.ServiceHost> dla usługi.  
  
-   `binding`., Zazwyczaj określa powiązania dostarczane przez system, takich jak <xref:System.ServiceModel.WSHttpBinding>, ale można również określić powiązania zdefiniowane przez użytkownika. Określone powiązanie Określa typ transportu, zabezpieczeń i kodowanie używane i niezawodne sesje, transakcje lub przesyłania strumieniowego obsługiwane czy jest włączone.  
  
-   `bindingConfiguration`., Jeśli wartości domyślne powiązania muszą zostać zmodyfikowane, można to zrobić przez skonfigurowanie odpowiednie `binding` element `bindings` elementu. Ten atrybut powinien mieć taką samą wartość jak `name` atrybutu `binding` element, który służy do zmiany ustawień domyślnych. Jeśli nazwa nie jest określony, lub nie `bindingConfiguration` określono powiązanie, powiązanie domyślny typ powiązania zostanie użyta w punkcie końcowym.  
  
-   `contract`., Określa interfejs, który definiuje kontrakt. To jest zaimplementowana w wspólny typ środowiska uruchomieniowego (języka wspólnego CLR) język określony przez interfejs `name` atrybutu `service` elementu.  
  
-   [\<punkt końcowy > odwołanie do elementu](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017)  
  
### <a name="the-bindings-element"></a>\<Powiązania > — Element  
 `bindings` Element zawiera specyfikacje dla wszystkich powiązań, które mogą być używane przez dowolnego punktu końcowego zdefiniowana w dowolnej usługi.  
  
 [\<powiązania >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a>\<Powiązania > — Element  
 `binding` Elementów zawartych w `bindings` element może być jedną z powiązania dostarczane przez system (zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md)) lub niestandardowego powiązania (zobacz [niestandardowego powiązania](../../../docs/framework/wcf/extending/custom-bindings.md)). `binding` Element ma `name` atrybutu odpowiadająca powiązania z punktem końcowym określone w `bindingConfiguration` atrybutu `endpoint` elementu. Jeśli nazwa nie zostanie określona, a następnie tego powiązania odpowiada wartość domyślna tego typu powiązania.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Konfigurowanie usług i klientów, zobacz [Konfigurowanie aplikacji systemu Windows Communication Foundation](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a).  
  
 [\<Powiązanie >](../../../docs/framework/misc/binding.md)  
  
### <a name="the-behaviors-element"></a>\<Zachowania > — Element  
 To jest elementem kontenera `behavior` elementów, które definiują zachowania dla usługi.  
  
 [\<zachowania >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a>\<Zachowanie > — Element  
 Każdy `behavior` element jest identyfikowany przez `name` atrybutu i zawiera albo dostarczane przez system zachowanie, takich jak <`throttling`>, lub zachowania niestandardowego. Jeśli nazwa nie jest określony element tego zachowania odpowiada domyślnego zachowania usługi lub punktu końcowego.  
  
 [\<zachowanie >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a>Jak używać powiązania i konfiguracje zachowanie  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]można łatwo udostępniać konfiguracje między punktami końcowymi za pomocą systemu odniesienia w konfiguracji. Zamiast bezpośrednio przypisywać wartości konfiguracji punktu końcowego, wartości konfiguracji odnoszące się do powiązania są pogrupowane w `bindingConfiguration` elementów w `<binding>` sekcji. Konfiguracja powiązania jest nazwaną grupę ustawień w powiązaniu. Następnie można odwoływać się punkty końcowe `bindingConfiguration` według nazwy.  
  
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
  
 `name` z `bindingConfiguration` jest ustawiany w `<binding>` elementu. `name` Musi być unikatowy ciąg w zakresie typ powiązania — w takim przypadku [< basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), lub wartość pusta w odwołaniu do powiązania domyślnego. Punkt końcowy łącza do konfiguracji przez ustawienie `bindingConfiguration` atrybutu na ciąg.  
  
 A `behaviorConfiguration` zaimplementowano tak samo, jak pokazano w poniższym przykładzie.  
  
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
  
 Należy pamiętać, że zestaw domyślnego zachowania usługi są dodawane do usługi. Ten system umożliwia punktów końcowych udostępnić typowe konfiguracje bez ponowne definiowanie ustawień. Jeśli zakres komputera jest wymagane, należy utworzyć powiązanie lub zachowania konfiguracji w pliku Machine.config. Ustawienia konfiguracji są dostępne we wszystkich plikach App.config. [Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) ułatwia tworzenie konfiguracji.  
  
## <a name="behavior-merge"></a>Zachowanie scalania  
 Zachowanie funkcji scalania ułatwia zarządzanie zachowania, gdy ma zestaw zachowań wspólnych zawsze korzystać. Ta funkcja pozwala na określenie zachowania na różnych poziomach hierarchii konfiguracji i ma dziedziczyć z różnych poziomów hierarchii konfiguracji zachowania usługi. Aby zilustrować jak to działa założono, że następujące układu katalogu wirtualnego w usługach IIS:  
  
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
  
 I ma element podrzędny, które Web.config znajdującym się w ~\Child\Web.config z następującą zawartość:  
  
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
  
 Usługi znajdującej się na ~\Child\Service.svc będą zachowywać się tak, jakby ma zarówno serviceDebug, jak i serviceMetadata zachowania. Usługi znajdującej się na ~\Service.svc będzie miał tylko zachowanie serviceDebug. Co się stanie, jest scalania kolekcje dwóch zachowanie o takiej samej nazwie (w tym przypadku ciągiem pustym).  
  
 Można także wyczyścić kolekcji zachowań przy użyciu \<Wyczyść > tagu i usunąć zachowania poszczególnych elementów z kolekcji przy użyciu \<Usuń > tagu. Na przykład następujące dwa wyniki konfiguracji w podrzędnym usługi o tylko zachowanie serviceMetadata:  
  
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
  
 Scalanie zachowanie jest wykonywane dla kolekcji zachowań bez, zgodnie z powyższym i nosi nazwę również kolekcji zachowań.  
  
 Zachowanie scalania działa w usługach IIS, środowisko, w którym scalania plików Web.config hierarchicznie z głównego pliku Web.config i machine.config hostingu. Jednak działa w środowisku aplikacji, w którym machine.config może łączyć się z pliku App.config.  
  
 Zachowanie scalania stosuje się do zachowania punktu końcowego i usługa zachowania w konfiguracji.  
  
 Jeśli podrzędnej kolekcji zachowanie zawiera zachowania, które jest już obecny w kolekcji zachowań nadrzędnej, zachowanie podrzędnego zastępuje element nadrzędny. Dlatego w przypadku kolekcji zachowań nadrzędny ma `<serviceMetadata httpGetEnabled="False" />` i została podrzędnej kolekcji zachowanie `<serviceMetadata httpGetEnabled="True" />`, działanie podrzędne spowoduje zastąpienie zachowania nadrzędnego w kolekcji zachowań i httpGetEnabled byłoby "true".  
  
## <a name="see-also"></a>Zobacz też  
 [Uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md)  
 [Konfigurowanie systemu Windows Communication Foundation aplikacji](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [\<usługi >](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
 [\<Powiązanie >](../../../docs/framework/misc/binding.md)
