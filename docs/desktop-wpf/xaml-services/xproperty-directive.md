---
title: x:Property — dyrektywa
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: 2804ec935d0626cba9ef050f70a3266cf23bcce0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071410"
---
# <a name="xproperty-directive"></a>x:Property — dyrektywa

Deklaruje właściwość XAML w znacznikach.

## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML

```xaml
<object x:Class="className">
  <x:Members>
    <x:Property Name="propertyName" Type="propertyType"/>
    additionalProperties
  </x:Members>
</object>
```

## <a name="xaml-values"></a>Wartości XAML

|||
|-|-|
|`className`|Nazwa klasy zapasowej lub klasy częściowej dla produkcji XAML.|
|`propertyName`|Nazwa elementu członkowskiego zdefiniowanej właściwości.|
|`propertyType`|Nazwa typu (lub inny formularz ciągu, specyficzne dla struktury), który określa typ tej właściwości.|

## <a name="remarks"></a>Uwagi

W implementacji usług .NET XAML , . `x:Property`nie ma bezpośredniego wsparcia typu, ale jest <xref:System.Windows.Markup.PropertyDefinition> obsługiwany przez klasę. W strumieniu węzła XAML element `x:Property` jest reprezentowany jako członek o nazwie `Property`, z obszaru nazw XAML języka XAML. Element `Property` członkowski przytrzymaj atrybuty zadeklarowane przez znaczniki.

Znaczenie `Name` i `Type` nie są przypisane na poziomie usług .NET XAML Services. Są one przechowywane w początkowym strumieniu węzła XAML jako wartości ciągu, które mają być interpretowane później zgodnie z regułami, które mogą być nałożone przez określone struktury. Znaczenie może być wyrównane do nazwy XAML i typu XAML znaczenie lub może być prawidłowy tylko w systemie typu kopii zapasowej, w zależności od implementacji.

Aby obsługiwać praktyczne `x:Members` użycie jako środek do określenia definicji elementów członkowskich w znacznikach, elementy członkowskie muszą być skojarzone z klasą, która może być modyfikowana. Zamierzony model `x:Members` jest, który istnieje jako element członkowski typu, który określa `x:Class`. Jednak mechanizm kojarzenia typów i elementów członkowskich lub tworzenia dynamicznych definicji elementów członkowskich nie jest obsługiwany na poziomie usług .NET XAML Services. Jest to pozostawione poszczególnych struktur, które mają modele aplikacji, które obsługują definicje elementów członkowskich z XAML. Zazwyczaj MSBUILD akcji kompilacji, które znaczników kompilować XAML i zintegrować go z kodem lub produkcji czystych z XAML zestawy są potrzebne do obsługi tej funkcji.

## <a name="xproperty-for-windows-workflow-foundation"></a>x:Właściwość dla fundacji przepływu pracy systemu Windows

W przypadku programu `x:Property` Windows Workflow Foundation definiuje elementy członkowskie działania niestandardowego składającego się w całości z XAML lub XAML — zdefiniowanych dynamicznych elementów członkowskich dla projektanta działań z kodem. `x:Class`należy również określić w elemencie głównym produkcji XAML. Nie jest to wymagane na poziomie usług .NET XAML Services, ale staje się wymaganiem, gdy produkcja XAML jest ładowana przez akcje kompilacji MSBUILD, które obsługują działania niestandardowe i XAML XAML programu Windows Workflow Foundation w ogóle. Windows Workflow Foundation nie używa czystej nazwy typu XAML `x:Property` `Type` jako jego zamierzonej wartości dla atrybutu, a zamiast tego używa konwencji, która nie jest opisana w tym miejscu. Aby uzyskać więcej informacji, zobacz [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).
