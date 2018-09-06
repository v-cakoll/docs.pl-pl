---
title: 'Porady: zmienianie granic formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: e04234b4f2f18738567c3f9846d8ae0c94780fcb
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788223"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a><span data-ttu-id="6f9fa-102">Porady: zmienianie granic formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6f9fa-102">How to: Change the Borders of Windows Forms</span></span>
<span data-ttu-id="6f9fa-103">Masz kilka style obramowania do wyboru przy ustalaniu wygląd i zachowanie formularzy Windows.</span><span class="sxs-lookup"><span data-stu-id="6f9fa-103">You have several border styles to choose from when you are determining the appearance and behavior of your Windows Forms.</span></span> <span data-ttu-id="6f9fa-104">Zmieniając <xref:System.Windows.Forms.Form.FormBorderStyle%2A> właściwości, można kontrolować zachowanie zmiany rozmiaru formularza.</span><span class="sxs-lookup"><span data-stu-id="6f9fa-104">By changing the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property, you can control the resizing behavior of the form.</span></span> <span data-ttu-id="6f9fa-105">Ponadto, ustawienie <xref:System.Windows.Forms.Form.FormBorderStyle%2A> ma wpływ na sposób wyświetlania pasek podpisu oraz jakie przycisków może pojawić się na nim.</span><span class="sxs-lookup"><span data-stu-id="6f9fa-105">In addition, setting the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> affects how the caption bar is displayed as well as what buttons might appear on it.</span></span> <span data-ttu-id="6f9fa-106">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.FormBorderStyle>.</span><span class="sxs-lookup"><span data-stu-id="6f9fa-106">For more information, see <xref:System.Windows.Forms.FormBorderStyle>.</span></span>  
  
 <span data-ttu-id="6f9fa-107">Brak zaawansowaną obsługę dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6f9fa-107">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="6f9fa-108">Zobacz też [porady: Zmienianie granic formularzy Windows za pomocą projektanta](https://msdn.microsoft.com/library/yettzh3e\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="6f9fa-108">See also [How to: Change the Borders of Windows Forms Using the Designer](https://msdn.microsoft.com/library/yettzh3e\(v=vs.110\)).</span></span>  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a><span data-ttu-id="6f9fa-109">Aby programowo ustawić styl obramowania formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6f9fa-109">To set the border style of Windows Forms programmatically</span></span>  
  
-   <span data-ttu-id="6f9fa-110">Ustaw <xref:System.Windows.Forms.Form.FormBorderStyle%2A> właściwość żądany styl.</span><span class="sxs-lookup"><span data-stu-id="6f9fa-110">Set the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to the style you want.</span></span> <span data-ttu-id="6f9fa-111">Poniższy przykład kodu ustawia styl obramowania w postaci `DlgBx1` do <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span><span class="sxs-lookup"><span data-stu-id="6f9fa-111">The following code example sets the border style of form `DlgBx1` to <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span></span>  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     <span data-ttu-id="6f9fa-112">Zobacz też [porady: tworzenie okien dialogowych w czasie projektowania](https://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="6f9fa-112">Also see [How to: Create Dialog Boxes at Design Time](https://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\)).</span></span>  
  
     <span data-ttu-id="6f9fa-113">Ponadto jeśli wybrano opcję Styl obramowania formularza, który zawiera opcjonalne **Minimalizuj** i **Maksymalizuj** przyciski, użytkownik może określić, czy jednego lub obu tych przycisków, aby działała prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="6f9fa-113">Additionally, if you have chosen a border style for the form that provides optional **Minimize** and **Maximize** buttons, you can specify whether you want either or both of these buttons to be functional.</span></span> <span data-ttu-id="6f9fa-114">Przyciski te są przydatne, jeśli chcesz ściśle kontrolować środowiska użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6f9fa-114">These buttons are useful when you want to closely control the user experience.</span></span> <span data-ttu-id="6f9fa-115">**Minimalizuj** i **Maksymalizuj** przyciski są domyślnie włączone, a ich funkcjonalność jest przetwarzany przez **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="6f9fa-115">The **Minimize** and **Maximize** buttons are enabled by default, and their functionality is manipulated through the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f9fa-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f9fa-116">See Also</span></span>  
 <xref:System.Windows.Forms.FormBorderStyle>  
 <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>  
 [<span data-ttu-id="6f9fa-117">Wprowadzenie do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6f9fa-117">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
