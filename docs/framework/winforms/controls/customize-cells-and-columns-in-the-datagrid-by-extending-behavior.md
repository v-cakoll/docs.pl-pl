---
title: Dostosowywanie komórek i kolumn w formancie DataGridView przez rozszerzenie ich zachowania i wyglądu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
ms.openlocfilehash: be01e085d4fa74c0c49f0a0494183482875c6a09
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744063"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Porady: dostosowywanie komórek i kolumn w formancie DataGridView (Formularze systemu Windows) przez rozszerzanie ich zachowania i wyglądu
Formant <xref:System.Windows.Forms.DataGridView> zapewnia wiele sposobów dostosowywania wyglądu i zachowania przy użyciu właściwości, zdarzeń i klas pomocniczych. Czasami mogą istnieć wymagania dotyczące komórek, które wykraczają poza te funkcje. Możesz utworzyć własną niestandardową klasę <xref:System.Windows.Forms.DataGridViewCell>, aby zapewnić rozszerzoną funkcjonalność.  
  
 Utwórz niestandardową klasę <xref:System.Windows.Forms.DataGridViewCell>, pobierając ją z klasy bazowej <xref:System.Windows.Forms.DataGridViewCell> lub jednej z jej klas pochodnych. Chociaż można wyświetlić każdą kolumnę dowolnego typu, zazwyczaj utworzysz niestandardową klasę <xref:System.Windows.Forms.DataGridViewColumn> wyspecjalizowaną do wyświetlania typu komórki. Klasy kolumn pochodzą z <xref:System.Windows.Forms.DataGridViewColumn> lub jednego z jego typów pochodnych.  
  
 W poniższym przykładzie kodu utworzysz klasę komórki niestandardowej o nazwie `DataGridViewRolloverCell`, która wykrywa, kiedy mysz zostanie wprowadzona i opuszcza granice komórki. Gdy mysz znajduje się w granicach komórki, jest rysowany prostokąt marginesu. Ten nowy typ pochodzi od <xref:System.Windows.Forms.DataGridViewTextBoxCell> i zachowuje się we wszystkich innych aspektach jako klasa bazowa. Klasa pomocniczej kolumny jest nazywana `DataGridViewRolloverColumn`.  
  
 Aby użyć tych klas, należy utworzyć formularz zawierający formant <xref:System.Windows.Forms.DataGridView>, dodać jeden lub więcej obiektów `DataGridViewRolloverColumn` do kolekcji <xref:System.Windows.Forms.DataGridView.Columns%2A> i wypełnić formant wierszami zawierającymi wartości.  
  
> [!NOTE]
> Ten przykład nie będzie działał poprawnie, jeśli dodasz puste wiersze. Puste wiersze są tworzone, na przykład po dodaniu wierszy do kontrolki przez ustawienie właściwości <xref:System.Windows.Forms.DataGridView.RowCount%2A>. Jest to spowodowane tym, że wiersze dodane w tym przypadku są automatycznie udostępniane, co oznacza, że `DataGridViewRolloverCell` obiekty nie są tworzone do momentu kliknięcia pojedynczych komórek, co spowoduje, że skojarzone wiersze staną się nieudostępnione.  
  
 Ponieważ ten typ dostosowania komórki wymaga nieudostępnianych wierszy, nie jest on odpowiedni do użycia z dużymi zestawami danych. Aby uzyskać więcej informacji na temat udostępniania wierszy, zobacz [najlepsze rozwiązania dotyczące skalowania Windows Forms formantu DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
> Gdy dziedziczysz z <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewColumn> i dodasz nowe właściwości do klasy pochodnej, pamiętaj, aby zastąpić metodę `Clone`, aby skopiować nowe właściwości podczas klonowania operacji. Należy również wywołać metodę `Clone` klasy bazowej, aby właściwości klasy bazowej były kopiowane do nowej komórki lub kolumny.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>Aby dostosować komórki i kolumny w formancie DataGridView  
  
1. Utwórz nową klasę komórki o nazwie `DataGridViewRolloverCell`z typu <xref:System.Windows.Forms.DataGridViewTextBoxCell>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2. Zastąp metodę <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> w klasie `DataGridViewRolloverCell`. W przesłonięciu najpierw Wywołaj implementację klasy bazowej, która obsługuje funkcję hostowanego pola tekstowego. Następnie użyj metody <xref:System.Windows.Forms.Control.PointToClient%2A> kontrolki do przekształcenia położenia kursora (we współrzędnych ekranu) do współrzędnych obszaru <xref:System.Windows.Forms.DataGridView> klienta. Jeśli Współrzędne myszy znajdują się w granicach komórki, narysuj prostokąt wstawki.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3. Zastąp <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> i <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> metod w klasie `DataGridViewRolloverCell`, aby wymusić, że komórki są odświeżane, gdy wskaźnik myszy zostanie wprowadzony lub pozostawiony.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4. Utwórz nową klasę o nazwie `DataGridViewRolloverCellColumn`z typu <xref:System.Windows.Forms.DataGridViewColumn>. W konstruktorze Przypisz nowy obiekt `DataGridViewRolloverCell` do jego właściwości <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A>.  
  
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
