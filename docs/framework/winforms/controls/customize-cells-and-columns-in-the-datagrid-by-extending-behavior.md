---
title: 'Porady: dostosowywanie komórek i kolumn w formancie DataGridView (Formularze systemu Windows) przez rozszerzanie ich zachowania i wyglądu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
ms.openlocfilehash: c183cb03535832dce9b2c3ed97eb4d68fab19796
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527905"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Porady: dostosowywanie komórek i kolumn w formancie DataGridView (Formularze systemu Windows) przez rozszerzanie ich zachowania i wyglądu
<xref:System.Windows.Forms.DataGridView> Control oferuje wiele sposobów, aby dostosować wygląd i zachowanie za pomocą właściwości, zdarzenia oraz klasy pomocnika. Od czasu do czasu może mieć wymagania dla Twojego komórek, które wykraczają poza co te funkcje umożliwiają. Możesz utworzyć własną niestandardową <xref:System.Windows.Forms.DataGridViewCell> Aby klasa zapewniała rozszerzoną funkcjonalność.  
  
 Utwórz niestandardową <xref:System.Windows.Forms.DataGridViewCell> przy pochodząca od <xref:System.Windows.Forms.DataGridViewCell> klasy bazowej lub jedna z jej klas pochodnych. Mimo że dowolny typ komórki można wyświetlić w dowolnej typ kolumny, zazwyczaj także utworzysz niestandardowego <xref:System.Windows.Forms.DataGridViewColumn> klasy przeznaczone do wyświetlania typu komórki. Kolumna klasy pochodzić od <xref:System.Windows.Forms.DataGridViewColumn> lub jeden z jego typów pochodnych.  
  
 W poniższym przykładzie kodu utworzy klasę komórki niestandardowej o nazwie `DataGridViewRolloverCell` wykrywa, gdy wskaźnik myszy wprowadza teren komórki. Gdy wskaźnik myszy znajduje się w granicach komórki, jest wstawiany krawędzi prostokąta. Ten nowy typ pochodzi z <xref:System.Windows.Forms.DataGridViewTextBoxCell> i zachowuje się pod innymi względami jak jej klasa bazowa. Klasa kolumny pomocnika jest nazywana `DataGridViewRolloverColumn`.  
  
 Aby korzystać z tych klas, tworzenia, zawierający formularz <xref:System.Windows.Forms.DataGridView> i Dodaj co najmniej jeden `DataGridViewRolloverColumn` obiekty do <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekcji i wypełniona kontrolka wiersze zawierające wartości.  
  
> [!NOTE]
>  W tym przykładzie nie będą działać poprawnie, jeśli dodasz pustych wierszy. Puste wiersze są tworzone, na przykład podczas dodawania wierszy do kontrolki, ustawiając <xref:System.Windows.Forms.DataGridView.RowCount%2A> właściwości. Jest to spowodowane wiersze dodane w tym przypadku są automatycznie udostępniane, co oznacza, że `DataGridViewRolloverCell` obiekty nie są tworzone, dopóki nie klikniesz na pojedyncze komórki, co powoduje skojarzone wierszy, które mają stać się nieudostępnionych.  
  
 Tego rodzaju dostosowanie komórek wymagają nieudostępnionych wierszy, dlatego nie jest przeznaczone do użycia z dużymi zestawami danych. Aby uzyskać więcej informacji o udostępnianiu wiersza, zobacz [najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy Windows](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
>  Po utworzeniu klasy pochodnej z <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewColumn> i dodać nowe właściwości do klasy pochodnej, pamiętaj zastąpić `Clone` metodę, aby skopiować nowe właściwości podczas operacji klonowania. Należy także wywołać klasy bazowej `Clone` metody, aby właściwości klasy bazowej są kopiowane do nowej komórce lub kolumnie.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>Dostosowywanie komórek i kolumn w formancie DataGridView  
  
1.  Klasa nowe komórki, o nazwie `DataGridViewRolloverCell`, z <xref:System.Windows.Forms.DataGridViewTextBoxCell> typu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2.  Zastąp <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> method in Class metoda `DataGridViewRolloverCell` klasy. W przypadku zastąpienia należy najpierw wywołać implementacji klasy podstawowej obsługuje funkcje pole tekstowe hostowanej. Następnie użyj formantu <xref:System.Windows.Forms.Control.PointToClient%2A> metody do przekształcenia pozycja kursora (we współrzędnych ekranu) do <xref:System.Windows.Forms.DataGridView> współrzędne obszaru klienta. Jeśli współrzędne myszy mieszczą się w granicach komórki, narysować prostokąt wstawki.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3.  Zastąp <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> i <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> metody `DataGridViewRolloverCell` klasy, aby wymusić komórek do samych odświeżenia, gdy wskaźnik myszy wnoszone lub pozostawia je.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4.  Pochodzi z nową klasę o nazwie `DataGridViewRolloverCellColumn`, z <xref:System.Windows.Forms.DataGridViewColumn> typu. W konstruktorze, Przypisz nowy `DataGridViewRolloverCell` obiektu na jego <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> właściwości.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>Przykład  
 Pełny przykład kodu zawiera formularz mały test, który demonstruje działanie typ niestandardowy komórki.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, przestrzeń nazw System.Windows.Forms i System.Drawing.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [DataGridView, kontrolka — architektura](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)
