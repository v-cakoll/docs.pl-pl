---
title: 'Porady: dostosowywanie komórek i kolumn w formancie DataGridView (Formularze systemu Windows) przez rozszerzanie ich zachowania i wyglądu'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8e48c5d451b4eece1bd88916e33f6a61d646b7fa
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Porady: dostosowywanie komórek i kolumn w formancie DataGridView (Formularze systemu Windows) przez rozszerzanie ich zachowania i wyglądu
<xref:System.Windows.Forms.DataGridView> Kontrola zapewnia wiele sposobów, aby dostosować wygląd i zachowanie przy użyciu właściwości, zdarzenia oraz pomocniczy klasy. Czasami mogą mieć wymagania dla Twojego komórek wykraczające poza co te funkcje mogą mieć. Możesz utworzyć własne <xref:System.Windows.Forms.DataGridViewCell> klasę, aby umożliwić korzystanie z funkcji rozszerzonej.  
  
 Utworzenie niestandardowego <xref:System.Windows.Forms.DataGridViewCell> przy pochodny <xref:System.Windows.Forms.DataGridViewCell> klasy podstawowej lub jednej z jej klas pochodnych. Choć można wyświetlać dowolnego typu komórki w typu kolumny, zazwyczaj również utworzysz niestandardowego <xref:System.Windows.Forms.DataGridViewColumn> klasy przeznaczone do wyświetlania danego typu komórki. Klasy kolumny pochodzić od <xref:System.Windows.Forms.DataGridViewColumn> lub jednego z jego typów pochodnych.  
  
 W poniższym przykładzie kodu utworzy komórki niestandardowej klasy o nazwie `DataGridViewRolloverCell` wykrywa, gdy wskaźnik myszy uzyskuje i opuszcza granicach komórki. Gdy wskaźnik myszy znajduje się w granicach komórki, jest rysowane krawędzi prostokąta. Ten nowy typ pochodzi z <xref:System.Windows.Forms.DataGridViewTextBoxCell> i działa we wszystkich innych aspektach jako swojej klasy podstawowej. Klasa kolumny pomocnika jest nazywana `DataGridViewRolloverColumn`.  
  
 Aby korzystać z tych klas, Utwórz zawierający formularz <xref:System.Windows.Forms.DataGridView> kontrolować, Dodaj co najmniej jeden `DataGridViewRolloverColumn` obiekty do <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekcji i umieścić w formancie wiersze zawierające wartości.  
  
> [!NOTE]
>  W tym przykładzie nie będzie działać poprawnie, jeśli dodasz puste wiersze. Puste wiersze są tworzone, na przykład podczas dodawania wierszy do formantu przez ustawienie <xref:System.Windows.Forms.DataGridView.RowCount%2A> właściwości. Wynika to z faktu wierszy dodawanych w tym przypadku są automatycznie udostępniane, co oznacza, że `DataGridViewRolloverCell` obiekty nie są wystąpienia, dopóki nie klikniesz w wybranych komórek, co powoduje skojarzone wierszy, które mają stać się nieudostępnionych.  
  
 Ponieważ tego rodzaju dostosowania komórki wymaga nieudostępnionych wierszy, nie jest odpowiedni dla dużych zestawów danych. Aby uzyskać więcej informacji o udostępnianiu wiersza, zobacz [najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
>  Jeśli pochodzi od <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewColumn> i dodać nowe właściwości do klasy pochodnej, należy zastąpić `Clone` metodę, aby skopiować nowe właściwości podczas operacji klonowania. Należy także wywołać klasy podstawowej `Clone` metody, aby właściwości klasy podstawowej są kopiowane do nowej komórki lub kolumny.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>Aby dostosować komórek i kolumn w formancie DataGridView  
  
1.  Pochodzi nową klasę komórki, o nazwie `DataGridViewRolloverCell`, z <xref:System.Windows.Forms.DataGridViewTextBoxCell> typu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2.  Zastąpienie <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> metoda `DataGridViewRolloverCell` klasy. W przypadku zastąpienia należy najpierw wywołać implementacji klasy podstawowej obsługi funkcji pole hostowanej tekstu. Następnie użyj formantu <xref:System.Windows.Forms.Control.PointToClient%2A> metody do przekształcenia pozycji kursora (we współrzędnych ekranu) do <xref:System.Windows.Forms.DataGridView> współrzędne obszaru klienckiego. Jeśli współrzędne myszy w granicach komórki, Rysuj prostokąt krawędzi.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3.  Zastąpienie <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> i <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> metod w `DataGridViewRolloverCell` klasy, aby wymusić komórek w celu odświeżenia się, gdy wskaźnik myszy wprowadza lub opuszcza je.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4.  Pochodzi nową klasę o nazwie `DataGridViewRolloverCellColumn`, z <xref:System.Windows.Forms.DataGridViewColumn> typu. W konstruktorze, Przypisz nowy `DataGridViewRolloverCell` obiektu do jego <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> właściwości.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>Przykład  
 Pełny przykład kodu zawiera formularz teście małych prezentującą zachowania typu niestandardowego komórki.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Windows.Forms i System.Drawing.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [DataGridView, kontrolka — architektura](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)
