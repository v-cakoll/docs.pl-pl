---
title: x:Reference — Rozszerzenie znaczników
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: f06e259893111a436e5afe2df754c3edee326d54
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071382"
---
# <a name="xreference-markup-extension"></a>x:Reference — Rozszerzenie znaczników

Odwołuje się do wystąpienia, które jest zadeklarowane w innym miejscu znaczników XAML. Odwołanie odnosi się do elementu `x:Name`.

## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML

```xaml
<object property="{x:Reference instancexName}" .../>
```

## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML

```xaml
<object>
  <object.property>
    <x:Reference Name="instancexName"/>
  </object.property>
</object>
```

## <a name="xaml-values"></a>Wartości XAML

|||
|-|-|
|`instancexName`|Wartość `x:Name` (lub wartość <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>właściwości -identified) wystąpienia, do którego istnieje odwołanie.|

## <a name="remarks"></a>Uwagi

`x:Reference`zapewnia obsługę na poziomie języka XAML dla koncepcji odwołania do elementu, która została w przeciwnym razie zaimplementowana w określonych ramach, takich jak WPF.

## <a name="xreference-and-wpf"></a>x:Odwołanie i WPF

W WPF WPF I XAML 2006 odwołania do elementów są adresowane przez funkcję na poziomie struktury <xref:System.Windows.Data.Binding.ElementName%2A> powiązania. W przypadku większości aplikacji i <xref:System.Windows.Data.Binding.ElementName%2A> scenariuszy WPF powiązanie powinno być nadal używane. Wyjątki od tych ogólnych wskazówek mogą obejmować przypadki, w których istnieją kontekst danych lub inne zagadnienia dotyczące zakresu, które sprawiają, że powiązanie danych jest niepraktyczne i w których kompilacja znaczników nie jest zaangażowana.

`x:Reference`jest konstrukcją zdefiniowaną w XAML 2009. W WPF WPF można użyć funkcji XAML 2009, ale tylko dla XAML, który nie jest Skompilowany znaczników WPF. Markup-skompilowany XAML i BAML formie XAML obecnie nie obsługują XAML 2009 słowa kluczowe i funkcje języka.
