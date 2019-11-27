---
title: GCLOHThreshold, element
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451221"
---
# <a name="gclohthreshold-element"></a>GCLOHThreshold, element

Określa rozmiar progu (w bajtach), który powoduje, że moduł wyrzucania elementów bezużytecznych umieszcza obiekty na stercie dużego obiektu (LOH).

[\<> konfiguracji](../configuration-element.md)\
&nbsp;&nbsp;[\<środowiska uruchomieniowego >](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold >

## <a name="syntax"></a>Składnia

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`enabled`|Atrybut wymagany.<br /><br />Określa rozmiar progu, który powoduje, że obiekty przechodzą na stertę dużego obiektu.|

### <a name="enabled-attribute"></a>włączony atrybut

|Wartość|Opis|
|-----------|-----------------|
|`nnnn`|Rozmiar progu, w bajtach, który powoduje, że obiekty przechodzą na stertę dużego obiektu.|

## <a name="child-elements"></a>Elementy podrzędne

Brak.

## <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|

## <a name="remarks"></a>Uwagi

To ustawienie zostało wprowadzone w .NET Framework 4,8.

## <a name="see-also"></a>Zobacz także

- [Schemat ustawień czasu wykonywania](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Podstawowe informacje dotyczące wyrzucania elementów bezużytecznych](../../../../standard/garbage-collection/fundamentals.md)
- [Podstawowe opcje konfiguracji sieci w czasie wykonywania dla usługi GC](../../../../core/run-time-config/garbage-collector.md)
