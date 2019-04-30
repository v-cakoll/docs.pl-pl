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
ms.openlocfilehash: 6144bcbda69b2ba799e87c3e7fa2118fbe4d9bf6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673746"
---
# <a name="performancecounters-element"></a>\<performanceCounters> Element

Określa rozmiar pamięci globalnej współużytkowane przez liczniki wydajności.

 \<Konfiguracja > \
\<system.diagnostics>\
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
|`system.diagnostics`|Określa element root dla sekcji konfiguracyjnej platformy ASP.NET.|

## <a name="remarks"></a>Uwagi

Liczniki wydajności użycia plików zamapowanych w pamięci lub pamięci współdzielonej, do publikowania danych wydajności.  Rozmiar pamięci współużytkowanej Określa, ile wystąpień, które może być użyty tylko raz.  Istnieją dwa rodzaje pamięci współużytkowanej: globalnego udostępnionych i oddzielnych pamięci udostępnionej.  Globalne pamięci współużytkowanej jest używana przez wszystkich kategorii licznika wydajności, instalowany z .NET Framework w wersji 1.0 i 1.1.  Kategorie liczników wydajności, instalowany z .NET Framework w wersji 2.0 za pomocą osobnych pamięci współużytkowanej, każdej kategorii licznika wydajności własnej pamięci posiadające.

Rozmiar pamięci współużytkowanej globalnych można ustawić tylko przy użyciu pliku konfiguracji.  Domyślny rozmiar to 524,288 bTak, maksymalny rozmiar to 33,554,432 bajtów i minimalny rozmiar to 32 768 bajtów.  Ponieważ globalnej pamięci współdzielonej jest współużytkowany przez wszystkie procesy i kategorie, pierwszy twórca Określa rozmiar.  Jeśli rozmiar jest zdefiniowana w pliku konfiguracyjnym aplikacji, ten rozmiar jest używana tylko, jeśli aplikacja jest pierwszą aplikację, który powoduje, że liczników wydajności do wykonania.  W związku z tym poprawnej lokalizacji, aby określić `filemappingsize` wartość jest pliku Machine.config.  Nie można zwolnić pamięć w globalnej pamięci współdzielonej przez liczniki wydajności poszczególnych, więc po pewnym czasie wyczerpania globalnej pamięci współdzielonej, gdy tworzonych jest wiele wystąpień licznika wydajności pod różnymi nazwami.

Dla rozmiaru pamięci współużytkowanej oddzielne w rejestrze wartość DWORD FileMappingSize klucza HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<nazwa kategorii >* mowa \Performance Po pierwsze a następnie wartość określona dla globalnych pamięci współużytkowanej w pliku konfiguracji. Jeśli wartość FileMappingSize nie istnieje, a następnie rozmiar oddzielne Pamięć współużytkowana jest ustawiony do jednej czwartej (1/4) ustawienie globalne w pliku konfiguracji.

## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
