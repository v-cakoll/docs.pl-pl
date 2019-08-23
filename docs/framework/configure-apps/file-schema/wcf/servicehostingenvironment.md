---
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: b81c9f3c4260f415f057cd74b6f113d88f635978
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936292"
---
# <a name="servicehostingenvironment"></a>\<serviceHostingEnvironment>
Ten element definiuje typ tworzenia wystąpień środowiska hostingu usługi dla określonego transportu. Jeśli ten element jest pusty, używany jest typ domyślny. Tego elementu można używać tylko w plikach konfiguracji na poziomie aplikacji lub komputera.  
  
 \<system.ServiceModel>  
\<ServiceHostingEnvironment >  
  
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
|aspNetCompatibilityEnabled|Wartość logiczna wskazująca, czy tryb zgodności ASP.NET został włączony dla bieżącej aplikacji. Wartość domyślna to `false`.<br /><br /> Gdy ten atrybut jest ustawiony na `true`, żądania do Windows Communication Foundation (WCF) usługi przepływu za pośrednictwem potoku HTTP ASP.NET, a komunikacja za pośrednictwem protokołów innych niż HTTP jest zabronione. Aby uzyskać więcej informacji, zobacz [usługi WCF i ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).|  
|minFreeMemoryPercentageToActivateService|Liczba całkowita określająca minimalną ilość wolnej pamięci, która powinna być dostępna dla systemu, zanim będzie można aktywować usługę WCF. **Ostrzeżenie**  Określenie tego atrybutu wraz z częściowym zaufaniem w pliku Web. config usługi WCF spowoduje, że <xref:System.Security.SecurityException> usługa zostanie uruchomiona.|  
|multipleSiteBindingsEnabled|Wartość logiczna określająca, czy włączono wiele powiązań usług IIS dla każdej witryny.<br /><br /> Usługi IIS składają się z witryn sieci Web, które są kontenerami dla aplikacji wirtualnych zawierających katalogi wirtualne. Dostęp do aplikacji w lokacji można uzyskać za pomocą jednego lub kilku powiązań usług IIS. Powiązanie usług IIS zawiera dwie informacje: powiązania dotyczące protokołu i powiązania. Protokół powiązania definiuje schemat, w którym odbywa się komunikacja, a informacje o powiązaniu są informacjami używanymi do uzyskiwania dostępu do witryny. Przykładem protokołu powiązania może być HTTP, natomiast informacje o powiązaniu mogą zawierać adres IP, port, nagłówek hosta itp.<br /><br /> Usługi IIS obsługują Określanie wielu powiązań usług IIS dla każdej witryny, co daje w wyniku wiele adresów bazowych na schemat. Jednak usługa Windows Communication Foundation (WCF) hostowana w ramach lokacji umożliwia powiązanie z tylko jedną baseAddress na schemat.<br /><br /> Aby włączyć wiele powiązań usług IIS dla każdej witryny dla usługi Windows Communication Foundation (WCF), ustaw ten atrybut `true`na. Zauważ, że wiele powiązań witryny jest obsługiwana tylko dla protokołu HTTP. Adres punktów końcowych w pliku konfiguracji musi być kompletnym identyfikatorem URI.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|Kolekcja elementów konfiguracji, które określają filtry prefiksu dla adresów bazowych używanych przez hosta usługi.|  
|[\<> ServiceActivations](serviceactivations.md)|Sekcja konfiguracji opisująca ustawienia aktywacji.|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|Kolekcja elementów konfiguracji, które identyfikują typ określonego transportu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Modelu|Element główny wszystkich elementów konfiguracji Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie usługi WCF działają równolegle z ASP.NET w domenach hostowanych aplikacji (AppDomain). Mimo że WCF i ASP.NET mogą współistnieć w tej samej domenie aplikacji, domyślnie żądania WCF nie są przetwarzane przez potok HTTP ASP.NET. W związku z tym niektóre elementy platformy aplikacji ASP.NET nie są dostępne dla usług WCF. Obejmują one  
  
- ASP.NET autoryzacja plików/adresów URL  
  
- Personifikacja ASP.NET  
  
- Stan sesji na podstawie pliku cookie  
  
- HttpContext. Current  
  
- Rozszerzalność potoku za pomocą niestandardowego modułu HttpModule  
  
 Jeśli usługi WCF muszą działać w kontekście ASP.NET i komunikować się tylko za pośrednictwem protokołu HTTP, można użyć trybu zgodności ASP.NET programu WCF. Ten tryb jest włączony, `aspNetCompatibilityEnabled` gdy atrybut jest ustawiony na `true` na poziomie aplikacji. Implementacje usług muszą deklarować możliwość uruchamiania w trybie zgodności przy użyciu <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> klasy. Gdy tryb zgodności jest włączony,  
  
- ASP.NET autoryzacja plików/adresów URL jest wymuszana przed autoryzacją WCF. Decyzja o autoryzacji jest oparta na tożsamości na poziomie transportu żądania. Tożsamości na poziomie komunikatu są ignorowane.  
  
- Operacje usługi WCF zaczynają działać w kontekście personifikacji ASP.NET. W przypadku włączenia zarówno personifikacji ASP.NET, jak i personifikacji WCF dla określonej usługi stosuje się kontekst personifikacji WCF.  
  
- Element HttpContext. Current może być używany z kodu usługi WCF, a usługi nie mogą uwidaczniać punktów końcowych innych niż HTTP.  
  
- Żądania WCF są przetwarzane przez potok ASP.NET. Elementy HttpModules, które zostały skonfigurowane do działania na żądania przychodzące mogą również przetwarzać żądania WCF. Mogą one obejmować składniki platformy ASP.NET (np. <xref:System.Web.SessionState.SessionStateModule>), a także niestandardowe moduły innych firm.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak włączyć tryb zgodności ASP.  
  
## <a name="code"></a>Kod  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [Hosting](../../../wcf/feature-details/hosting.md)
- [Usługi WCF i platforma ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md)
