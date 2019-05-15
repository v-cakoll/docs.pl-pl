---
title: 'Instrukcje: włączanie widoku Tile w kontrolce ListView formularzy systemu Windows'
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
ms.openlocfilehash: bd152d19567806cf1cc7b1b38d9a3c0e47d2a960
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591685"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a>Instrukcje: włączanie widoku Tile w kontrolce ListView formularzy systemu Windows
Korzystając z funkcji widoku kafelków <xref:System.Windows.Forms.ListView> kontrolki, możesz podać visual równowagi między informacje graficzne i tekstowe. Tekstowe informacje wyświetlane dla elementu w widoku kafelków jest taka sama jak informacji o kolumnie zdefiniowane dla widoku szczegółów. Widoku kafelków działa w połączeniu z grupowania lub wstawiania funkcji znaku w <xref:System.Windows.Forms.ListView> kontroli.  
  
 Wyświetlanie kafelka używa ikonę 32 x 32 piksele i kilka wierszy tekstu, jak pokazano na poniższych ilustracjach.  
  
 ![Widok w kontrolce ListView kafelków](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Kafelek widoku ikon i tekstu")  
 
 Aby włączyć widoku kafelków, ustaw <xref:System.Windows.Forms.ListView.View%2A> właściwość <xref:System.Windows.Forms.View.Tile>. Można dostosować rozmiar kafelków, ustawiając <xref:System.Windows.Forms.ListView.TileSize%2A> właściwość i liczbę wierszy tekstu, wyświetlane na kafelku, dostosowując <xref:System.Windows.Forms.ListView.Columns%2A> kolekcji.  
  
> [!NOTE]
>  Widoku kafelków jest dostępna tylko na [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] gdy Twoja aplikacja wywołuje <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody. W starszych systemach operacyjnych, dowolnego kodu, powiązany z widoku kafelków nie obowiązuje oraz <xref:System.Windows.Forms.ListView> kontrolka wyświetla się w Widok dużych ikon. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.  
  
### <a name="to-set-tile-view-programmatically"></a>Aby programowo ustawić widoku kafelków  
  
1. Użyj <xref:System.Windows.Forms.View> wyliczenie <xref:System.Windows.Forms.ListView> kontroli.  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompletny kod pokazuje widoku kafelków z kafelkami zmodyfikowany do wyświetlania trzy wiersze tekstu. Rozmiar fragmentu został dostosowany tak, aby zapobiec zawijania wierszy.  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.  
  
- Plik ikony o nazwie book.ico w tym samym katalogu co plik wykonywalny.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [Kontrolka ListView](listview-control-windows-forms.md)
- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
