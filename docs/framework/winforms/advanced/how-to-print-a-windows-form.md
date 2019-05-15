---
title: 'Instrukcje: Drukowanie formularza systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
ms.openlocfilehash: cd10e0a43ff37b921dc8e024d7a6a51fafbb0400
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591855"
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="54511-102">Instrukcje: Drukowanie formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="54511-102">How to: Print a Windows Form</span></span>
<span data-ttu-id="54511-103">Jako część procesu projektowania zazwyczaj można wydrukować formularza Windows.</span><span class="sxs-lookup"><span data-stu-id="54511-103">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="54511-104">Poniższy przykład kodu pokazuje jak drukować kopię bieżącego formularza za pomocą <xref:System.Drawing.Graphics.CopyFromScreen%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="54511-104">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54511-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="54511-105">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="54511-106">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="54511-106">Robust Programming</span></span>  
 <span data-ttu-id="54511-107">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="54511-107">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="54511-108">Nie masz uprawnień dostępu do drukarki.</span><span class="sxs-lookup"><span data-stu-id="54511-108">You do not have permission to access the printer.</span></span>  
  
- <span data-ttu-id="54511-109">Brak Brak zainstalowanej drukarki.</span><span class="sxs-lookup"><span data-stu-id="54511-109">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="54511-110">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="54511-110">.NET Framework Security</span></span>  
 <span data-ttu-id="54511-111">Aby można było uruchomić ten przykład kodu, musi mieć uprawnienia dostępu do drukarki, używanej do komputera.</span><span class="sxs-lookup"><span data-stu-id="54511-111">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54511-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54511-112">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="54511-113">Instrukcje: Renderowanie obrazów za pomocą GDI +</span><span class="sxs-lookup"><span data-stu-id="54511-113">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
- [<span data-ttu-id="54511-114">Instrukcje: Drukowanie grafiki w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="54511-114">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)
