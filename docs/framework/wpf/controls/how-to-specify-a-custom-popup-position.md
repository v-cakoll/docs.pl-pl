---
title: "Jak określić niestandardowe położenie okna podręcznego"
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
helpviewer_keywords: Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ab9baca1103adf8de96204bdb1b3353a5456b94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-a-custom-popup-position"></a>Jak określić niestandardowe położenie okna podręcznego
W tym przykładzie przedstawiono sposób określania pozycjonowanie niestandardowe dla <xref:System.Windows.Controls.Primitives.Popup> decyduje o <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwość jest ustawiona na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.  
  
## <a name="example"></a>Przykład  
 Gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwość jest ustawiona na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, <xref:System.Windows.Controls.Primitives.Popup> wywołuje zdefiniowane wystąpienia <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegowanie. Ten delegat zwraca zestaw możliwych punktów, które są względem lewym górnym rogu obszar docelowy i lewym górnym rogu aplikacji <xref:System.Windows.Controls.Primitives.Popup>. <xref:System.Windows.Controls.Primitives.Popup> Umieszczania występuje w momencie, który zapewnia widoczność najlepsze.  
  
 Poniższy przykład przedstawia sposób definiowania pozycja <xref:System.Windows.Controls.Primitives.Popup> przez ustawienie <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwości <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Przedstawiono również sposób utworzyć i przypisać <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegata w celu umieść <xref:System.Windows.Controls.Primitives.Popup>.  Zwraca delegata wywołania zwrotnego, dwa <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> obiektów.  Jeśli <xref:System.Windows.Controls.Primitives.Popup> jest ukryty przez krawędzi ekranu, na pierwszym miejscu <xref:System.Windows.Controls.Primitives.Popup> znajduje się w drugim pozycji.  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 Pełny przykład, zobacz [podręcznego umieszczania próbki](http://go.microsoft.com/fwlink/?LinkID=160032).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [Omówienie menu podręczne](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [Tematy porad](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
