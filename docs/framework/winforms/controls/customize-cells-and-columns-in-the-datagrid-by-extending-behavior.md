---
title: Dostosowywanie komórek i kolumn w formancie DataGridView przez rozszerzanie ich zachowania i wyglądu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
ms.openlocfilehash: e111f0bce812fc0851fabd1fde0fc2a6d44dd25f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182391"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Porady: dostosowywanie komórek i kolumn w formancie DataGridView (Formularze systemu Windows) przez rozszerzanie ich zachowania i wyglądu
Formant <xref:System.Windows.Forms.DataGridView> udostępnia wiele sposobów, aby dostosować jego wygląd i zachowanie przy użyciu właściwości, zdarzeń i klas towarzyszących. Od czasu do czasu możesz mieć wymagania dotyczące komórek, które wykraczają poza to, co te funkcje mogą zapewnić. Można utworzyć własną <xref:System.Windows.Forms.DataGridViewCell> klasę niestandardową, aby zapewnić rozszerzone funkcje.  
  
 Klasy niestandardowej <xref:System.Windows.Forms.DataGridViewCell> można utworzyć, <xref:System.Windows.Forms.DataGridViewCell> wyprowadzając się z klasy podstawowej lub jednej z jej klas pochodnych. Chociaż można wyświetlić dowolny typ komórki w dowolnym typie kolumny, <xref:System.Windows.Forms.DataGridViewColumn> zazwyczaj można również utworzyć klasę niestandardową wyspecjalizowaną do wyświetlania typu komórki. Klasy kolumn wywodzą się z <xref:System.Windows.Forms.DataGridViewColumn> lub jeden z jego typów pochodnych.  
  
 W poniższym przykładzie kodu utworzysz `DataGridViewRolloverCell` niestandardową klasę komórek o nazwie, która wykrywa, kiedy mysz wchodzi i opuszcza granice komórek. Gdy mysz znajduje się w granicach komórki, rysowany jest prostokąt wstawki. Ten nowy typ <xref:System.Windows.Forms.DataGridViewTextBoxCell> pochodzi od i zachowuje się we wszystkich innych aspektach jako jego klasy podstawowej. Klasa kolumny towarzyszącej `DataGridViewRolloverColumn`jest wywoływana .  
  
 Aby użyć tych klas, należy <xref:System.Windows.Forms.DataGridView> utworzyć formularz zawierający `DataGridViewRolloverColumn` formant, dodać jeden lub więcej obiektów do <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekcji i wypełnić formant wierszami zawierającymi wartości.  
  
> [!NOTE]
> Ten przykład nie będzie działać poprawnie, jeśli dodasz puste wiersze. Puste wiersze są tworzone, na przykład podczas dodawania wierszy do formantu przez ustawienie <xref:System.Windows.Forms.DataGridView.RowCount%2A> właściwości. Dzieje się tak, ponieważ wiersze dodane w tym `DataGridViewRolloverCell` przypadku są automatycznie udostępniane, co oznacza, że obiekty nie są tworzone, dopóki nie klikniesz poszczególnych komórek, co powoduje, że skojarzone wiersze stają się nieudostępnione.  
  
 Ponieważ ten typ dostosowywania komórek wymaga nieudostępnionych wierszy, nie jest odpowiedni do użycia z dużymi zestawami danych. Aby uzyskać więcej informacji na temat udostępniania [wierszy, zobacz Najważniejsze wskazówki dotyczące skalowania formantu DataGridView formularzy systemu Windows](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
> Po wyprowadzeniu lub <xref:System.Windows.Forms.DataGridViewCell> <xref:System.Windows.Forms.DataGridViewColumn> i dodać nowe właściwości do klasy pochodnej, `Clone` należy zastąpić metodę kopiowania nowych właściwości podczas operacji klonowania. Należy również wywołać `Clone` metodę klasy podstawowej, tak aby właściwości klasy podstawowej były kopiowane do nowej komórki lub kolumny.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>Aby dostosować komórki i kolumny w formancie DataGridView  
  
1. Wywodź nową klasę `DataGridViewRolloverCell`komórek, <xref:System.Windows.Forms.DataGridViewTextBoxCell> o nazwie , od typu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2. Zastądnie <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> metody `DataGridViewRolloverCell` w klasie. W zastąpienia najpierw wywołać implementacji klasy podstawowej, która obsługuje funkcjonalność hostowanego pola tekstowego. Następnie użyj <xref:System.Windows.Forms.Control.PointToClient%2A> metody formantu, aby przekształcić położenie kursora (we <xref:System.Windows.Forms.DataGridView> współrzędnych ekranu) do współrzędnych obszaru klienta. Jeśli współrzędne myszy mieszczą się w granicach komórki, narysuj prostokąt wstawki.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3. Zastąpokaj <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> metody i metody <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> w klasie, `DataGridViewRolloverCell` aby wymusić na komórkach ponowne malowanie się, gdy wskaźnik myszy wejdzie lub opuści je.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4. Wywodź nową `DataGridViewRolloverCellColumn`klasę, <xref:System.Windows.Forms.DataGridViewColumn> o nazwie , od typu. W konstruktorze przypisz `DataGridViewRolloverCell` nowy <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> obiekt do jego właściwości.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>Przykład  
 Przykład pełnego kodu zawiera mały formularz testowy, który pokazuje zachowanie niestandardowego typu komórki.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów System, System.Windows.Forms i System.Drawing.  

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Dostosowywanie formantu DataGridView formularzy systemu Windows](customizing-the-windows-forms-datagridview-control.md)
- [DataGridView, kontrolka — architektura](datagridview-control-architecture-windows-forms.md)
- [Typy kolumn w formancie DataGridView formularzy systemu Windows](column-types-in-the-windows-forms-datagridview-control.md)
- [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
