---
title: x:Members — dyrektywa
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: c751a4f1cdea8dce7ef5165f5225ab3a825c7344
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071466"
---
# <a name="xmembers-directive"></a>x:Members — dyrektywa
Zawiera zestaw elementów członkowskich, które są zdefiniowane w znacznikach, które mają zastosowanie do x:Class elementu nadrzędnego.

## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML

```xaml
<object x:Class="className">
<x:Members>
  oneOrMoreMembers
</x:Members
</object>
```

## <a name="xaml-values"></a>Wartości XAML

|||
|-|-|
|`className`|Nazwa klasy zapasowej lub klasy częściowej dla produkcji XAML. Zobacz uwagi.|
|`oneOrMoreMembers`|Jeden lub więcej elementów obiektu, które reprezentują definicje elementów członkowskich. Zazwyczaj są `x:Property` to elementy obiektu. Zobacz uwagi.|

## <a name="remarks"></a>Uwagi

W implementacji usług .NET XAML services nie ma `x:Members`żadnej klasy kopii zapasowej ani podstawowej implementacji elementu członkowskiego dla . `x:Members`jest specjalnym elementem członkowskim XAML, który może istnieć jako element członkowski dowolnego typu. W strumieniu węzła `x:Members` XAML jest reprezentowany jako członek o nazwie `Members`, z obszaru nazw XAML języka XAML. Element `Members` członkowski zawiera ogólną `Member` listę obiektów tylko do odczytu. W typowych znaczników poszczególnych `x:Property` elementów członkowskich są określone jako elementy właściwości. `x:Property`jest bardziej precyzyjnym typem specjalnie dla właściwości typów `x:Member`i można go przypisać do . Aby uzyskać więcej informacji, zobacz [x:Property Directive](xproperty-directive.md).

Aby obsługiwać praktyczne `x:Members` użycie jako środek do określenia definicji elementów członkowskich w znacznikach, elementy członkowskie muszą być skojarzone z klasą, która może być modyfikowana. Zamierzony model `x:Members` jest, który istnieje jako element członkowski typu, który określa `x:Class`. Jednak mechanizm kojarzenia typów i elementów członkowskich lub tworzenia dynamicznych definicji elementów członkowskich nie jest obsługiwany na poziomie usług .NET XAML Services. Jest to pozostawione poszczególnych struktur, które mają modele aplikacji, które obsługują definicje elementów członkowskich z XAML. Zazwyczaj MSBUILD akcji kompilacji, które znaczników kompilować XAML i zintegrować go z kodem lub produkcji czystych z XAML zestawy są potrzebne do obsługi tej funkcji.

## <a name="xmembers-for-windows-workflow-foundation"></a>x:Członkowie fundacji przepływu pracy systemu Windows

W przypadku programu `x:Members` Windows Workflow Foundation zawiera elementy członkowskie działania niestandardowego składającego się w całości z XAML lub XAML — zdefiniowanych dynamicznych elementów członkowskich dla projektanta działań z kodem. `x:Class`należy również określić w elemencie głównym produkcji XAML. Nie jest to wymagane na poziomie usług .NET XAML Services, ale staje się wymaganiem, gdy produkcja XAML jest ładowana przez akcje kompilacji MSBUILD, które obsługują działania niestandardowe i XAML XAML programu Windows Workflow Foundation w ogóle. `x:Members`musi być pierwszym elementem podrzędnym w znacznikach `x:Class`elementu obiektu, który deklaruje .
