---
title: "Porady: wyodrębnianie ikon skojarzonych z plikiem w formularzach systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a5153f6389c4477a18c647d7cdaf7b49b43bb7ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a><span data-ttu-id="82719-102">Porady: wyodrębnianie ikon skojarzonych z plikiem w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="82719-102">How to: Extract the Icon Associated with a File in Windows Forms</span></span>
<span data-ttu-id="82719-103">Wiele plików zostały osadzone ikony, które pozwalają wizualną reprezentację skojarzonego typu pliku.</span><span class="sxs-lookup"><span data-stu-id="82719-103">Many files have embedded icons that provide a visual representation of the associated file type.</span></span> <span data-ttu-id="82719-104">Na przykład Microsoft Word dokumenty zawierają ikonę, która identyfikuje je jako dokumenty programu Word.</span><span class="sxs-lookup"><span data-stu-id="82719-104">For example, Microsoft Word documents contain an icon that identifies them as Word documents.</span></span> <span data-ttu-id="82719-105">Wyświetlanie plików w formancie listy lub formancie tabeli, możesz wyświetlić ikonę reprezentujący typ pliku obok nazwy każdego pliku.</span><span class="sxs-lookup"><span data-stu-id="82719-105">When displaying files in a list control or table control, you may want to display the icon representing the file type next to each file name.</span></span> <span data-ttu-id="82719-106">Łatwo to zrobić, za pomocą <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="82719-106">You can do this easily by using the <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82719-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="82719-107">Example</span></span>  
 <span data-ttu-id="82719-108">W poniższym przykładzie pokazano, jak wyodrębnianie ikon skojarzonych z plikiem i wyświetlić nazwę pliku i jego skojarzony ikonę w <xref:System.Windows.Forms.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="82719-108">The following code example demonstrates how to extract the icon associated with a file and display the file name and its associated icon in a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="82719-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="82719-109">Compiling the Code</span></span>  
 <span data-ttu-id="82719-110">Aby skompilować w przykładzie:</span><span class="sxs-lookup"><span data-stu-id="82719-110">To compile the example:</span></span>  
  
-   <span data-ttu-id="82719-111">Wklej poprzedni kod w formularzu systemu Windows, a wywołania `ExtractAssociatedIconExample` metody z Konstruktor elementu form lub <xref:System.Windows.Forms.Form.Load> metoda obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="82719-111">Paste the preceding code into a Windows Form, and call the `ExtractAssociatedIconExample` method from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     <span data-ttu-id="82719-112">Należy się upewnić, że formularz importuje <xref:System.IO> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="82719-112">You will need to make sure that your form imports the <xref:System.IO> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82719-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="82719-113">See Also</span></span>  
 [<span data-ttu-id="82719-114">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="82719-114">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="82719-115">Kontrolka ListView</span><span class="sxs-lookup"><span data-stu-id="82719-115">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
