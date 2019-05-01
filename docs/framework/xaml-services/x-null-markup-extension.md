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
ms.openlocfilehash: e46d8561b62d9137d4fed4df447338a97fc0577b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938918"
---
# <a name="xnull-markup-extension"></a>x:Null — Rozszerzenie znaczników
Określa `null` jako wartość dla elementu członkowskiego XAML.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Uwagi  
 Słowo kluczowe odwołanie o wartości null w C# i [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] ma wartość null. Słowo kluczowe języka Visual Basic dla odwołanie o wartości null jest `Nothing`, ale zawsze używaj `{x:Null}` jako użycie XAML niezależnie od tego, jaki język związanym z kodem, należy skojarzyć z XAML.  
  
 `x:Null` — Rozszerzenie znaczników nie ma żadnych właściwości do ustawienia.  
  
 Użycie o wartości null jest często kojarzona z narażenia elementu członkowskiego XAML CLR <xref:System.Nullable%601> wartość.  
  
 `x:Null` — Rozszerzenie znaczników, takich jak wszystkie rozszerzenia znaczników XAML używa nawiasów klamrowych (`{,}`) do anulowania obsługi wartości atrybutów były inne niż literały ani odwołania do obsługi zdarzeń. Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Składnia elementu obiektu `<x:Null />` jest technicznie możliwe, ale jest rzadko używana, ponieważ `x:Null` — rozszerzenie znaczników nie ma parametry pozycyjne ani argumentów.  
  
 Aby uzyskać informacje na temat rozszerzeń znaczników, zobacz [rozszerzenia znacznikowania i WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 W programie .NET Framework XAML Services obsługi dla tego rozszerzenia znacznika jest definiowany przez <xref:System.Windows.Markup.NullExtension> klasy.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użytkowania WPF  
 Należy pamiętać, że `null` niekoniecznie jest początkowa nie ustawiono wartość dla właściwości zależności typu odwołania. Wartość domyślna początkowej mogą się różnić dla każdej właściwości zależności i mogą opierać się na metadane właściwe dla właściwości. Wiele właściwości zależności nie są akceptowane `null` jako wartość za pomocą znaczników lub innego kodu ze względu na ich implementacji wywołanie zwrotne weryfikacji. Aby uzyskać więcej informacji na temat właściwości zależności zobacz [Przegląd właściwości zależności](../wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [Przegląd XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [Rozszerzenia znaczników i WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
