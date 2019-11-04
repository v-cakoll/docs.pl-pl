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
ms.openlocfilehash: ff82b0bfc1983240431e582dbd78778dc4469241
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459944"
---
# <a name="xnull-markup-extension"></a>x:Null — Rozszerzenie znaczników
Określa `null` jako wartość elementu członkowskiego języka XAML.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Uwagi  
 Słowo kluczowe dla odwołania o wartości null C# w C++ i ma wartość null. Słowo kluczowe Microsoft Visual Basic dla odwołania o wartości null jest `Nothing`, ale zawsze używasz `{x:Null}` jako użycia XAML niezależnie od tego, jaki język związany z kodem jest skojarzony z XAML.  
  
 Rozszerzenie znacznika `x:Null` nie ma właściwości settable.  
  
 Użycie wartości null jest często związane z narażeniem elementu członkowskiego języka XAML na wartość <xref:System.Nullable%601> CLR.  
  
 `x:Null` rozszerzenie znacznika, podobnie jak wszystkie rozszerzenia znaczników XAML, używa nawiasów (`{,}`) do ucieczki obsługi wartości atrybutów, aby były inne niż literały lub odwołania do obsługi zdarzeń. Składnia atrybutu jest składnią najczęściej używaną z tym rozszerzeniem znacznika. Składnia elementu obiektu `<x:Null />` jest technicznie możliwa, ale rzadko jest używana, ponieważ rozszerzenie znaczników `x:Null` nie ma parametrów pozycyjnych ani argumentów konstrukcyjnych.  
  
 Aby uzyskać informacje na temat rozszerzeń znaczników, zobacz [rozszerzenia znaczników i XAML WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 W .NET Framework usługach XAML obsługa tego rozszerzenia znacznika jest definiowana przez klasę <xref:System.Windows.Markup.NullExtension>.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 Należy pamiętać, że `null` nie musi być początkową wartością ustawienia dla właściwości zależności typu odwołania. Początkowa wartość domyślna może różnić się w zależności od właściwości zależności i może opierać się na metadanych specyficznych dla właściwości. Wiele właściwości zależności nie akceptuje `null` jako wartości, za pomocą znaczników ani kodu z powodu implementacji wywołania zwrotnego walidacji. Aby uzyskać więcej informacji na temat właściwości zależności, zobacz [Omówienie właściwości zależności](../wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [Przegląd XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
- [Rozszerzenia znaczników i WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
