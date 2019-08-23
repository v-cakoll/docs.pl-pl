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
ms.openlocfilehash: 44d34ddb00005a0fb86b2d06c4c14e2a5b949819
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966677"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a>Instrukcje: włączanie widoku Tile w kontrolce ListView formularzy systemu Windows
Za pomocą funkcji <xref:System.Windows.Forms.ListView> widok kafelków formantu można zapewnić wizualną równowagę między informacjami graficznymi i tekstowymi. Informacje tekstowe wyświetlane dla elementu w widoku kafelków są takie same, jak informacje o kolumnie zdefiniowane dla widoku szczegółów. Widok kafelków działa w połączeniu z funkcjami grupowania lub wstawiania znaczników w <xref:System.Windows.Forms.ListView> formancie.  
  
 Widok kafelka używa ikony pikseli 32 x 32 i kilku wierszy tekstu, jak pokazano na poniższych ilustracjach.  
  
 ![Widok kafelka w kontrolce ListView](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Wyświetlanie ikon i tekstu kafelków")  
 
 Aby włączyć widok kafelków, ustaw <xref:System.Windows.Forms.ListView.View%2A> właściwość na <xref:System.Windows.Forms.View.Tile>. Można dostosować rozmiar kafelków, ustawiając <xref:System.Windows.Forms.ListView.TileSize%2A> Właściwość oraz liczbę linii tekstu wyświetlanych na kafelku przez <xref:System.Windows.Forms.ListView.Columns%2A> dostosowanie kolekcji.  
  
> [!NOTE]
> Widok kafelków jest dostępny tylko [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] wtedy, gdy aplikacja <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> wywołuje metodę. We wcześniejszych systemach operacyjnych każdy kod związany z widokiem kafelka nie ma żadnego efektu, a <xref:System.Windows.Forms.ListView> kontrolka zostanie wyświetlona w widoku dużych ikon. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.  
  
### <a name="to-set-tile-view-programmatically"></a>Aby programowo ustawić widok kafelków  
  
1. <xref:System.Windows.Forms.View> Użyj wyliczenia<xref:System.Windows.Forms.ListView> formantu.  
  
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
- [Kontrolka ListView](listview-control-windows-forms.md)
- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
