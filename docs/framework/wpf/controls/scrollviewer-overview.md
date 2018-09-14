---
title: ScrollViewer — Przegląd
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], ScrollViewer
- ScrollViewer control [WPF], about ScrollViewer control
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
ms.openlocfilehash: 4c9a2e8cf64f18f3e8614912759a4a6eb01d4823
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45593807"
---
# <a name="scrollviewer-overview"></a>ScrollViewer — Przegląd
Zawartość w interfejsie użytkownika często jest większy niż obszaru wyświetlania ekranu komputera. <xref:System.Windows.Controls.ScrollViewer> Kontrola zapewnia wygodny sposób, aby włączyć przewijanie zawartości w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji. W tym temacie przedstawiono <xref:System.Windows.Controls.ScrollViewer> elementu i udostępnia kilka przykładów użycia.  
  
<a name="what_is_a_scrollviewer_element"></a>   
## <a name="the-scrollviewer-control"></a>Scrollviewer — formant  
 Istnieją dwa wstępnie zdefiniowane elementy, które umożliwiają przewijanie w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji: <xref:System.Windows.Controls.Primitives.ScrollBar> i <xref:System.Windows.Controls.ScrollViewer>. <xref:System.Windows.Controls.ScrollViewer> Kontroli hermetyzuje poziomo i pionowo <xref:System.Windows.Controls.Primitives.ScrollBar> elementów i zawartość kontenerów (takie jak <xref:System.Windows.Controls.Panel> elementu) aby wyświetlić inne widoczne elementy w przewijanym obszarze. Należy utworzyć niestandardowy obiekt, aby można było używać <xref:System.Windows.Controls.Primitives.ScrollBar> element przewijania zawartości. Można jednak użyć <xref:System.Windows.Controls.ScrollViewer> elementu samodzielnie, ponieważ jest on złożonego kontrolkę, która hermetyzuje <xref:System.Windows.Controls.Primitives.ScrollBar> funkcji.  
  
 <xref:System.Windows.Controls.ScrollViewer> Kontroli reaguje na polecenia klawiatury i myszy, a następnie definiuje wiele metod czekających za pomocą którego można przewijać zawartość przy wstępnie zdefiniowanych przyrostów. Możesz użyć <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> zdarzenia w celu wykrycia zmian w <xref:System.Windows.Controls.ScrollViewer> stanu.  
  
 A <xref:System.Windows.Controls.ScrollViewer> może mieć tylko jeden element podrzędny, zwykle <xref:System.Windows.Controls.Panel> element, który może obsługiwać <xref:System.Windows.Controls.Panel.Children%2A> kolekcję elementów. <xref:System.Windows.Controls.ContentPresenter.Content%2A> Właściwość definiuje jedyny podrzędnym <xref:System.Windows.Controls.ScrollViewer>.  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## <a name="physical-vs-logical-scrolling"></a>Fizyczne programu vs. Przewijanie logiczne  
 Przewijanie fizycznych służy do przewijanie zawartości z wstępnie zdefiniowanych przyrostem fizycznych, zwykle przez wartość, która jest zadeklarowana w pikselach. Przewijanie logicznych jest używany do przewiń do następnego elementu w drzewie logicznym. Przewijanie fizycznego jest domyślne zachowanie przewijania dla większości <xref:System.Windows.Controls.Panel> elementów. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje oba rodzaje przewijania.  
  
#### <a name="the-iscrollinfo-interface"></a>Interfejsu IScrollInfo  
 <xref:System.Windows.Controls.Primitives.IScrollInfo> Interfejs reprezentuje główny region przewijania w ramach <xref:System.Windows.Controls.ScrollViewer> lub pochodnego kontroli. Interfejs definiuje przewijania właściwości i metod, które może być implementowany przez <xref:System.Windows.Controls.Panel> elementy, które wymagają przewijania jednostki logicznej, a nie fizycznej przyrostu. Rzutowania wystąpienia <xref:System.Windows.Controls.Primitives.IScrollInfo> do pochodnej <xref:System.Windows.Controls.Panel> i następnie przy użyciu jego metod przewijania zapewnia wygodny sposób, aby przewinąć do następnego jednostki logicznej w kolekcji podrzędnej, a nie z przyrostem pikseli. Domyślnie <xref:System.Windows.Controls.ScrollViewer> kontrolka obsługuje przewijania jednostek fizycznych.  
  
 <xref:System.Windows.Controls.StackPanel> i <xref:System.Windows.Controls.VirtualizingStackPanel> zarówno zaimplementować <xref:System.Windows.Controls.Primitives.IScrollInfo> i przewijanie logicznego w sposób natywny obsługują. Układ formantów tego natywnej obsługi logiczne przewijanie, można nadal osiągnąć fizycznych przewijanie opakowując hosta <xref:System.Windows.Controls.Panel> element <xref:System.Windows.Controls.ScrollViewer> i ustawienie <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> właściwość `false`.  
  
 Poniższy przykład kodu demonstruje sposób rzutowania wystąpienia <xref:System.Windows.Controls.Primitives.IScrollInfo> do <xref:System.Windows.Controls.StackPanel> i używania metod przewijania zawartości (<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> i <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>) zdefiniowany przez interfejs.  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## <a name="defining-and-using-a-scrollviewer-element"></a>Definiowanie i korzystanie z elementu ScrollViewer  
 Poniższy przykład tworzy <xref:System.Windows.Controls.ScrollViewer> w oknie, który zawiera część tekstu i prostokąt. <xref:System.Windows.Controls.Primitives.ScrollBar> elementy są wyświetlane tylko wtedy, gdy są one niezbędne. Podczas zmiany rozmiaru okna, <xref:System.Windows.Controls.Primitives.ScrollBar> elementy pojawiają się i znikają z powodu zaktualizowanymi wartościami z <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> i <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> właściwości.  
  
 [!code-cpp[ScrollViewer#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## <a name="styling-a-scrollviewer"></a>Scrollviewer — style  
 Wszystkie formanty w oprogramowaniu Windows Presentation Foundation, takich jak <xref:System.Windows.Controls.ScrollViewer> być różne, aby zmienić domyślne zachowanie renderowania formantu. Aby uzyskać dodatkowe informacje na temat ustawiania stylu formantu, zobacz [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## <a name="paginating-documents"></a>Podział na strony w dokumentach  
 Alternatywa przewijanie zawartości dokumentu jest Wybierz kontener dokumentów, która obsługuje podział na strony. <xref:System.Windows.Documents.FlowDocument> jest dokumentów, które mają zostać umieszczony w elemencie wyświetlania kontrolki, takie jak <xref:System.Windows.Controls.FlowDocumentPageViewer>, obsługujący zawartość dzielonych na wielu stronach, zapobiegając potrzebę przewijania. <xref:System.Windows.Controls.DocumentViewer> zapewnia rozwiązanie do wyświetlania <xref:System.Windows.Documents.FixedDocument> zawartość, która korzysta z tradycyjnych przewijanie do wyświetlenia zawartości spoza obszaru obszaru wyświetlania.  
  
 Aby uzyskać dodatkowe informacje na temat formatów dokumentów i prezentacji opcji, zobacz [dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.ScrollBar>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 [Tworzenie podglądu z przewijaniem](https://msdn.microsoft.com/library/c8e46af7-b417-441b-aa30-791cbdbd43ef)  
 [Dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [ScrollBar — style i szablony](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)  
 [Kontrolki](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
