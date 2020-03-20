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
ms.openlocfilehash: 2ff0f134ea3174f7f034d47446aab782e2141916
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186984"
---
# <a name="scrollviewer-overview"></a>ScrollViewer — Przegląd
Zawartość w interfejsie użytkownika jest często większa niż obszar wyświetlania ekranu komputera. Formant <xref:System.Windows.Controls.ScrollViewer> zapewnia wygodny sposób, aby umożliwić [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] przewijanie zawartości w aplikacjach. W tym temacie <xref:System.Windows.Controls.ScrollViewer> przedstawiono element i zawiera kilka przykładów użycia.  
  
<a name="what_is_a_scrollviewer_element"></a>
## <a name="the-scrollviewer-control"></a>Kontrolka ScrollViewer  
 Istnieją dwa wstępnie zdefiniowane elementy, które [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umożliwiają <xref:System.Windows.Controls.Primitives.ScrollBar> <xref:System.Windows.Controls.ScrollViewer>przewijanie w aplikacjach: i . Formant <xref:System.Windows.Controls.ScrollViewer> hermetyzuje elementy <xref:System.Windows.Controls.Primitives.ScrollBar> poziome i pionowe <xref:System.Windows.Controls.Panel> oraz kontener zawartości (na przykład element) w celu wyświetlenia innych widocznych elementów w przewijanym obszarze. Należy utworzyć obiekt niestandardowy, aby <xref:System.Windows.Controls.Primitives.ScrollBar> użyć elementu do przewijania zawartości. Jednak można użyć <xref:System.Windows.Controls.ScrollViewer> elementu przez siebie, ponieważ jest to formant <xref:System.Windows.Controls.Primitives.ScrollBar> złożony, który hermetyzuje funkcjonalność.  
  
 Formant <xref:System.Windows.Controls.ScrollViewer> reaguje na polecenia myszy i klawiatury i definiuje wiele metod, za pomocą których można przewijać zawartość według wstępnie określonych przyrostów. Za pomocą <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> zdarzenia można wykryć <xref:System.Windows.Controls.ScrollViewer> zmianę stanu.  
  
 A <xref:System.Windows.Controls.ScrollViewer> może mieć tylko jeden <xref:System.Windows.Controls.Panel> element podrzędny, <xref:System.Windows.Controls.Panel.Children%2A> zazwyczaj element, który może obsługiwać kolekcję elementów. Właściwość <xref:System.Windows.Controls.ContentPresenter.Content%2A> określa jedyne dziecko <xref:System.Windows.Controls.ScrollViewer>.  
  
<a name="scrollviewer_physical_vs_logical"></a>
## <a name="physical-vs-logical-scrolling"></a>Przewijanie fizyczne i logiczne  
 Fizyczne przewijanie jest używane do przewijania zawartości przez wstępnie określony przyrost fizyczny, zazwyczaj przez wartość zadeklarowaną w pikselach. Logiczne przewijanie służy do przewijania do następnego elementu w drzewie logicznym. Przewijanie fizyczne jest domyślnym zachowaniem przewijania dla większości <xref:System.Windows.Controls.Panel> elementów. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsługuje oba typy przewijania.  
  
#### <a name="the-iscrollinfo-interface"></a>Interfejs IScrollInfo  
 Interfejs <xref:System.Windows.Controls.Primitives.IScrollInfo> reprezentuje główny obszar przewijania <xref:System.Windows.Controls.ScrollViewer> w formancie lub pochodnym. Interfejs definiuje właściwości przewijania i metody, które <xref:System.Windows.Controls.Panel> mogą być implementowane przez elementy, które wymagają przewijania przez jednostkę logiczną, a nie przez przyrost fizyczny. Rzutowanie wystąpienia <xref:System.Windows.Controls.Primitives.IScrollInfo> do <xref:System.Windows.Controls.Panel> pochodnych, a następnie przy użyciu jego metody przewijania zapewnia przydatny sposób przewijania do następnej jednostki logicznej w kolekcji podrzędnej, a nie przez przyrost pikseli. Domyślnie formant <xref:System.Windows.Controls.ScrollViewer> obsługuje przewijanie według jednostek fizycznych.  
  
 <xref:System.Windows.Controls.StackPanel>i <xref:System.Windows.Controls.VirtualizingStackPanel> zarówno <xref:System.Windows.Controls.Primitives.IScrollInfo> implementować, jak i natywnie obsługiwać logiczne przewijanie. W przypadku formantów układu, które natywnie obsługują logiczne <xref:System.Windows.Controls.Panel> przewijanie, nadal można uzyskać fizyczne przewijanie, zawijając element hosta w a <xref:System.Windows.Controls.ScrollViewer> i ustawiając <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> właściwość na `false`.  
  
 Poniższy przykład kodu pokazuje, jak <xref:System.Windows.Controls.Primitives.IScrollInfo> rzutować <xref:System.Windows.Controls.StackPanel> wystąpienie do i<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>używać metody przewijania zawartości ( i ) zdefiniowane przez interfejs.  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>
## <a name="defining-and-using-a-scrollviewer-element"></a>Definiowanie i używanie elementu ScrollViewer  
 Poniższy przykład <xref:System.Windows.Controls.ScrollViewer> tworzy w oknie, który zawiera tekst i prostokąt. <xref:System.Windows.Controls.Primitives.ScrollBar>elementy pojawiają się tylko wtedy, gdy są konieczne. Po zmienić rozmiar okna, <xref:System.Windows.Controls.Primitives.ScrollBar> elementy pojawiają się i znikają, <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> ze względu na zaktualizowane wartości i właściwości.  
  
 [!code-cpp[ScrollViewer#1](~/samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](~/samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>
## <a name="styling-a-scrollviewer"></a>Stylizowanie widoku przewijania  
 Podobnie jak wszystkie formanty <xref:System.Windows.Controls.ScrollViewer> w programie Windows Presentation Foundation, można stylizować w celu zmiany domyślnego zachowania renderowania formantu. Aby uzyskać dodatkowe informacje na temat stylizacji sterowania, zobacz [Stylowanie i tworzenie szablonów](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>
## <a name="paginating-documents"></a>Dokumenty na strony  
 W przypadku zawartości dokumentu alternatywą dla przewijania jest wybranie kontenera dokumentu obsługującego podział na strony. <xref:System.Windows.Documents.FlowDocument>jest przeznaczony dla dokumentów, które są przeznaczone do <xref:System.Windows.Controls.FlowDocumentPageViewer>hostowania w formancie wyświetlania, takich jak , który obsługuje podział na strony na wielu stronach, zapobiegając konieczności przewijania. <xref:System.Windows.Controls.DocumentViewer>zapewnia rozwiązanie do <xref:System.Windows.Documents.FixedDocument> przeglądania zawartości, która używa tradycyjnego przewijania do wyświetlania zawartości poza obszarem obszaru wyświetlania.  
  
 Aby uzyskać dodatkowe informacje dotyczące formatów dokumentów i opcji prezentacji, zobacz [Dokumenty w WPF](../advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.ScrollBar>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- [Jak: Tworzenie podglądu przewijania](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752352(v=vs.90))
- [Dokumenty w WPF](../advanced/documents-in-wpf.md)
- [ScrollBar — style i szablony](scrollbar-styles-and-templates.md)
- [Kontrolki](../advanced/optimizing-performance-controls.md)
