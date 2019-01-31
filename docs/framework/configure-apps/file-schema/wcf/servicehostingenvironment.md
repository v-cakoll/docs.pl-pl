---
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: 09a796a78cf37b464f5f7c359822d9d0c5001787
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257580"
---
# <a name="servicehostingenvironment"></a>\<serviceHostingEnvironment>
Ten element definiuje typ, który usługę hostingu środowiskowego dla danego transportu. Jeśli ten element jest pusta, używany jest domyślny typ. Ten element należy używać tylko w aplikacji lub pliki konfiguracji na poziomie maszyny.  
  
 \<system.ServiceModel>  
\<ServiceHostingEnvironment>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean"
                           minFreeMemoryPercentageToActivateService="Integer"
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|aspNetCompatibilityEnabled|Wartość logiczna wskazująca, czy tryb zgodności ASP.NET został włączony dla bieżącej aplikacji. Wartość domyślna to `false`.<br /><br /> Jeśli ten atrybut jest równa `true`żądania do usług Windows Communication Foundation (WCF) przepływać za pośrednictwem potoku HTTP platformy ASP.NET i komunikacji za pośrednictwem protokołów innych niż HTTP jest zabronione. Aby uzyskać więcej informacji, zobacz [usługi WCF i platforma ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).|  
|minFreeMemoryPercentageToActivateService|Liczba całkowita, która określa minimalną ilość wolnej pamięci, która powinna być dostępna w systemie, w celu aktywowania usługi WCF. **Uwaga:**  Określanie tego atrybutu, wraz z częściowej relacji zaufania w pliku web.config, usługi WCF spowoduje <xref:System.Security.SecurityException> uruchamiania usługi.|  
|multipleSiteBindingsEnabled|Wartość logiczna określająca, czy włączone jest wiele powiązań usług IIS dla każdej witryny.<br /><br /> Usługi IIS składa się z witryn sieci web, które są kontenerami dla katalogów wirtualnych zawierających aplikacje wirtualne. Aplikacja w lokacji jest możliwy za pośrednictwem jednego lub więcej powiązań usług IIS. Powiązania usługi IIS zawiera dwa rodzaje informacji: Protokół powiązania i informacje o powiązaniu. Protokół powiązania definiuje schemat, przez który dane są przesyłane, a informacje o powiązaniu informacji używanych do uzyskiwania dostępu do witryny. Przykładem Protokół powiązania mogą być protokołu HTTP, a informacje o powiązaniu może zawierać adres IP, portu, nagłówek hosta, itp.<br /><br /> Program IIS obsługuje Określanie wielu powiązań usług IIS dla witryny, co skutkuje wielu adresów bazowych na schemat. Jednak usługi Windows Communication Foundation (WCF) hostowanej przez witrynę umożliwia powiązanie, aby tylko jedna baseAddress każdego schematu.<br /><br /> Aby włączyć wiele powiązań dla każdej witryny usług IIS dla usługi Windows Communication Foundation (WCF), ustaw ten atrybut na `true`. Należy zauważyć, że wiele powiązania witryny jest obsługiwany tylko w przypadku protokołu HTTP. Adres punktów końcowych w pliku konfiguracyjnym musi być pełny identyfikator URI.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|Kolekcja elementów konfiguracji, które określają, filtrów prefiks dla adres podstawowy, używany przez hosta usługi.|  
|[\<serviceActivations>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceactivations.md)|Sekcja konfiguracji, który opisuje ustawienia aktywacji.|  
|[\<transportConfigurationTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|Kolekcja elementów konfiguracji, które identyfikują typ danego transportu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|serviceModel|Element główny wszystkich elementów konfiguracji usługi Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie wykonywania side-by-side za pomocą platformy ASP.NET w hostowanej domen aplikacji (AppDomain) usług WCF. Mimo że program WCF i platformy ASP.NET mogą współistnieć w tej samej domenie aplikacji, usługi WCF żądania nie są przetwarzane przez potok HTTP platformy ASP.NET domyślnie. W rezultacie kilka elementów w aplikacji platformy ASP.NET nie są dostępne do usług WCF. Należą do nich  
  
-   ASP.NET, plik lub adres URL autoryzacji  
  
-   Personifikacji aplikacji ASP.NET  
  
-   Stan sesji na podstawie plików cookie  
  
-   HttpContext.Current  
  
-   Rozszerzalność potoku za pomocą niestandardowych HttpModule  
  
 Jeśli usług WCF muszą działać w kontekście platformy ASP.NET i komunikować się tylko za pośrednictwem protokołu HTTP, można użyć tryb zgodności ASP.NET dla usługi WCF. Ten tryb jest włączona podczas `aspNetCompatibilityEnabled` ma ustawioną wartość atrybutu `true` na poziomie aplikacji. Implementacji usługi należy zadeklarować możliwość uruchamiania w trybie zgodności za pomocą <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> klasy. Po włączeniu trybu zgodności  
  
-   Autoryzacji programu ASP.NET, plik lub adres URL jest wymuszana przed autoryzacji usługi WCF. Decyzja o autoryzacji opiera się na poziomie transportu tożsamości żądania. Tożsamości na poziomie wiadomości są ignorowane.  
  
-   Rozpocznij operacji usługi WCF do wykonania w kontekście personifikacji platformy ASP.NET. Jeśli personifikacji aplikacji ASP.NET i WCF personifikacji są włączone dla określonej usługi, stosuje kontekstu personifikacji WCF.  
  
-   HttpContext.Current można używać na kod usługi WCF i usługi mają zablokowaną możliwość uwidaczniania punktów końcowych protokołu HTTP.  
  
-   Usługi WCF żądania są przetwarzane przez potoku ASP.NET. Elementy HttpModule, które zostały skonfigurowane do działania na przychodzące żądania może również przetwarzanie żądań usługi WCF. Obejmują one składniki platformy ASP.NET (np. <xref:System.Web.SessionState.SessionStateModule>), a także moduły niestandardowe innych firm.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak włączyć tryb zgodności ASP.  
  
## <a name="code"></a>Kod  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [Hosting](../../../../../docs/framework/wcf/feature-details/hosting.md)
- [Usługi WCF i platforma ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
