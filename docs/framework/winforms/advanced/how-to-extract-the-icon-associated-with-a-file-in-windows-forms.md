---
title: 'Instrukcje: Wyodrębnianie ikony skojarzonej z plikiem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: 28769144b0e1c631a31c3c541747a6215f861d0e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742543"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a><span data-ttu-id="8ae40-102">Porady: wyodrębnianie ikon skojarzonych z plikiem w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8ae40-102">How to: Extract the Icon Associated with a File in Windows Forms</span></span>
<span data-ttu-id="8ae40-103">Wiele plików ma osadzone ikony, które zapewniają wizualną reprezentację skojarzonego typu pliku.</span><span class="sxs-lookup"><span data-stu-id="8ae40-103">Many files have embedded icons that provide a visual representation of the associated file type.</span></span> <span data-ttu-id="8ae40-104">Na przykład dokumenty programu Microsoft Word zawierają ikonę, która identyfikuje je jako dokumenty programu Word.</span><span class="sxs-lookup"><span data-stu-id="8ae40-104">For example, Microsoft Word documents contain an icon that identifies them as Word documents.</span></span> <span data-ttu-id="8ae40-105">Podczas wyświetlania plików w kontrolce listy lub formancie tabeli można wyświetlić ikonę reprezentującą typ pliku obok każdej nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="8ae40-105">When displaying files in a list control or table control, you may want to display the icon representing the file type next to each file name.</span></span> <span data-ttu-id="8ae40-106">Można to łatwo zrobić przy użyciu metody <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A>.</span><span class="sxs-lookup"><span data-stu-id="8ae40-106">You can do this easily by using the <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ae40-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ae40-107">Example</span></span>  
 <span data-ttu-id="8ae40-108">Poniższy przykład kodu demonstruje, jak wyodrębnić ikonę skojarzoną z plikiem i wyświetlić nazwę pliku oraz skojarzoną ikonę w kontrolce <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="8ae40-108">The following code example demonstrates how to extract the icon associated with a file and display the file name and its associated icon in a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8ae40-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="8ae40-109">Compiling the Code</span></span>  
 <span data-ttu-id="8ae40-110">Aby skompilować przykład:</span><span class="sxs-lookup"><span data-stu-id="8ae40-110">To compile the example:</span></span>  
  
- <span data-ttu-id="8ae40-111">Wklej poprzedni kod do formularza systemu Windows i Wywołaj metodę `ExtractAssociatedIconExample` z konstruktora formularza lub <xref:System.Windows.Forms.Form.Load> metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8ae40-111">Paste the preceding code into a Windows Form, and call the `ExtractAssociatedIconExample` method from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     <span data-ttu-id="8ae40-112">Należy upewnić się, że formularz importuje <xref:System.IO> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8ae40-112">You will need to make sure that your form imports the <xref:System.IO> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ae40-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ae40-113">See also</span></span>

- [<span data-ttu-id="8ae40-114">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="8ae40-114">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="8ae40-115">Kontrolka ListView</span><span class="sxs-lookup"><span data-stu-id="8ae40-115">ListView Control</span></span>](../controls/listview-control-windows-forms.md)
