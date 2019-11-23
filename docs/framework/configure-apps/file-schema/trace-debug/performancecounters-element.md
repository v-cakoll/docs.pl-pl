---
title: <performanceCounters>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <performanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
ms.openlocfilehash: f52fdb2d5b0b7911de63f96663e70735d2f2496c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697151"
---
# <a name="performancecounters-element"></a>\<element > liczniki wydajności

Określa rozmiar pamięci globalnej udostępnionej przez liczniki wydajności.

[ **> konfiguracji \<** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<system. Diagnostics >** ](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<liczniki wydajności >**  

## <a name="syntax"></a>Składnia

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|filemappingsize|Atrybut wymagany.<br /><br /> Określa rozmiar pamięci globalnej udostępnionej przez liczniki wydajności w bajtach. Wartość domyślna to 524288.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`Configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`system.diagnostics`|Określa element główny dla sekcji konfiguracji ASP.NET.|

## <a name="remarks"></a>Uwagi

Liczniki wydajności używają pliku mapowanego na pamięć lub pamięci współdzielonej do publikowania danych wydajności.  Rozmiar pamięci współdzielonej określa, ile wystąpień może być używanych jednocześnie.  Istnieją dwa typy pamięci współdzielonej: globalna pamięć udostępniona i oddzielna pamięć współdzielona.  Globalna pamięć współdzielona jest używana przez wszystkie kategorie liczników wydajności zainstalowane z .NET Framework wersjami 1,0 lub 1,1.  Kategorie liczników wydajności zainstalowane z .NET Framework w wersji 2,0 używają oddzielnej pamięci współdzielonej, z każdą kategorią licznika wydajności mającą własną pamięć.

Rozmiar globalnej pamięci współdzielonej można ustawić tylko przy użyciu pliku konfiguracji.  Domyślny rozmiar to 524 288 bTak, maksymalny rozmiar to 33 554 432 bajtów, a minimalny rozmiar to 32 768 bajtów.  Ponieważ globalna pamięć udostępniona jest współdzielona przez wszystkie procesy i kategorie, pierwszy twórca określa rozmiar.  W przypadku zdefiniowania rozmiaru w pliku konfiguracyjnym aplikacji ten rozmiar jest używany tylko wtedy, gdy aplikacja jest pierwszą aplikacją, która powoduje wykonanie liczników wydajności.  W związku z tym poprawną lokalizacją określającą `filemappingsize` wartość jest plik Machine. config.  Pamięć w globalnej pamięci współdzielonej nie może zostać wydana przez poszczególne liczniki wydajności, więc ostatecznie globalna pamięć udostępniona jest wyczerpana, jeśli utworzono dużą liczbę wystąpień liczników wydajności o różnych nazwach.

W przypadku rozmiaru oddzielnej pamięci współdzielonej wartość DWORD FileMappingSize w kluczu rejestru HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\\ *\<nazwa kategorii >* , a następnie wartość określona dla globalnej pamięci współdzielonej w pliku konfiguracji. Jeśli wartość FileMappingSize nie istnieje, oddzielny rozmiar pamięci współdzielonej jest ustawiany na jeden czwarty (1/4) ustawienia globalne w pliku konfiguracji.

## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
