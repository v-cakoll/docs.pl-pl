---
title: 'Instrukcje: Uzyskiwanie dostępu do obiektów powiązanych z Windows Forms wierszami formantu DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 5c66bc961d92a2ece1aea4986d0c23181c971b3e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720348"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a>Instrukcje: Uzyskiwanie dostępu do obiektów powiązanych z Windows Forms wierszami formantu DataGridView
Czasami warto wyświetlić tabelę informacji przechowywanych w kolekcji obiektów biznesowych. Po powiązaniu <xref:System.Windows.Forms.DataGridView> formantu do tych kolekcji, każda właściwość publiczna jest wyświetlany w kolumnie swój własny, chyba że właściwość jest oznaczona za nie można przeglądać za pomocą <xref:System.ComponentModel.BrowsableAttribute>. Na przykład zbiór `Customer` obiektów takich jak miałoby kolumn **nazwa** i **adres**.  
  
 Jeśli te obiekty zawierają dodatkowe informacje i kod, który chcesz uzyskać dostęp, mógł go osiągnąć za pomocą obiektów wiersza. W poniższym przykładzie kodu użytkowników można wybrać wiele wierszy i kliknąć przycisk służący do wysyłania faktur do każdego z odpowiednich klientów.  
  
### <a name="to-access-row-bound-objects"></a>Dostęp do obiektów powiązanych z wiersza  
  
-   Użyj <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> właściwości.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a>Przykład  
 Pełny przykład kodu zawiera prosty `Customer` implementacji i powiązań <xref:System.Windows.Forms.DataGridView> do <xref:System.Collections.ArrayList> zawierającego kilka `Customer` obiektów. <xref:System.Windows.Forms.Control.Click> Program obsługi zdarzeń <xref:System.Windows.Forms.Button?displayProperty=nameWithType> musi mieć dostęp `Customer` obiektów za pomocą wierszy, ponieważ kolekcja klienta nie jest dostępny na zewnątrz <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> programu obsługi zdarzeń.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Powiązanie obiektów do kontrolek DataGridView formularzy Windows Forms](how-to-bind-objects-to-windows-forms-datagridview-controls.md)
