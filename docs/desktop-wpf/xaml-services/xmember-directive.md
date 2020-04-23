---
title: x:Member — dyrektywa
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: e82bb6397404ee466a12ab438585ae1898c34d1a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071473"
---
# <a name="xmember-directive"></a>x:Member — dyrektywa
Deklaruje element członkowski XAML w znacznikach.

## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML

```xaml
<object x:Class="className">
  <x:Members>
    <x:Member Name="propertyName"/>
    additionalMembers
  </x:Members>
</object>
```

## <a name="xaml-values"></a>Wartości XAML

|||
|-|-|
|`className`|Nazwa klasy zapasowej lub klasy częściowej dla produkcji XAML.|
|`memberName`|Nazwa elementu członkowskiego zdefiniowanej właściwości.|

## <a name="remarks"></a>Uwagi

W implementacji usług .NET XAML , . `x:Member`nie ma bezpośredniego wsparcia typu, ale jest <xref:System.Windows.Markup.MemberDefinition> obsługiwany przez klasę. W strumieniu węzła XAML element `x:Member` jest reprezentowany jako członek o nazwie `Member`, z obszaru nazw XAML języka XAML. Element `Member` członkowski przechowuje atrybuty zadeklarowane przez znaczniki.

Znaczenie `Name` i `Type` nie są przypisane na poziomie usług .NET XAML Services. Są one przechowywane w początkowym strumieniu węzła XAML jako wartości ciągu, które mają być interpretowane później zgodnie z regułami, które mogą być nałożone przez określone struktury. Znaczenie może być wyrównane do nazwy XAML i typu XAML znaczenie lub może być prawidłowy tylko w systemie typu kopii zapasowej, w zależności od implementacji.

Aby obsługiwać praktyczne `x:Members` użycie jako środek do określenia definicji elementów członkowskich w znacznikach, elementy członkowskie muszą być skojarzone z klasą, która może być modyfikowana. Zamierzony model `x:Members` jest, który istnieje jako element członkowski typu, który określa `x:Class`. Jednak mechanizm kojarzenia typów i elementów członkowskich lub tworzenia dynamicznych definicji elementów członkowskich nie jest obsługiwany na poziomie usług .NET XAML Services. Jest to pozostawione poszczególnych struktur, które mają modele aplikacji, które obsługują definicje elementów członkowskich z XAML. Zazwyczaj MSBUILD akcji kompilacji, które znaczników kompilować XAML i zintegrować go z kodem lub produkcji czystych z XAML zestawy są potrzebne do obsługi tej funkcji.

## <a name="xproperty-for-windows-workflow-foundation"></a>x:Właściwość dla fundacji przepływu pracy systemu Windows

W przypadku programu `x:Property` Windows Workflow Foundation definiuje elementy członkowskie działania niestandardowego składającego się w całości z XAML lub XAML — zdefiniowanych dynamicznych elementów członkowskich dla projektanta działań z kodem. `x:Class`należy również określić w elemencie głównym produkcji XAML. Nie jest to wymagane na poziomie usług .NET XAML Services, ale staje się wymaganiem, gdy produkcja XAML jest ładowana przez akcje kompilacji MSBUILD, które obsługują działania niestandardowe i XAML XAML programu Windows Workflow Foundation w ogóle. Windows Workflow Foundation nie używa czystej nazwy typu XAML `x:Property` `Type` jako jego zamierzonej wartości dla atrybutu, a zamiast tego używa konwencji, która nie jest opisana w tym miejscu. Aby uzyskać więcej informacji, zobacz [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).
