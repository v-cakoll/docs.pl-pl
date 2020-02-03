---
title: Zmień obramowanie formularza
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: 2c8eb25b44c7406e4312f432f2d69524346f94d6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739568"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a><span data-ttu-id="3d08a-102">Porady: zmienianie granic formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3d08a-102">How to: Change the Borders of Windows Forms</span></span>
<span data-ttu-id="3d08a-103">Istnieje kilka stylów obramowania, które można wybrać podczas określania wyglądu i zachowania Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3d08a-103">You have several border styles to choose from when you are determining the appearance and behavior of your Windows Forms.</span></span> <span data-ttu-id="3d08a-104">Zmieniając właściwość <xref:System.Windows.Forms.Form.FormBorderStyle%2A>, można kontrolować zachowanie zmiany rozmiarów formularza.</span><span class="sxs-lookup"><span data-stu-id="3d08a-104">By changing the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property, you can control the resizing behavior of the form.</span></span> <span data-ttu-id="3d08a-105">Ponadto ustawienie <xref:System.Windows.Forms.Form.FormBorderStyle%2A> wpływa na sposób wyświetlania paska podpisu, a także jakie przyciski mogą być na nim widoczne.</span><span class="sxs-lookup"><span data-stu-id="3d08a-105">In addition, setting the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> affects how the caption bar is displayed as well as what buttons might appear on it.</span></span> <span data-ttu-id="3d08a-106">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.FormBorderStyle>.</span><span class="sxs-lookup"><span data-stu-id="3d08a-106">For more information, see <xref:System.Windows.Forms.FormBorderStyle>.</span></span>  
  
 <span data-ttu-id="3d08a-107">W programie Visual Studio jest dostępna szeroka pomoc techniczna dla tego zadania.</span><span class="sxs-lookup"><span data-stu-id="3d08a-107">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="3d08a-108">Zobacz również [: Zmienianie obramowań Windows Forms przy użyciu narzędzia Projektant](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3d08a-108">See also [How to: Change the Borders of Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100)).</span></span>  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a><span data-ttu-id="3d08a-109">Aby ustawić styl obramowania Windows Forms programowo</span><span class="sxs-lookup"><span data-stu-id="3d08a-109">To set the border style of Windows Forms programmatically</span></span>  
  
- <span data-ttu-id="3d08a-110">Ustaw właściwość <xref:System.Windows.Forms.Form.FormBorderStyle%2A> na żądany styl.</span><span class="sxs-lookup"><span data-stu-id="3d08a-110">Set the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to the style you want.</span></span> <span data-ttu-id="3d08a-111">Poniższy przykład kodu ustawia styl obramowania `DlgBx1`, aby <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span><span class="sxs-lookup"><span data-stu-id="3d08a-111">The following code example sets the border style of form `DlgBx1` to <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span></span>  
  
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
  
     <span data-ttu-id="3d08a-112">Zobacz również [instrukcje: tworzenie okien dialogowych w czasie projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3d08a-112">Also see [How to: Create Dialog Boxes at Design Time](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100)).</span></span>  
  
     <span data-ttu-id="3d08a-113">Ponadto, jeśli wybrano styl obramowania dla formularza, który zapewnia opcjonalne przyciski **Minimalizuj** i **Maksymalizuj** , można określić, czy chcesz, aby oba przyciski były funkcjonalne.</span><span class="sxs-lookup"><span data-stu-id="3d08a-113">Additionally, if you have chosen a border style for the form that provides optional **Minimize** and **Maximize** buttons, you can specify whether you want either or both of these buttons to be functional.</span></span> <span data-ttu-id="3d08a-114">Te przyciski są przydatne, gdy chcesz ściśle kontrolować środowisko użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3d08a-114">These buttons are useful when you want to closely control the user experience.</span></span> <span data-ttu-id="3d08a-115">Przyciski **Minimalizuj** i **Maksymalizuj** są domyślnie włączone, a ich funkcje są manipulowane za pomocą okna **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="3d08a-115">The **Minimize** and **Maximize** buttons are enabled by default, and their functionality is manipulated through the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d08a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d08a-116">See also</span></span>

- <xref:System.Windows.Forms.FormBorderStyle>
- <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>
- [<span data-ttu-id="3d08a-117">Wprowadzenie do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3d08a-117">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
