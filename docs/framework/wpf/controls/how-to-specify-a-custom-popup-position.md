---
title: Jak określić niestandardowe położenie okna podręcznego
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: b48dedc044b418062642af5c5bb40afab78a3c97
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635750"
---
# <a name="how-to-specify-a-custom-popup-position"></a>Jak określić niestandardowe położenie okna podręcznego
W tym przykładzie pokazano, jak <xref:System.Windows.Controls.Primitives.Popup> określić <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> pozycję niestandardową formantu, gdy właściwość jest ustawiona na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.  
  
## <a name="example"></a>Przykład  
 Gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwość jest <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>ustawiona na <xref:System.Windows.Controls.Primitives.Popup> , <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> wywołuje zdefiniowane wystąpienie pełnomocnika. Ten pełnomocnik zwraca zestaw możliwych punktów, które są względem lewego górnego rogu obszaru <xref:System.Windows.Controls.Primitives.Popup>docelowego i lewego górnego rogu . Umieszczenie <xref:System.Windows.Controls.Primitives.Popup> występuje w punkcie, który zapewnia najlepszą widoczność.  
  
 W poniższym przykładzie pokazano, <xref:System.Windows.Controls.Primitives.Popup> jak zdefiniować położenie a, ustawiając <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwość na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Pokazuje również, jak utworzyć <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> i przypisać pełnomocnika <xref:System.Windows.Controls.Primitives.Popup>w celu umieszczenia pliku .  Pełnomocnik wywołania zwrotnego zwraca dwa <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> obiekty.  Jeśli <xref:System.Windows.Controls.Primitives.Popup> jest ukryty przez krawędź ekranu na <xref:System.Windows.Controls.Primitives.Popup> pierwszej pozycji, jest umieszczany na drugiej pozycji.  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 Aby uzyskać pełną próbkę, zobacz [Przykładu umieszczania wyskakujących okienków](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.Primitives.Popup>
- [Omówienie wyskakujących okienka](popup-overview.md)
- [Artykuły do artykułów](popup-how-to-topics.md)
