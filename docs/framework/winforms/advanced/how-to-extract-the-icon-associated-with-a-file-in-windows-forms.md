---
title: 'Instrukcje: Wyodrębnianie ikon skojarzonych z plikiem w formularzach Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: 5cbce48643d21418d580a6db44f86b00cf50fb9d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714193"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a><span data-ttu-id="96f65-102">Instrukcje: Wyodrębnianie ikon skojarzonych z plikiem w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="96f65-102">How to: Extract the Icon Associated with a File in Windows Forms</span></span>
<span data-ttu-id="96f65-103">Wiele plików zostały osadzone ikon, które zapewniają wizualnej reprezentacji skojarzonego typu pliku.</span><span class="sxs-lookup"><span data-stu-id="96f65-103">Many files have embedded icons that provide a visual representation of the associated file type.</span></span> <span data-ttu-id="96f65-104">Na przykład dokumenty Microsoft Word zawiera ikonę która identyfikuje je jako dokumenty programu Word.</span><span class="sxs-lookup"><span data-stu-id="96f65-104">For example, Microsoft Word documents contain an icon that identifies them as Word documents.</span></span> <span data-ttu-id="96f65-105">Wyświetlanie plików w formancie listy lub kontrolki tabeli, można wyświetlić ikony reprezentującej typ pliku obok nazwy każdego pliku.</span><span class="sxs-lookup"><span data-stu-id="96f65-105">When displaying files in a list control or table control, you may want to display the icon representing the file type next to each file name.</span></span> <span data-ttu-id="96f65-106">Łatwo to zrobić, korzystając z <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="96f65-106">You can do this easily by using the <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96f65-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="96f65-107">Example</span></span>  
 <span data-ttu-id="96f65-108">Poniższy przykład kodu pokazuje, jak wyodrębnianie ikon skojarzonych z plikiem i wyświetlić nazwę pliku i jego skojarzonej ikony w <xref:System.Windows.Forms.ListView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="96f65-108">The following code example demonstrates how to extract the icon associated with a file and display the file name and its associated icon in a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="96f65-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="96f65-109">Compiling the Code</span></span>  
 <span data-ttu-id="96f65-110">Aby skompilować przykład:</span><span class="sxs-lookup"><span data-stu-id="96f65-110">To compile the example:</span></span>  
  
-   <span data-ttu-id="96f65-111">Wklej powyższy kod do formularza Windows i Wywołaj `ExtractAssociatedIconExample` metody z konstruktora formularza lub <xref:System.Windows.Forms.Form.Load> metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="96f65-111">Paste the preceding code into a Windows Form, and call the `ExtractAssociatedIconExample` method from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     <span data-ttu-id="96f65-112">Należy się upewnić, że formularz importuje <xref:System.IO> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="96f65-112">You will need to make sure that your form imports the <xref:System.IO> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96f65-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96f65-113">See also</span></span>
- [<span data-ttu-id="96f65-114">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="96f65-114">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="96f65-115">Kontrolka ListView</span><span class="sxs-lookup"><span data-stu-id="96f65-115">ListView Control</span></span>](../controls/listview-control-windows-forms.md)
