---
title: 'Instrukcje: dostosowywanie komórek i kolumn w kontrolce DataGridView (Formularze systemu Windows) przez rozszerzanie ich zachowania i wyglądu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
ms.openlocfilehash: 0976a0e07aead1bbaf951c6db8266c5de1a31cd8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929701"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Instrukcje: dostosowywanie komórek i kolumn w kontrolce DataGridView (Formularze systemu Windows) przez rozszerzanie ich zachowania i wyglądu
<xref:System.Windows.Forms.DataGridView> Formant zawiera wiele sposobów dostosowywania wyglądu i zachowania przy użyciu właściwości, zdarzeń i klas pomocniczych. Czasami mogą istnieć wymagania dotyczące komórek, które wykraczają poza te funkcje. Możesz utworzyć własną klasę niestandardową <xref:System.Windows.Forms.DataGridViewCell> , aby zapewnić rozszerzoną funkcjonalność.  
  
 Utwórz klasę niestandardową <xref:System.Windows.Forms.DataGridViewCell> , pobierając ją <xref:System.Windows.Forms.DataGridViewCell> z klasy bazowej lub jednej z jej klas pochodnych. Chociaż można wyświetlić dowolną kolumnę w dowolnym typie kolumny, zazwyczaj utworzysz również klasę niestandardową <xref:System.Windows.Forms.DataGridViewColumn> wyspecjalizowaną do wyświetlania typu komórki. Klasy kolumn pochodzą z <xref:System.Windows.Forms.DataGridViewColumn> lub jeden z jego typów pochodnych.  
  
 W poniższym przykładzie kodu utworzysz klasę komórki niestandardowej o nazwie `DataGridViewRolloverCell` , która wykrywa czas wejścia myszy i opuszcza granice komórki. Gdy mysz znajduje się w granicach komórki, jest rysowany prostokąt marginesu. Ten nowy typ pochodzi z <xref:System.Windows.Forms.DataGridViewTextBoxCell> i zachowuje wszystkie inne względy jako jego klasę bazową. Klasa pomocniczej kolumny jest wywoływana `DataGridViewRolloverColumn`.  
  
 Aby użyć tych klas, należy utworzyć formularz zawierający <xref:System.Windows.Forms.DataGridView> formant, dodać jeden lub więcej `DataGridViewRolloverColumn` obiektów do <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekcji i wypełnić formant wierszami zawierającymi wartości.  
  
> [!NOTE]
> Ten przykład nie będzie działał poprawnie, jeśli dodasz puste wiersze. Puste wiersze są tworzone, na przykład po dodaniu wierszy do kontrolki przez ustawienie <xref:System.Windows.Forms.DataGridView.RowCount%2A> właściwości. Dzieje się tak, ponieważ wiersze dodane w tym przypadku są automatycznie udostępniane, co oznacza `DataGridViewRolloverCell` , że obiekty nie są tworzone do momentu kliknięcia pojedynczych komórek, co spowoduje, że skojarzone wiersze staną się nieudostępnione.  
  
 Ponieważ ten typ dostosowania komórki wymaga nieudostępnianych wierszy, nie jest on odpowiedni do użycia z dużymi zestawami danych. Aby uzyskać więcej informacji na temat udostępniania wierszy, zobacz [najlepsze rozwiązania dotyczące skalowania Windows Forms formantu DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
> Gdy pochodzą z <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewColumn> i dodajesz nowe właściwości do klasy pochodnej, pamiętaj, aby zastąpić `Clone` metodę, aby skopiować nowe właściwości podczas klonowania operacji. Należy również wywołać `Clone` metodę klasy bazowej, aby właściwości klasy bazowej były kopiowane do nowej komórki lub kolumny.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>Aby dostosować komórki i kolumny w formancie DataGridView  
  
1. Utwórz nową klasę komórki o nazwie `DataGridViewRolloverCell` <xref:System.Windows.Forms.DataGridViewTextBoxCell> z typu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2. Zastąp `DataGridViewRolloverCell` metodę w klasie. <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> W przesłonięciu najpierw Wywołaj implementację klasy bazowej, która obsługuje funkcję hostowanego pola tekstowego. Następnie użyj <xref:System.Windows.Forms.Control.PointToClient%2A> metody kontrolki do przekształcenia położenia kursora (we współrzędnych ekranu) <xref:System.Windows.Forms.DataGridView> do współrzędnych obszaru klienta. Jeśli Współrzędne myszy znajdują się w granicach komórki, narysuj prostokąt wstawki.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3. Zastąp metody <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> `DataGridViewRolloverCell` i w klasie, aby wymusić odświeżenie komórek, gdy wskaźnik myszy zostanie wprowadzony lub pozostawiony. <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4. Utwórz nową klasę o nazwie, `DataGridViewRolloverCellColumn`która <xref:System.Windows.Forms.DataGridViewColumn> jest wywoływana z typu. W konstruktorze Przypisz nowy `DataGridViewRolloverCell` obiekt do jego <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> właściwości.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>Przykład  
 Kompletny przykład kodu zawiera mały formularz testu, który demonstruje zachowanie niestandardowego typu komórki.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Windows. Forms i system. Drawing.  
 
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](customizing-the-windows-forms-datagridview-control.md)
- [DataGridView, kontrolka — architektura](datagridview-control-architecture-windows-forms.md)
- [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
- [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
