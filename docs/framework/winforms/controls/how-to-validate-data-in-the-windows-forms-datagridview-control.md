---
title: 'Instrukcje: Sprawdzanie poprawności danych w kontrolce DataGridView formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
ms.assetid: d10aef35-701e-4a3c-a684-2a2ed1aeaca6
ms.openlocfilehash: 0ebecac96e110c40b1ed96ecbc5e08ab2ebe12a5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707004"
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a>Instrukcje: Sprawdzanie poprawności danych w kontrolce DataGridView formularzy Windows Forms
Poniższy przykład kodu demonstruje sposób sprawdzania poprawności danych wprowadzanych przez użytkownika do <xref:System.Windows.Forms.DataGridView> kontroli. W tym przykładzie <xref:System.Windows.Forms.DataGridView> jest wypełniana przy użyciu wierszy z `Customers` tabelę w bazie danych Northwind. Gdy użytkownik edytuje komórkę w `CompanyName` kolumny, jego wartość jest sprawdzane pod kątem ważności, sprawdzając, czy nie jest pusty. Jeśli program obsługi zdarzeń dla <xref:System.Windows.Forms.DataGridView.CellValidating> zdarzeń wykryje, że wartość jest ciągiem pustym <xref:System.Windows.Forms.DataGridView> uniemożliwia użytkownikowi zamykania komórki, dopóki nie podano niepustym ciągiem.  
  
 Aby uzyskać pełne wyjaśnienie ten przykład kodu, zobacz [instruktażu: Sprawdzanie poprawności danych w Windows formantu DataGridView formularzy](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, dane systemowe, przestrzeń nazw System.Windows.Forms i System.XML.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Przechowywanie poufnych informacji, takich jak hasła, w ciągu połączenia mogą wpływać na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Przewodnik: Sprawdzanie poprawności danych w kontrolce DataGridView formularzy Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Przewodnik: Obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView formularzy Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md)
