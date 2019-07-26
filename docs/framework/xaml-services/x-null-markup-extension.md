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
ms.openlocfilehash: 7dbea2c7d4010d8defc572dbdc14a0dfd6d7601e
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484705"
---
# <a name="xnull-markup-extension"></a>x:Null — Rozszerzenie znaczników
Określa `null` jako wartość dla elementu członkowskiego języka XAML.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Uwagi  
 Słowo kluczowe dla odwołania o wartości null C# w C++ i ma wartość null. Słowo kluczowe Microsoft Visual Basic dla odwołania o wartości null `Nothing`to, ale jest zawsze `{x:Null}` używane jako użycie XAML, niezależnie od kodu związanego z kodem, który jest skojarzony z XAML.  
  
 Rozszerzenie `x:Null` znaczników nie ma właściwości settable.  
  
 Użycie wartości null jest często kojarzone ze współczynnikiem członkowskim języka XAML <xref:System.Nullable%601> dla wartości CLR.  
  
 Rozszerzenie znacznika, takie jak wszystkie rozszerzenia znaczników XAML, używa nawiasów (`{,}`) do ucieczki obsługi wartości atrybutów, aby były inne niż literały lub odwołania do obsługi zdarzeń. `x:Null` Składnia atrybutu jest składnią najczęściej używaną z tym rozszerzeniem znacznika. Składnia `<x:Null />` elementu obiektu jest technicznie możliwa, ale rzadko jest używana, `x:Null` ponieważ rozszerzenie znaczników nie ma parametrów pozycyjnych ani argumentów konstrukcji.  
  
 Aby uzyskać informacje na temat rozszerzeń znaczników, zobacz [rozszerzenia znaczników i XAML WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 W .NET Framework usługach XAML obsługa tego rozszerzenia znacznika jest definiowana przez <xref:System.Windows.Markup.NullExtension> klasę.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 Należy pamiętać `null` , że nie musi być początkową wartością ustawienia dla właściwości zależności typu odwołania. Początkowa wartość domyślna może różnić się w zależności od właściwości zależności i może opierać się na metadanych specyficznych dla właściwości. Wiele właściwości zależności nie akceptuje `null` jako wartości, za pomocą znaczników ani kodu ze względu na implementacje wywołania zwrotnego walidacji. Aby uzyskać więcej informacji na temat właściwości zależności, zobacz [Omówienie właściwości zależności](../wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [Przegląd XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [Rozszerzenia znaczników i WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
