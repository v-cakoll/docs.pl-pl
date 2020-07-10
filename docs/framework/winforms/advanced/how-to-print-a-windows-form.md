---
title: 'Porady: drukowanie formularza systemu Windows'
description: Dowiedz się, jak programowo wydrukować kopię bieżącego formularza systemu Windows przy użyciu metody CopyFromScreen.
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
ms.openlocfilehash: b59ea4b5347903b36a166c4f8ac0d8d7db18635e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174695"
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="cc57c-103">Porady: drukowanie formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cc57c-103">How to: Print a Windows Form</span></span>
<span data-ttu-id="cc57c-104">W ramach procesu tworzenia zwykle warto wydrukować kopię formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="cc57c-104">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="cc57c-105">Poniższy przykład kodu pokazuje, jak wydrukować kopię bieżącego formularza przy użyciu <xref:System.Drawing.Graphics.CopyFromScreen%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cc57c-105">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc57c-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc57c-106">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="cc57c-107">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="cc57c-107">Robust Programming</span></span>  
 <span data-ttu-id="cc57c-108">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="cc57c-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="cc57c-109">Nie masz uprawnień dostępu do drukarki.</span><span class="sxs-lookup"><span data-stu-id="cc57c-109">You do not have permission to access the printer.</span></span>  
  
- <span data-ttu-id="cc57c-110">Nie ma zainstalowanej drukarki.</span><span class="sxs-lookup"><span data-stu-id="cc57c-110">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="cc57c-111">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="cc57c-111">.NET Framework Security</span></span>  
 <span data-ttu-id="cc57c-112">Aby można było uruchomić ten przykład kodu, musisz mieć uprawnienia dostępu do drukarki używanej na komputerze.</span><span class="sxs-lookup"><span data-stu-id="cc57c-112">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc57c-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc57c-113">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="cc57c-114">Instrukcje: renderowanie obrazów za pomocą GDI+</span><span class="sxs-lookup"><span data-stu-id="cc57c-114">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
- [<span data-ttu-id="cc57c-115">Instrukcje: drukowanie grafiki w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc57c-115">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)
