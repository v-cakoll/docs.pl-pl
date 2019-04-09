---
title: <disableFusionUpdatesFromADManager> Element
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27c8c1cac68aca1c40826ff549d62d9636d9b0c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085886"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<disableFusionUpdatesFromADManager> Element
Określa, czy należy wyłączyć zachowanie domyślne, które jest, aby zezwolić na host środowiska uruchomieniowego w celu zastąpienia ustawień konfiguracji domeny aplikacji.  
  
 \<Konfiguracja > Element  
\<środowisko uruchomieniowe > Element  
\<disableFusionUpdatesFromADManager>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Włączone|Atrybut wymagany.<br /><br /> Określa, czy należy wyłączyć domyślne możliwość przesłaniania ustawień Fusion.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|0|Nie należy wyłączać możliwość przesłaniania ustawień Fusion. Jest to domyślne zachowanie, począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
|1|Wyłącz możliwość zastąpienia ustawień Fusion. Spowoduje to przywrócenie zachowania wcześniejszych wersji programu .NET Framework.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], zachowanie domyślne jest umożliwienie <xref:System.AppDomainManager> obiekt, aby zastąpić ustawienia konfiguracji za pomocą <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwości lub <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody <xref:System.AppDomainSetup> obiektu, który jest przekazywany do implementacji z <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metodę, w swojej podklasą <xref:System.AppDomainManager>. Dla domyślnej domeny aplikacji ustawienia, które można zmienić zastąpienia ustawień, które zostały określone w pliku konfiguracyjnym aplikacji. W przypadku innych domen aplikacji zastępują ustawienia konfiguracji, które zostały przekazane do <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> lub <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metody.  
  
 Możesz przekazać nowe informacje o konfiguracji, lub przekazać wartości null (`Nothing` w języku Visual Basic), aby wyeliminować informacje o konfiguracji, która została przekazana.  
  
 Nie przekazuj informacje o konfiguracji zarówno <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwości i <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody. W przypadku przekazania informacji o konfiguracji na wartość oba, informacje są przekazywane do <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwość jest ignorowana, ponieważ <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metoda zastępuje informacje o konfiguracji z pliku konfiguracji aplikacji. Jeśli używasz <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwości, można przekazać wartości null (`Nothing` w języku Visual Basic) do <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metodę, aby wyeliminować wszelkie bajtów konfiguracji, które zostały określone w wywołaniu <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> lub <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metody.  
  
 Oprócz informacji o konfiguracji, można zmienić następujące ustawienia na <xref:System.AppDomainSetup> obiekt, który jest przekazywany do implementacji <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metoda: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, i <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.  
  
 Jako alternatywa dla użycia `<disableFusionUpdatesFromADManager>` elementu, możesz wyłączyć to zachowanie domyślne, tworząc ustawienie rejestru lub przez ustawienie zmiennej środowiskowej. W rejestrze Utwórz wartość DWORD o nazwie `COMPLUS_disableFusionUpdatesFromADManager` w obszarze `HKCU\Software\Microsoft\.NETFramework` lub `HKLM\Software\Microsoft\.NETFramework`, a następnie ustaw wartość na 1. W wierszu polecenia, należy ustawić zmienną środowiskową `COMPLUS_disableFusionUpdatesFromADManager` 1.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyłączyć możliwość zastąpienia ustawień łączenia za pomocą `<disableFusionUpdatesFromADManager>` elementu.  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
