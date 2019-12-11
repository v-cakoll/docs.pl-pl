---
title: 'Porady: włączanie widoku Tile w formancie ListView formularzy systemu Windows'
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
ms.openlocfilehash: 489b9a9d0341391c756175acb19d962d642eb7b2
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960452"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a>Porady: włączanie widoku Tile w formancie ListView formularzy systemu Windows
Za pomocą funkcji Widok kafelka kontrolki <xref:System.Windows.Forms.ListView> można zapewnić balans wizualizacji między informacjami graficznymi i tekstowymi. Informacje tekstowe wyświetlane dla elementu w widoku kafelków są takie same, jak informacje o kolumnie zdefiniowane dla widoku szczegółów. Widok kafelków działa w połączeniu z funkcjami grupowania lub wstawiania znaczników w kontrolce <xref:System.Windows.Forms.ListView>.  
  
 Widok kafelka używa ikony pikseli 32 x 32 i kilku wierszy tekstu, jak pokazano na poniższych ilustracjach.  
  
 ![Widok kafelka w kontrolce ListView](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Wyświetlanie ikon i tekstu kafelków")  
 
 Aby włączyć widok kafelków, ustaw właściwość <xref:System.Windows.Forms.ListView.View%2A> na <xref:System.Windows.Forms.View.Tile>. Można dostosować rozmiar kafelków, ustawiając właściwość <xref:System.Windows.Forms.ListView.TileSize%2A> i liczbę wierszy tekstu wyświetlanych na kafelku przez dostosowanie kolekcji <xref:System.Windows.Forms.ListView.Columns%2A>.  
  
### <a name="to-set-tile-view-programmatically"></a>Aby programowo ustawić widok kafelków  
  
1. Użyj <xref:System.Windows.Forms.View> Wyliczenie <xref:System.Windows.Forms.ListView> formantu.  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod ilustruje widok kafelków z kafelkami zmodyfikowanymi, aby pokazać trzy wiersze tekstu. Rozmiar kafelka został dostosowany, aby zapobiec zawijaniu wierszy.  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system i system. Windows. Forms.  
  
- Plik ikony o nazwie Book. ico w tym samym katalogu, w którym znajduje się plik wykonywalny.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [ListView, kontrolka](listview-control-windows-forms.md)
- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
