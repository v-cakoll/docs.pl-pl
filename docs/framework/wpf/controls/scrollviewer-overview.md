---
title: ScrollViewer — Przegląd
description: Zapoznaj się z kontrolką ScrollViewer, która umożliwia przewijanie zawartości w aplikacjach Windows Presentation Foundation. Zobacz przykłady użycia.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], ScrollViewer
- ScrollViewer control [WPF], about ScrollViewer control
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
ms.openlocfilehash: 1ef680bb004315a2b523814714d5533535d044e5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164638"
---
# <a name="scrollviewer-overview"></a>ScrollViewer — Przegląd
Zawartość w interfejsie użytkownika jest często większa niż obszar wyświetlania ekranu komputera. <xref:System.Windows.Controls.ScrollViewer>Kontrolka zapewnia wygodny sposób włączania przewijania zawartości w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacjach. W tym temacie przedstawiono <xref:System.Windows.Controls.ScrollViewer> element i przedstawiono kilka przykładów użycia.  
  
<a name="what_is_a_scrollviewer_element"></a>
## <a name="the-scrollviewer-control"></a>Kontrolka ScrollViewer  
 Istnieją dwa wstępnie zdefiniowane elementy, które umożliwiają przewijanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji: <xref:System.Windows.Controls.Primitives.ScrollBar> i <xref:System.Windows.Controls.ScrollViewer> . <xref:System.Windows.Controls.ScrollViewer>Formant hermetyzuje elementy poziome i pionowe <xref:System.Windows.Controls.Primitives.ScrollBar> oraz kontener zawartości (na przykład <xref:System.Windows.Controls.Panel> element), aby wyświetlić inne widoczne elementy w przewijanym obszarze. Należy utworzyć obiekt niestandardowy, aby można było użyć elementu do <xref:System.Windows.Controls.Primitives.ScrollBar> przewijania zawartości. Można jednak użyć <xref:System.Windows.Controls.ScrollViewer> samego elementu, ponieważ jest to formant złożony, który hermetyzuje <xref:System.Windows.Controls.Primitives.ScrollBar> funkcjonalność.  
  
 <xref:System.Windows.Controls.ScrollViewer>Kontrolka reaguje na polecenia myszy i klawiatury oraz definiuje wiele metod, za pomocą których można przewijać zawartość według wstępnie określonych przyrostów. Możesz użyć zdarzenia, <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> Aby wykryć zmianę w <xref:System.Windows.Controls.ScrollViewer> stanie.  
  
 <xref:System.Windows.Controls.ScrollViewer>Może mieć tylko jeden element podrzędny, zazwyczaj <xref:System.Windows.Controls.Panel> elementu, który może hostować <xref:System.Windows.Controls.Panel.Children%2A> kolekcję elementów. <xref:System.Windows.Controls.ContentPresenter.Content%2A>Właściwość definiuje wyłączny element podrzędny <xref:System.Windows.Controls.ScrollViewer> .  
  
<a name="scrollviewer_physical_vs_logical"></a>
## <a name="physical-vs-logical-scrolling"></a>Przewijanie fizyczne a logiczne  
 Przewijanie fizyczne służy do przewijania zawartości przez wstępnie określony przyrost fizyczny, zazwyczaj przez wartość zadeklarowaną w pikselach. Przewijanie logiczne służy do przewijania do następnego elementu w drzewie logicznym. Przewijanie fizyczne jest domyślnym zachowaniem przewijania dla większości <xref:System.Windows.Controls.Panel> elementów. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsługuje oba typy przewijania.  
  
