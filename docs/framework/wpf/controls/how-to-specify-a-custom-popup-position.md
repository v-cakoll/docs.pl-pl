---
title: Jak określić niestandardowe położenie okna podręcznego
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: ea8d73c51dd018608b95104f00bf341ff434225c
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344949"
---
# <a name="how-to-specify-a-custom-popup-position"></a>Jak określić niestandardowe położenie okna podręcznego
W tym przykładzie pokazano, jak <xref:System.Windows.Controls.Primitives.Popup> określić <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> pozycję niestandardową formantu, gdy właściwość jest ustawiona na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.  
  
## <a name="example"></a>Przykład  
 Gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwość jest <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>ustawiona na <xref:System.Windows.Controls.Primitives.Popup> , <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> wywołuje zdefiniowane wystąpienie pełnomocnika. Ten delegat zwraca zestaw możliwych punktów, które są względem lewego górnego rogu <xref:System.Windows.Controls.Primitives.Popup>obszaru docelowego i lewego górnego rogu . Umieszczenie <xref:System.Windows.Controls.Primitives.Popup> występuje w punkcie, który zapewnia najlepszą widoczność.  
  
 W poniższym przykładzie pokazano, <xref:System.Windows.Controls.Primitives.Popup> jak zdefiniować położenie a, ustawiając <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwość na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Pokazuje również, jak utworzyć <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> i przypisać pełnomocnika <xref:System.Windows.Controls.Primitives.Popup>w celu umieszczenia pliku .  Pełnomocnik wywołania zwrotnego zwraca dwa <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> obiekty.  Jeśli <xref:System.Windows.Controls.Primitives.Popup> jest ukryty przez krawędź ekranu na <xref:System.Windows.Controls.Primitives.Popup> pierwszej pozycji, jest umieszczany na drugiej pozycji.  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 Aby uzyskać pełną próbkę, zobacz [Przykładu umieszczania wyskakujących okienków](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.Primitives.Popup>
- [Okno podręczne — omówienie](popup-overview.md)
- [— Tematy porad](popup-how-to-topics.md)
