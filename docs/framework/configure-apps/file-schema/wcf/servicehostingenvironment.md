---
title: '&lt;serviceHostingEnvironment&gt;'
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: 1d9edec2c5bbddefe575952d591416353d603d33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltservicehostingenvironmentgt"></a>&lt;serviceHostingEnvironment&gt;
Ten element definiuje typ, który usługę hostingu środowiskowego dla danego transportu. Jeśli ten element jest pusta, domyślny typ jest używany. Ten element może być użyty tylko w aplikacji lub pliki konfiguracji na poziomie maszyny.  
  
 \<system.ServiceModel>  
\<serviceHostingEnvironment >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean" 
                           minFreeMemoryPercentageToActivateService="Integer" 
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String" service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String" transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|aspNetCompatibilityEnabled|Wartość logiczna wskazująca, czy tryb zgodności ASP.NET został włączony dla bieżącej aplikacji. Wartość domyślna to `false`.<br /><br /> Jeśli ten atrybut ma wartość `true`przepływ żądań do usługi Windows Communication Foundation (WCF) za pośrednictwem potoku HTTP programu ASP.NET i komunikacji za pośrednictwem protokołów innych niż HTTP jest zabronione. Aby uzyskać więcej informacji, zobacz [usługi WCF i platformy ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).|  
|Ustawienia minFreeMemoryPercentageToActivateService|Liczba całkowita, która określa minimalną ilość wolnej pamięci, która powinna być dostępna w systemie, w celu aktywowania usługi WCF. **Uwaga:** określania tego atrybutu wraz z częściowa relacja zaufania w pliku web.config, usługi WCF spowoduje <xref:System.Security.SecurityException> po uruchomieniu usługi.|  
|multipleSiteBindingsEnabled|Wartość logiczna określająca, czy włączono wielokrotne powiązania usługi IIS dla każdej witryny.<br /><br /> Usługi IIS składa się z witryn sieci web, które są kontenerami dla katalogów wirtualnych zawierających aplikacje wirtualne. Za pomocą co najmniej jednego powiązania usługi IIS można uzyskać dostępu do aplikacji w lokacji. Powiązanie z usług IIS oferuje dwa rodzaje informacji: Protokół powiązania i informacje o wiązaniu. Protokół powiązania definiuje schemat, przez który dane są przesyłane, a informacje o wiązaniu są to informacje używane do uzyskania dostępu do witryny. Przykładem Protokół powiązania, które mogą być protokołu HTTP, a informacje o wiązaniu może zawierać adres IP portu nagłówek hosta, itp.<br /><br /> Usługi IIS obsługują określania wielokrotne powiązania usługi IIS dla każdej witryny, co prowadzi do wielu adresów bazowych dla każdego schematu. Jednak usługi Windows Communication Foundation (WCF) hostowanej przez witrynę umożliwia powiązanie z tylko jedną właściwość baseAddress dla każdego schematu.<br /><br /> Aby włączyć wiele powiązań dla każdej witryny usług IIS dla usługi Windows Communication Foundation (WCF), ustaw ten atrybut `true`. Należy zauważyć, że wiele powiązania witryny jest obsługiwana tylko dla protokołu HTTP. Adres punktów końcowych w pliku konfiguracji musi być pełny identyfikator URI.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|Kolekcja elementów konfiguracji, które określają prefiks filtrów dla adres podstawowy używany przez hosta usługi.|  
|[\<serviceActivations >](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceactivations.md)|Sekcja konfiguracyjna, który opisuje ustawienia aktywacji.|  
|[\<transportConfigurationTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|Kolekcja elementów konfiguracji, które określa rodzaj danego transportu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|ServiceModel|Element główny wszystkich elementów konfiguracji systemu Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie uruchomienia obok siebie z programem ASP.NET w hostowanej domeny aplikacji (AppDomain) usług WCF. Mimo że WCF i platforma ASP.NET mogą współistnieć w tej samej domenie aplikacji, usługi WCF żądania nie są przetwarzane przez potoku HTTP platformy ASP.NET domyślnie. W związku z tym kilku elementów aplikacji platformy ASP.NET nie są dostępne dla usługi WCF. Obejmują one  
  
-   Autoryzacji URL pliku ASP.NET  
  
-   Personifikacja w programie ASP.NET  
  
-   Plik cookie na podstawie stanu sesji  
  
-   Właściwość HttpContext.Current  
  
-   Rozszerzalność potoku za pośrednictwem HttpModule niestandardowych  
  
 Jeśli usługi WCF muszą działać w kontekście programu ASP.NET i komunikować się tylko za pośrednictwem protokołu HTTP, można użyć tryb zgodności ASP.NET dla usługi WCF. Ten tryb jest włączony podczas `aspNetCompatibilityEnabled` atrybut ma ustawioną `true` na poziomie aplikacji. Implementacji usługi muszą mieć możliwość uruchamiania w trybie zgodności z użyciem <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> klasy. Po włączeniu trybu zgodności  
  
-   Autoryzacji URL pliku ASP.NET jest wymuszana przed WCF autoryzacji. Decyzję dotyczącą autoryzacji jest oparta na poziomie transportu tożsamości żądania. Tożsamości na poziomie wiadomości są ignorowane.  
  
-   Uruchom operacji usługi WCF do wykonania w kontekście personifikacji platformy ASP.NET. Jeśli zarówno personifikacji aplikacji ASP.NET i WCF personifikacji są włączone dla określonej usługi, stosuje kontekstu personifikacji WCF.  
  
-   Właściwość HttpContext.Current można używać z kodem usługi WCF i usługi będą mogli udostępnianie punktów końcowych protokołu HTTP.  
  
-   Usługi WCF żądania są przetwarzane przez potoku ASP.NET. HttpModules, które zostały skonfigurowane do działania na przychodzące żądania może również przetwarzanie żądań WCF. Obejmują one składniki platformy ASP.NET (np. <xref:System.Web.SessionState.SessionStateModule>), oraz moduły niestandardowe innych firm.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób włączania trybu zgodności z ASP.  
  
## <a name="code"></a>Kod  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [Hosting](../../../../../docs/framework/wcf/feature-details/hosting.md)  
 [Usługi WCF i platforma ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
