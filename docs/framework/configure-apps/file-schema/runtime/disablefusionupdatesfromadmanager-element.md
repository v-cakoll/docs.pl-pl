---
title: <disableFusionUpdatesFromADManager> Element
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: 4e7375fddaa98b45766b29d911d555f773edcafa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117444"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<disableFusionUpdatesFromADManager> Element
Określa, czy domyślne zachowanie, które umożliwia hostowi środowiska uruchomieniowego przesłonięcie ustawień konfiguracji dla domeny aplikacji, jest wyłączone.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableFusionUpdatesFromADManager>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|enabled|Atrybut wymagany.<br /><br /> Określa, czy domyślna możliwość przesłonięcia ustawień Fusion jest wyłączona.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|0|Nie należy wyłączać możliwości przesłonięcia ustawień Fusion. Jest to zachowanie domyślne, zaczynając od .NET Framework 4.|  
|1|Wyłącz możliwość przesłonięcia ustawień Fusion. Spowoduje to przywrócenie zachowania wcześniejszych wersji .NET Framework.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od .NET Framework 4, domyślnym zachowaniem jest umożliwienie <xref:System.AppDomainManager> obiektowi przesłania ustawień konfiguracji przy użyciu <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwości lub <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody <xref:System.AppDomainSetup> obiektu, który jest przesyłany do implementacji <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody w podklasy <xref:System.AppDomainManager> . W przypadku domyślnej domeny aplikacji zmiany ustawień zastępują ustawienia, które zostały określone przez plik konfiguracyjny aplikacji. W przypadku innych domen aplikacji zastępują one ustawienia konfiguracji, które zostały przesłane do <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metody lub.  
  
 Można przekazać nowe informacje konfiguracyjne lub przekazać wartość null ( `Nothing` w Visual Basic), aby wyeliminować przekazane informacje o konfiguracji.  
  
 Nie przekazuj informacji o konfiguracji do <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwości i <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody. W przypadku przekazania informacji o konfiguracji do obu tych informacji przekazywane do <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwości zostanie zignorowane, ponieważ <xref:System.AppDomainSetup.SetConfigurationBytes%2A> Metoda przesłania informacje o konfiguracji z pliku konfiguracyjnego aplikacji. W przypadku użycia <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwości można przekazać wartość null ( `Nothing` w Visual Basic) do <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody, aby wyeliminować wszystkie bajty konfiguracyjne, które zostały określone w wywołaniu <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metody lub.  
  
 Oprócz informacji o konfiguracji można zmienić następujące ustawienia w <xref:System.AppDomainSetup> obiekcie, który jest przesyłany do implementacji metody:,,,,,,,,,, <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomainSetup.ApplicationName%2A> <xref:System.AppDomainSetup.CachePath%2A> <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A> <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> <xref:System.AppDomainSetup.DisallowCodeDownload%2A> <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> <xref:System.AppDomainSetup.DynamicBase%2A> <xref:System.AppDomainSetup.LoaderOptimization%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A> <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> , i <xref:System.AppDomainSetup.ShadowCopyFiles%2A> .  
  
 Alternatywą wobec korzystania z `<disableFusionUpdatesFromADManager>` elementu jest wyłączenie domyślnego zachowania przez utworzenie ustawienia rejestru lub ustawienie zmiennej środowiskowej. W rejestrze utwórz wartość DWORD o nazwie `COMPLUS_disableFusionUpdatesFromADManager` w obszarze `HKCU\Software\Microsoft\.NETFramework` lub `HKLM\Software\Microsoft\.NETFramework` , a następnie ustaw wartość 1. W wierszu polecenia Ustaw wartość zmiennej środowiskowej `COMPLUS_disableFusionUpdatesFromADManager` na 1.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyłączyć możliwość zastąpienia ustawień Fusion przy użyciu `<disableFusionUpdatesFromADManager>` elementu.  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../deployment/how-the-runtime-locates-assemblies.md)