#### <a name="the-iscrollinfo-interface"></a>Interfejs IScrollInfo  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>Interfejs reprezentuje główny region przewijania w <xref:System.Windows.Controls.ScrollViewer> formancie pochodnym lub. Interfejs definiuje właściwości i metody przewijania, które mogą być implementowane przez <xref:System.Windows.Controls.Panel> elementy wymagające przewijania według jednostki logicznej, a nie przez przyrost fizyczny. Rzutowanie wystąpienia elementu <xref:System.Windows.Controls.Primitives.IScrollInfo> na pochodną <xref:System.Windows.Controls.Panel> i użycie jego metod przewijania zapewnia przydatny sposób przewijania do następnej jednostki logicznej w kolekcji podrzędnej, a nie przez przyrost pikseli. Domyślnie <xref:System.Windows.Controls.ScrollViewer> kontrolka obsługuje przewijanie według jednostek fizycznych.  
  
 <xref:System.Windows.Controls.StackPanel>i <xref:System.Windows.Controls.VirtualizingStackPanel> zarówno Implementuj <xref:System.Windows.Controls.Primitives.IScrollInfo> , jak i natywnie obsługują przewijanie logiczne. W przypadku kontrolek układu, które natywnie obsługują przewijanie logiczne, można nadal osiągnąć bezpośrednie przewijanie, zawijając <xref:System.Windows.Controls.Panel> element hosta w <xref:System.Windows.Controls.ScrollViewer> i ustawiając <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> Właściwość na `false` .  
  
 Poniższy przykład kodu demonstruje, jak rzutować wystąpienie elementu <xref:System.Windows.Controls.Primitives.IScrollInfo> na <xref:System.Windows.Controls.StackPanel> i użyć metod przewijania zawartości ( <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> i <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> ) zdefiniowanych przez interfejs.  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>
## <a name="defining-and-using-a-scrollviewer-element"></a>Definiowanie i używanie elementu ScrollViewer  
 Poniższy przykład tworzy <xref:System.Windows.Controls.ScrollViewer> w oknie, które zawiera tekst i prostokąt. <xref:System.Windows.Controls.Primitives.ScrollBar>elementy pojawiają się tylko wtedy, gdy są potrzebne. Po zmianie rozmiaru okna <xref:System.Windows.Controls.Primitives.ScrollBar> elementy pojawiają się i znikają z powodu zaktualizowanych wartości <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> właściwości i.  
  
 [!code-cpp[ScrollViewer#1](~/samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](~/samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>
## <a name="styling-a-scrollviewer"></a>Określanie stylu elementu ScrollViewer  
 Podobnie jak w przypadku wszystkich formantów w Windows Presentation Foundation, <xref:System.Windows.Controls.ScrollViewer> można mieć styl w celu zmiany domyślnego zachowania renderowania formantu. Aby uzyskać dodatkowe informacje na temat stylów kontroli, zobacz [Style i tworzenia szablonów](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>
## <a name="paginating-documents"></a>Paginating dokumenty  
 W przypadku zawartości dokumentu alternatywą dla przewijania jest wybranie kontenera dokumentu, który obsługuje podział na strony. <xref:System.Windows.Documents.FlowDocument>Program jest przeznaczony dla dokumentów, które są przeznaczone do hostowania w kontrolce wyświetlania, takich jak <xref:System.Windows.Controls.FlowDocumentPageViewer> , które obsługują zawartość paginating na wielu stronach, co uniemożliwia konieczność przewijania. <xref:System.Windows.Controls.DocumentViewer>zapewnia rozwiązanie do wyświetlania <xref:System.Windows.Documents.FixedDocument> zawartości, która używa tradycyjnego przewijania do wyświetlania zawartości poza obszarem obszaru wyświetlania.  
  
 Aby uzyskać dodatkowe informacje na temat formatów dokumentów i opcji prezentacji, zobacz [dokumenty w WPF](../advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.ScrollBar>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- [Instrukcje: Tworzenie podglądu przewijania](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752352(v=vs.90))
- [Dokumenty w WPF](../advanced/documents-in-wpf.md)
- [ScrollBar — Style i szablony](scrollbar-styles-and-templates.md)
- [Formanty](../advanced/optimizing-performance-controls.md)
