---
title: '&lt;liczniki wydajności&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <perfomanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: cb4af08095c14c0c748a79f53104d8454d3dcd47
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754161"
---
# <a name="ltperformancecountersgt-element"></a>&lt;liczniki wydajności&gt; — Element
Określa rozmiar pamięci globalnej współużytkowane przez liczniki wydajności.  
  
 \<Konfiguracja >  
\<System.Diagnostics >  
\<performanceCounters>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<performanceCounters filemappingsize="524288" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|filemappingsize|Atrybut wymagany.<br /><br /> Określa rozmiar w bajtach pamięci globalnej współużytkowane przez liczniki wydajności. Wartość domyślna to 524288.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`Configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa element root dla sekcji konfiguracji ASP.NET.|  
  
## <a name="remarks"></a>Uwagi  
 Liczniki wydajności za pomocą plików mapowanych na pamięć lub pamięci współużytkowanej do publikowania danych wydajności.  Rozmiar pamięci współużytkowanej Określa, jak wiele wystąpień, które mogą być używane jednocześnie.  Istnieją dwa typy pamięci współużytkowanej: globalne udostępnionych pamięci i oddzielne pamięci współużytkowanej.  Globalnej pamięci współdzielonej jest używany przez wszystkie kategorii licznika wydajności zainstalowane wersje .NET Framework w wersji 1.0 lub 1.1.  Zainstalowane z .NET Framework w wersji 2.0 kategorii licznika wydajności za pomocą osobnych pamięci współużytkowanej, każdej kategorii licznika wydajności posiadanie własnej pamięci.  
  
 Rozmiar globalnej pamięci współdzielonej można ustawić tylko w pliku konfiguracji.  Rozmiar domyślny to 524,288 bTak, maksymalny rozmiar to 33,554,432 bajtów, a minimalny rozmiar to 32 768 bajtów.  Ponieważ globalnej pamięci współdzielonej jest współużytkowana przez wszystkie procesy i kategorie, twórca pierwszy Określa rozmiar.  Jeśli rozmiar jest zdefiniowana w pliku konfiguracyjnym aplikacji, ten rozmiar jest używane, jeśli aplikacja jest pierwszym aplikacji, która powoduje, że liczniki wydajności do wykonania.  W związku z tym właściwym miejscu, aby określić `filemappingsize` wartość jest plik Machine.config.  Nie można zwolnić pamięć w globalnej pamięci współdzielonej przez liczniki wydajności poszczególnych, więc po pewnym czasie wyczerpania globalnej pamięci współdzielonej jeśli są tworzone dużą liczbę wystąpień liczników wydajności o różnych nazwach.  
  
 Rozmiaru oddzielne pamięci współużytkowanej w rejestrze wartość DWORD FileMappingSize klucza HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<nazwa kategorii >* \Performance odwołuje się do najpierw a następnie wartość określona dla globalnej pamięci współdzielonej w pliku konfiguracji. Jeśli wartość FileMappingSize nie istnieje, a następnie czwarty co ma ustawianą wielkość pamięci współużytkowanej oddzielne (1/4) ustawienie globalne w pliku konfiguracji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.PerformanceCounter>  
 <xref:System.Diagnostics.PerformanceCounterCategory>  
 <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>  
 <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
