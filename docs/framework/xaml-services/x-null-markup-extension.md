---
title: "x:Null — Rozszerzenie znaczników"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- Null
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a60d74bdf3343d02eaf912ac7700f36a649f659c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xnull-markup-extension"></a>x:Null — Rozszerzenie znaczników
Określa `null` jako wartość dla elementu członkowskiego XAML.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Uwagi  
 Słowo kluczowe odwołanie o wartości null w [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] i [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] ma wartość null. [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)] — Słowo kluczowe dla odwołanie o wartości null jest `Nothing`, ale zawsze używaj `{x:Null}` jako użycia XAML niezależnie od języka kodu z opóźnieniem, w którym jest skojarzona z XAML.  
  
 `x:Null` — Rozszerzenie znaczników nie ma można ustawić właściwości.  
  
 Użycie wartości null jest często skojarzony z ujawnienia elementu członkowskiego XAML CLR <xref:System.Nullable%601> wartość.  
  
 `x:Null` — Rozszerzenie znaczników, podobnie jak wszystkie rozszerzenia znaczników XAML, używa nawiasy klamrowe (`{,}`) dla anulowanie obsługi wartości atrybutów, aby być inne niż literały lub odwołania do obsługi zdarzeń. Składnia atrybutu jest składnia najczęściej używane dla tego rozszerzenia znacznika. Składnia elementu obiektu `<x:Null />` jest technicznie możliwe, ale jest rzadko używana, ponieważ `x:Null` — rozszerzenie znaczników nie ma parametrów pozycyjnych ani konstrukcji argumentów.  
  
 Aby uzyskać informacje na temat rozszerzeń znaczników, zobacz [rozszerzenia znaczników i WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 W programie .NET Framework XAML Services obsługę tego rozszerzenia znacznika jest definiowana za pomocą <xref:System.Windows.Markup.NullExtension> klasy.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 Należy pamiętać, że `null` niekoniecznie początkowej nie ustawiono wartości dla właściwości zależności typu odwołania. Wartość domyślna początkowej mogą się różnić dla każdej właściwości zależności i mogą być oparte na metadane dotyczące właściwości. Wiele właściwości zależności nie akceptują `null` jako wartość, przy użyciu znaczników lub kodu ze względu na ich implementacji wywołanie zwrotne weryfikacji. Aby uzyskać więcej informacji na temat właściwości zależności, zobacz [Przegląd właściwości zależności](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.DependencyProperty.UnsetValue>  
 [Omówienie XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozszerzenia znaczników i WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
