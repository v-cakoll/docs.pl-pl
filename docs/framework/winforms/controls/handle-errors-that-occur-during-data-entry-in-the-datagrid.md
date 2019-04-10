---
title: 'Instrukcje: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
ms.assetid: 9004e72f-fdec-4264-a37d-2c99764efc13
ms.openlocfilehash: e5ba42c2ff86f46e2722d0f4455c10ab7b85af1c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204656"
---
# <a name="how-to-handle-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>Instrukcje: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView formularzy systemu Windows
Poniższy przykład kodu demonstruje sposób używania <xref:System.Windows.Forms.DataGridView> kontrolki błędy zapisu danych raportu dla użytkownika.  
  
 Aby uzyskać pełne wyjaśnienie ten przykład kodu, zobacz [instruktażu: Obsługa błędów występujących podczas wprowadzania danych w Windows formantu DataGridView formularzy](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, dane systemowe, przestrzeń nazw System.Windows.Forms i System.XML.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Przechowywanie poufnych informacji, takich jak hasła, w ciągu połączenia mogą wpływać na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Przewodnik: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView formularzy systemu Windows](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Wprowadzanie danych w formancie DataGridView formularzy systemu Windows](data-entry-in-the-windows-forms-datagridview-control.md)
- [Przewodnik: sprawdzanie poprawności danych w kontrolce DataGridView formularzy systemu Windows](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md)
