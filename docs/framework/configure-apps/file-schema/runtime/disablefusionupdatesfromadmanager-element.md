---
title: '&lt;disablefusionupdatesfromadmanager —&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e5e33cd3d250b26f0a83a87c4f7ce438af22e96
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltdisablefusionupdatesfromadmanagergt-element"></a>&lt;disablefusionupdatesfromadmanager —&gt; — Element
Określa, czy zachowanie domyślne, czyli aby umożliwić host czasu wykonywania w celu zastąpienia ustawień konfiguracji dla domeny aplikacji jest wyłączone.  
  
 \<Konfiguracja > — Element  
\<środowisko uruchomieniowe > — Element  
\<disablefusionupdatesfromadmanager — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|włączone|Atrybut wymagany.<br /><br /> Określa, czy domyślne możliwość zastąpienia ustawień Fusion jest wyłączona.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|0|Nie wyłączaj możliwości zastępują ustawienia Fusion. Jest to zachowanie domyślne, począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
|1|Wyłącz możliwości zastępują ustawienia Fusion. Spowoduje to przywrócenie zachowania wcześniejszych wersji programu .NET Framework.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], domyślne zachowanie jest umożliwienie <xref:System.AppDomainManager> obiektu w celu zastąpienia ustawień konfiguracji za pomocą <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwości lub <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody <xref:System.AppDomainSetup> obiektu, który jest przekazywany do implementacji z <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody w Twojej podklasą klasy <xref:System.AppDomainManager>. Dla domyślnej domeny aplikacji ustawienia, które można zmienić zastępują ustawienia, które zostały określone w pliku konfiguracyjnym aplikacji. W przypadku innych domen aplikacji zastępują one ustawienia konfiguracji, które zostały przekazane do <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> lub <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metody.  
  
 Możesz przekazać nowe informacje o konfiguracji, lub należy przekazać wartość null (`Nothing` w języku Visual Basic) w celu usunięcia informacji o konfiguracji, która została przekazana.  
  
 Informacje o konfiguracji nie są przekazywane do obu <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwości i <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody. Zarówno w przypadku przekazania informacji o konfiguracji, informacje są przekazywane do <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwość jest ignorowana, ponieważ <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metoda zastępuje informacje o konfiguracji z pliku konfiguracji aplikacji. Jeśli używasz <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwości, można przekazać wartości null (`Nothing` w języku Visual Basic) do <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metodę, aby wyeliminować żadnych bajtów konfiguracji, które zostały określone w wywołaniu <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> lub <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metody.  
  
 Oprócz informacji o konfiguracji, można zmienić następujących ustawień na <xref:System.AppDomainSetup> obiekt, który jest przekazywany do implementacji <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, i <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.  
  
 Alternatywą wobec przy użyciu `<disableFusionUpdatesFromADManager>` elementu, można wyłączyć domyślnego zachowania tworząc ustawienie rejestru lub przez ustawienie zmiennej środowiskowej. W rejestrze, utwórz wartość DWORD o nazwie `COMPLUS_disableFusionUpdatesFromADManager` w obszarze `HKCU\Software\Microsoft\.NETFramework` lub `HKLM\Software\Microsoft\.NETFramework`, a następnie ustaw wartość na 1. W wierszu polecenia, ustaw zmienną środowiskową `COMPLUS_disableFusionUpdatesFromADManager` do 1.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyłączenie możliwości zastępują ustawienia Fusion przy użyciu `<disableFusionUpdatesFromADManager>` elementu.  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
