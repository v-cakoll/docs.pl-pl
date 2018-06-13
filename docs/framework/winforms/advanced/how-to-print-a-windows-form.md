---
title: 'Porady: drukowanie formularza systemu Windows'
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
ms.openlocfilehash: 42940654a0754ac3616ca7983af07d20607f480f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522272"
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="35b97-102">Porady: drukowanie formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="35b97-102">How to: Print a Windows Form</span></span>
<span data-ttu-id="35b97-103">W ramach procesu tworzenia zwykle można wydrukować kopię formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="35b97-103">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="35b97-104">Poniższy przykładowy kod przedstawia sposób wydrukować kopię bieżącego formularza za pomocą <xref:System.Drawing.Graphics.CopyFromScreen%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="35b97-104">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35b97-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="35b97-105">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="35b97-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="35b97-106">Compiling the Code</span></span>  
 <span data-ttu-id="35b97-107">To jest przykład kompletny kod, który zawiera `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="35b97-107">This is a complete code example that contains a `Main` method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="35b97-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="35b97-108">Robust Programming</span></span>  
 <span data-ttu-id="35b97-109">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="35b97-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="35b97-110">Nie masz uprawnień dostępu do drukarki.</span><span class="sxs-lookup"><span data-stu-id="35b97-110">You do not have permission to access the printer.</span></span>  
  
-   <span data-ttu-id="35b97-111">Nie została zainstalowana drukarka.</span><span class="sxs-lookup"><span data-stu-id="35b97-111">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="35b97-112">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="35b97-112">.NET Framework Security</span></span>  
 <span data-ttu-id="35b97-113">Aby można było uruchomić ten przykład kodu, musi mieć uprawnienia dostępu do drukarki, używanej do komputera.</span><span class="sxs-lookup"><span data-stu-id="35b97-113">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35b97-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35b97-114">See Also</span></span>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [<span data-ttu-id="35b97-115">Instrukcje: renderowanie obrazów za pomocą GDI+</span><span class="sxs-lookup"><span data-stu-id="35b97-115">How to: Render Images with GDI+</span></span>](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)  
 [<span data-ttu-id="35b97-116">Instrukcje: drukowanie grafiki w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="35b97-116">How to: Print Graphics in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)
