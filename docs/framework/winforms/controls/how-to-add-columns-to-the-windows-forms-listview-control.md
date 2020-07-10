---
title: Dodawanie kolumn do formantu ListView
description: Dowiedz się, jak dodać kolumny do kontrolki ListView Windows Forms, aby wyświetlić kilka typów informacji na temat każdego elementu listy.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: 7ca4e86ca3a9679876f2525c49596534f175096a
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174565"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a><span data-ttu-id="80a3a-103">Porady: dodawanie kolumn do formantu ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="80a3a-103">How to: Add Columns to the Windows Forms ListView Control</span></span>
<span data-ttu-id="80a3a-104">W widoku szczegółów <xref:System.Windows.Forms.ListView> kontrolka może wyświetlić wiele kolumn dla każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="80a3a-104">In the Details view, the <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item.</span></span> <span data-ttu-id="80a3a-105">Kolumny można używać do wyświetlania użytkownikowi kilku typów informacji na temat każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="80a3a-105">You can use the columns to display to the user several types of information about each list item.</span></span> <span data-ttu-id="80a3a-106">Na przykład lista plików może zawierać nazwę pliku, typ pliku, rozmiar i datę ostatniej modyfikacji pliku.</span><span class="sxs-lookup"><span data-stu-id="80a3a-106">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="80a3a-107">Aby uzyskać informacje dotyczące wypełniania kolumn po ich utworzeniu, zobacz [How to: Display SubItems in Columns with Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="80a3a-107">For information about populating the columns after they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>  
  
### <a name="to-add-columns-programmatically"></a><span data-ttu-id="80a3a-108">Aby programowo dodać kolumny</span><span class="sxs-lookup"><span data-stu-id="80a3a-108">To add columns programmatically</span></span>  
  
1. <span data-ttu-id="80a3a-109">Ustaw właściwość kontrolki <xref:System.Windows.Forms.ListView.View%2A> na wartość <xref:System.Windows.Forms.View.Details> .</span><span class="sxs-lookup"><span data-stu-id="80a3a-109">Set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
2. <span data-ttu-id="80a3a-110">Użyj <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> metody właściwości widoku listy <xref:System.Windows.Forms.ListView.Columns%2A> .</span><span class="sxs-lookup"><span data-stu-id="80a3a-110">Use the <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> method of the list view's <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="80a3a-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80a3a-111">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="80a3a-112">ListView — Formant</span><span class="sxs-lookup"><span data-stu-id="80a3a-112">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="80a3a-113">ListView — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="80a3a-113">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
