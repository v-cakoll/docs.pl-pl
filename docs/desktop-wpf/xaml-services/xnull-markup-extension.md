---
title: x:Null — Rozszerzenie znaczników
ms.date: 03/30/2017
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
ms.openlocfilehash: b83e893f951c15eca69fbb6b002369dd723ca469
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071431"
---
# <a name="xnull-markup-extension"></a>x:Null — Rozszerzenie znaczników

Określa `null` jako wartość dla elementu członkowskiego XAML.

## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a>Uwagi

Słowo kluczowe dla odwołania null w języku C# i C++ ma wartość null. Słowo kluczowe Microsoft Visual Basic `Nothing`dla odwołania null `{x:Null}` jest , ale zawsze używasz jako użycia XAML, niezależnie od tego, który język związany z kodem jest skojarzony z XAML.

Rozszerzenie `x:Null` znaczników nie ma właściwości settable.

Użycie wartości null jest często skojarzone z ekspozycją <xref:System.Nullable%601> elementu członkowskiego XAML wartości CLR.

Rozszerzenie `x:Null` znaczników, podobnie jak wszystkie rozszerzenia znaczników XAML,`{,}`używa nawiasów klamrowych ( ) do uciekania obsługi wartości atrybutów, które mają być inne niż literały lub odwołania do obsługi zdarzeń. Składnia atrybutów jest składnią najczęściej używaną z tym rozszerzeniem znaczników. Składnia elementu obiektu `<x:Null />` jest technicznie możliwa, ale `x:Null` jest rzadko używana, ponieważ rozszerzenie znaczników nie ma parametrów pozycyjnych ani argumentów konstrukcyjnych.

Aby uzyskać informacje na temat rozszerzeń znaczników, zobacz [Rozszerzenia znaczników i WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).

W usługach .NET XAML obsługa tego rozszerzenia znaczników <xref:System.Windows.Markup.NullExtension> jest definiowana przez klasę.

## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF

Należy `null` zauważyć, że niekoniecznie jest początkowa wartość unset dla właściwości zależności typu odwołania. Początkowa wartość domyślna może się różnić dla każdej właściwości zależności i może być oparta na metadanych specyficznych dla właściwości. Wiele właściwości zależności nie `null` akceptuje jako wartość, za pośrednictwem znaczników lub kodu ze względu na ich implementacje wywołania zwrotnego sprawdzania poprawności. Aby uzyskać więcej informacji na temat właściwości zależności, zobacz [Omówienie właściwości zależności](../../framework/wpf/advanced/dependency-properties-overview.md).

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [Omówienie XAML (WPF)](../fundamentals/xaml.md)
- [Rozszerzenia znacznikowania i WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
