---
title: "Jak zmienić typ kursora"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 41cd8c9cd647c7efbc4e6cf13517ed638245e51c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-change-the-cursor-type"></a>Jak zmienić typ kursora
W tym przykładzie pokazano, jak zmienić <xref:System.Windows.Input.Cursor> wskaźnika myszy dla określonego elementu i aplikacji.  
  
 W tym przykładzie składa się z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plików i pliku CodeBehind.  
  
## <a name="example"></a>Przykład  
 Interfejs użytkownika został utworzony, który składa się z <xref:System.Windows.Controls.ComboBox> wybrać żądaną <xref:System.Windows.Input.Cursor>, para <xref:System.Windows.Controls.RadioButton> obiektów do określenia, czy zmiany kursora dotyczy tylko jeden element i ma zastosowanie do całej aplikacji, a <xref:System.Windows.Controls.Border> czyli element nowy kursor jest stosowany do.  
  
 [!code-xaml[cursors#ChangeCursorsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 Poniższy kod za tworzy <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> obsługi zdarzeń, które jest wywoływane, gdy typ kursora została zmieniona w <xref:System.Windows.Controls.ComboBox>.  Instrukcja switch filtry kursora o nazwie i zestawy <xref:System.Windows.FrameworkElement.Cursor%2A> właściwości na <xref:System.Windows.Controls.Border> który o nazwie *DisplayArea*.  
  
 Jeśli zmiana kursora jest równa "Całą aplikację" <xref:System.Windows.Input.Mouse.OverrideCursor%2A> właściwość jest ustawiona na <xref:System.Windows.FrameworkElement.Cursor%2A> właściwość <xref:System.Windows.Controls.Border> formantu.  Dzięki temu kursor zmiany dla całej aplikacji.  
  
 [!code-csharp[cursors#ChangeCursorsSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dane wejściowe — omówienie](../../../../docs/framework/wpf/advanced/input-overview.md)
