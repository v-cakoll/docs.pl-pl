---
title: "ScrollViewer — Przegląd"
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
- cpp
helpviewer_keywords:
- controls [WPF], ScrollViewer
- ScrollViewer control [WPF], about ScrollViewer control
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d060e0b511f17a68edb013ae7241e1accbc7dcf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="scrollviewer-overview"></a>ScrollViewer — Przegląd
Zawartość w interfejsie użytkownika często jest większy niż obszar wyświetlania ekranu komputera. <xref:System.Windows.Controls.ScrollViewer> Kontrola zapewnia wygodny sposób, aby włączyć przewijanie zawartości w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji. W tym temacie przedstawiono <xref:System.Windows.Controls.ScrollViewer> element i zawiera kilka przykładów użycia.  
  
<a name="what_is_a_scrollviewer_element"></a>   
## <a name="the-scrollviewer-control"></a>Kontrolki ScrollViewer  
 Istnieją dwa wstępnie zdefiniowane elementy, które umożliwiają przewijanie w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji: <xref:System.Windows.Controls.Primitives.ScrollBar> i <xref:System.Windows.Controls.ScrollViewer>. <xref:System.Windows.Controls.ScrollViewer> Kontroli hermetyzuje poziome i pionowe <xref:System.Windows.Controls.Primitives.ScrollBar> elementów i zawartości kontenera (takich jak <xref:System.Windows.Controls.Panel> element), aby wyświetlić inne widoczne elementy w przewijany obszar. Aby można było używać należy utworzyć niestandardowego obiektu <xref:System.Windows.Controls.Primitives.ScrollBar> element przewijania zawartości. Można jednak użyć <xref:System.Windows.Controls.ScrollViewer> element samodzielnie, ponieważ jest złożone kontrolować, który hermetyzuje <xref:System.Windows.Controls.Primitives.ScrollBar> funkcji.  
  
 <xref:System.Windows.Controls.ScrollViewer> Kontroli reaguje na polecenia zarówno myszy i klawiatury i definiuje wiele metod umożliwiające przewijanie zawartości w ustalonej krokami. Można użyć <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> zdarzenie, aby wykryć zmiany <xref:System.Windows.Controls.ScrollViewer> stanu.  
  
 A <xref:System.Windows.Controls.ScrollViewer> może mieć tylko jeden element podrzędny, zwykle <xref:System.Windows.Controls.Panel> element, który może obsługiwać <xref:System.Windows.Controls.Panel.Children%2A> kolekcję elementów. <xref:System.Windows.Controls.ContentPresenter.Content%2A> Właściwość definiuje wyłącznie podrzędnym <xref:System.Windows.Controls.ScrollViewer>.  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## <a name="physical-vs-logical-scrolling"></a>Vs fizycznych. Przewijanie logiczne  
 Przewijanie fizycznych służy przewijanie zawartości w ustalonej przyrost fizycznych zazwyczaj przez wartość, która jest zadeklarowana w pikselach. Przewijanie logiczna jest używana do przewiń do następnego elementu w drzewie logicznym. Przewijanie fizycznych jest to domyślne zachowanie przewijania dla większości <xref:System.Windows.Controls.Panel> elementów. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsługuje oba rodzaje przewijania.  
  
#### <a name="the-iscrollinfo-interface"></a>Interfejs IScrollInfo  
 <xref:System.Windows.Controls.Primitives.IScrollInfo> Interfejsu reprezentuje głównym regionie przewijania w <xref:System.Windows.Controls.ScrollViewer> lub pochodnego formantu. Interfejs definiuje przewijania właściwości i metody, które może być zaimplementowany przez <xref:System.Windows.Controls.Panel> elementy, które wymagają przewijanie jednostki logicznej, a nie fizycznych przyrostu. Rzutowanie wystąpienia <xref:System.Windows.Controls.Primitives.IScrollInfo> do pochodnego <xref:System.Windows.Controls.Panel> i za pomocą jej metod przewijania zapewnia wygodny sposób na przewiń do następnego jednostki logicznej w kolekcji podrzędnych, a nie przez przyrostu pikseli. Domyślnie <xref:System.Windows.Controls.ScrollViewer> sterowanie obsługuje przewijanie przez fizyczne jednostki.  
  
 <xref:System.Windows.Controls.StackPanel>i <xref:System.Windows.Controls.VirtualizingStackPanel> zarówno zaimplementować <xref:System.Windows.Controls.Primitives.IScrollInfo> i natywnie obsługuje logicznego przewijania. Układ formantów tego natywnie Obsługa logicznej przewijania, można nadal osiągnąć fizycznych przewijanie zawijania hosta <xref:System.Windows.Controls.Panel> element <xref:System.Windows.Controls.ScrollViewer> i ustawienie <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> właściwości `false`.  
  
 Poniższy przykład kodu pokazuje, jak można rzutować wystąpienia <xref:System.Windows.Controls.Primitives.IScrollInfo> do <xref:System.Windows.Controls.StackPanel> i używać zawartości metody przewijania (<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> i <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>) zdefiniowany przez interfejs.  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## <a name="defining-and-using-a-scrollviewer-element"></a>Definiowanie i przy użyciu elementu ScrollViewer  
 Poniższy przykład tworzy <xref:System.Windows.Controls.ScrollViewer> w oknie zawierający tekst i prostokąta. <xref:System.Windows.Controls.Primitives.ScrollBar>elementy są wyświetlane tylko wtedy, gdy są wymagane. Podczas zmiany rozmiaru okna, <xref:System.Windows.Controls.Primitives.ScrollBar> elementy pojawiają się i znikają, z powodu zaktualizowanej wartości <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> i <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> właściwości.  
  
 [!code-cpp[ScrollViewer#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## <a name="styling-a-scrollviewer"></a>Ustawianie stylów ScrollViewer  
 Wszystkie formanty w systemie Windows Presentation Foundation, takich jak <xref:System.Windows.Controls.ScrollViewer> być stylem, aby zmienić domyślne zachowanie renderowania formantu. Dodatkowe informacje na temat stylów formantu, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## <a name="paginating-documents"></a>Dzielenie na strony dokumentów  
 Zawartość dokumentu zamiast przewijanie jest Wybierz kontener dokumentu, która obsługuje podział na strony. <xref:System.Windows.Documents.FlowDocument>dla dokumentów, które mają być hostowana w formancie wyświetlania, takich jak <xref:System.Windows.Controls.FlowDocumentPageViewer>, która obsługuje podział na strony zawartość na wielu stronach uniemożliwia potrzebę przewijanie. <xref:System.Windows.Controls.DocumentViewer>zapewnia rozwiązanie w celu wyświetlenia <xref:System.Windows.Documents.FixedDocument> zawartość, która korzysta z tradycyjnego przewijanie do wyświetlenia zawartości spoza obszaru obszaru wyświetlania.  
  
 Aby uzyskać dodatkowe informacje dotyczące formatowania dokumentu i opcje prezentacji, zobacz [dokumentów na platformie WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.ScrollBar>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 [Tworzenie przeglądarki przewijania](http://msdn.microsoft.com/en-us/c8e46af7-b417-441b-aa30-791cbdbd43ef)  
 [Dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [ScrollBar — style i szablony](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)  
 [Kontrolki](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
