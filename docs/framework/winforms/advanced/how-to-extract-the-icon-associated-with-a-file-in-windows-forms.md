---
title: 'Porady: wyodrębnianie ikon skojarzonych z plikiem w formularzach systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: 21bce2f630649afb59272362a7f40055855ed512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a><span data-ttu-id="10e1a-102">Porady: wyodrębnianie ikon skojarzonych z plikiem w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="10e1a-102">How to: Extract the Icon Associated with a File in Windows Forms</span></span>
<span data-ttu-id="10e1a-103">Wiele plików zostały osadzone ikony, które pozwalają wizualną reprezentację skojarzonego typu pliku.</span><span class="sxs-lookup"><span data-stu-id="10e1a-103">Many files have embedded icons that provide a visual representation of the associated file type.</span></span> <span data-ttu-id="10e1a-104">Na przykład Microsoft Word dokumenty zawierają ikonę, która identyfikuje je jako dokumenty programu Word.</span><span class="sxs-lookup"><span data-stu-id="10e1a-104">For example, Microsoft Word documents contain an icon that identifies them as Word documents.</span></span> <span data-ttu-id="10e1a-105">Wyświetlanie plików w formancie listy lub formancie tabeli, możesz wyświetlić ikonę reprezentujący typ pliku obok nazwy każdego pliku.</span><span class="sxs-lookup"><span data-stu-id="10e1a-105">When displaying files in a list control or table control, you may want to display the icon representing the file type next to each file name.</span></span> <span data-ttu-id="10e1a-106">Łatwo to zrobić, za pomocą <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="10e1a-106">You can do this easily by using the <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10e1a-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="10e1a-107">Example</span></span>  
 <span data-ttu-id="10e1a-108">W poniższym przykładzie pokazano, jak wyodrębnianie ikon skojarzonych z plikiem i wyświetlić nazwę pliku i jego skojarzony ikonę w <xref:System.Windows.Forms.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="10e1a-108">The following code example demonstrates how to extract the icon associated with a file and display the file name and its associated icon in a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="10e1a-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="10e1a-109">Compiling the Code</span></span>  
 <span data-ttu-id="10e1a-110">Aby skompilować w przykładzie:</span><span class="sxs-lookup"><span data-stu-id="10e1a-110">To compile the example:</span></span>  
  
-   <span data-ttu-id="10e1a-111">Wklej poprzedni kod w formularzu systemu Windows, a wywołania `ExtractAssociatedIconExample` metody z Konstruktor elementu form lub <xref:System.Windows.Forms.Form.Load> metoda obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="10e1a-111">Paste the preceding code into a Windows Form, and call the `ExtractAssociatedIconExample` method from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     <span data-ttu-id="10e1a-112">Należy się upewnić, że formularz importuje <xref:System.IO> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="10e1a-112">You will need to make sure that your form imports the <xref:System.IO> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10e1a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10e1a-113">See Also</span></span>  
 [<span data-ttu-id="10e1a-114">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="10e1a-114">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="10e1a-115">Kontrolka ListView</span><span class="sxs-lookup"><span data-stu-id="10e1a-115">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
