---
title: Włącz widok kafelków w kontrolce widoku listview
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tile view feature
- tiling
- Windows Forms, controls
- ListView control [Windows Forms], tile view
ms.assetid: c20e67a3-2d94-413d-9fcf-ecbd0fe251da
ms.openlocfilehash: 1478ba5e4f175cd7d9ec7ab5c3c4bc9050ce02fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182150"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a>Porady: włączanie widoku Tile w formancie ListView formularzy systemu Windows
Dzięki funkcji widoku kafelków <xref:System.Windows.Forms.ListView> formantu można zapewnić wizualną równowagę między informacjami graficznymi i tekstowymi. Informacje tekstowe wyświetlane dla elementu w widoku kafelków są takie same jak informacje o kolumnach zdefiniowane dla widoku szczegółów. Widok kafelków działa w połączeniu z elementami grupowania <xref:System.Windows.Forms.ListView> lub wstawiania w formancie.  
  
 Widok kafelka używa ikony 32 x 32 pikseli i kilku wierszy tekstu, jak pokazano na poniższych obrazach.  
  
 ![Widok kafli w formancie widoku listy](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Ikony widoku kafelków i tekst")  

 Aby włączyć widok kafelka, <xref:System.Windows.Forms.View.Tile>ustaw właściwość na <xref:System.Windows.Forms.ListView.View%2A> . Rozmiar kafelków można dostosować, ustawiając <xref:System.Windows.Forms.ListView.TileSize%2A> właściwość oraz liczbę linii tekstowych wyświetlanych na <xref:System.Windows.Forms.ListView.Columns%2A> kafelku, dostosowując kolekcję.  
  
### <a name="to-set-tile-view-programmatically"></a>Aby programowo ustawić widok kafelków  
  
1. Użyj <xref:System.Windows.Forms.View> wyliczenia <xref:System.Windows.Forms.ListView> formantu.  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pełnego kodu przedstawiono widok kafelków z zmodyfikowanymi kafelkami, aby wyświetlić trzy wiersze tekstu. Rozmiar kafelka został dostosowany, aby zapobiec zawijania linii.  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów System i System.Windows.Forms.  
  
- Plik ikony o nazwie book.ico w tym samym katalogu co plik wykonywalny.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [ListView, kontrolka](listview-control-windows-forms.md)
- [ListView — Informacje o formancie](listview-control-overview-windows-forms.md)
