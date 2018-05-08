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
ms.openlocfilehash: e47c61667a12ea9215c13bee873a668d2ad2188b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a>Porady: włączanie widoku Tile w formancie ListView formularzy systemu Windows
Korzystając z funkcji Widok kafelków <xref:System.Windows.Forms.ListView> kontroli, możesz podać visual równowagi między informacji graficznych i tekstowych. Wyświetlane dla elementu w widoku tile informacji tekstowych jest taka sama jak informacji o kolumnie zdefiniowanych w widoku szczegółów. Widoku Tile współdziała z funkcjami znak grupowania lub wstawiania w <xref:System.Windows.Forms.ListView> formantu.  
  
 Widoku tile używa ikona 32 x 32 pikseli i kilka wierszy tekstu, jak pokazano na poniższych ilustracjach.  
  
 ![Widok sąsiadujący w formancie ListView](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")  
Kafelek widoku ikon i tekst  
  
 Aby włączyć widoku kafelków, ustaw <xref:System.Windows.Forms.ListView.View%2A> właściwości <xref:System.Windows.Forms.View.Tile>. Przez ustawienie można dostosować rozmiar Kafelki <xref:System.Windows.Forms.ListView.TileSize%2A> właściwości, a liczba wierszy tekstu wyświetlane na kafelku dostosowując <xref:System.Windows.Forms.ListView.Columns%2A> kolekcji.  
  
> [!NOTE]
>  Jest dostępna tylko w widoku tile [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] podczas wywołania aplikacji <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody. W starszych systemach operacyjnych, dowolny kod związane z widoku tile nie obowiązuje, a <xref:System.Windows.Forms.ListView> kontrolka ma być wyświetlana w widoku dużych ikon. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.  
  
### <a name="to-set-tile-view-programmatically"></a>Aby programowo Ustawianie widoku kafelków  
  
1.  Użyj <xref:System.Windows.Forms.View> wyliczenie <xref:System.Windows.Forms.ListView> formantu.  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kompletny kod pokazuje widoku Tile z Kafelki zmodyfikować, aby wyświetlić trzy wiersze tekstu. Aby zapobiec zawijania wierszy został dostosowany rozmiar kafelka.  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu i System.Windows.Forms.  
  
-   Plik ikony o nazwie book.ico w tym samym katalogu co plik wykonywalny.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.TileSize%2A>  
 [Kontrolka ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Funkcje systemu Windows XP i formantów formularzy systemu Windows](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)
