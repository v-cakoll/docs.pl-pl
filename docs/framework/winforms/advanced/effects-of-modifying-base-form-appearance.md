---
title: Efekty modyfikowania formularza podstawowego&#39;wygląd
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms [Windows Forms]
- inherited forms [Windows Forms], modifications to base form
- Windows Forms, base form appearance
- base forms
- inheritance [Windows Forms], forms
ms.assetid: 1c3f2b29-a05c-4c6f-aa1a-4e66b94f343a
ms.openlocfilehash: adaf9224fd340c6ea4342e2591806a7c877e83ff
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43746175"
---
# <a name="effects-of-modifying-a-base-form39s-appearance"></a><span data-ttu-id="c967e-102">Efekty modyfikowania formularza podstawowego&#39;wygląd</span><span class="sxs-lookup"><span data-stu-id="c967e-102">Effects of Modifying a Base Form&#39;s Appearance</span></span>
<span data-ttu-id="c967e-103">Podczas opracowywania aplikacji często konieczne może być zmiana wyglądu formularza podstawowego, z której dziedziczą inne formy w projekcie (lub w innych projektach).</span><span class="sxs-lookup"><span data-stu-id="c967e-103">During application development, you may often need to change the appearance of the base form from which other forms in the project (or in other projects) are inheriting.</span></span>  
  
 <span data-ttu-id="c967e-104">W czasie projektowania, zmienia się na wygląd formularza podstawowego (jest to ustawienie właściwości lub dodawania i odejmowania formantów) są odzwierciedlane na odziedziczone formularze, podczas kompilowania projektu zawierającego formularz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="c967e-104">At design time, changes to the base form's appearance (be it the setting of properties or the addition and subtraction of controls) are reflected on inherited forms when the project containing the base form is built.</span></span> <span data-ttu-id="c967e-105">Nie jest wystarczające, umożliwiające po prostu zapisać zmiany w podstawowej postaci.</span><span class="sxs-lookup"><span data-stu-id="c967e-105">It is not sufficient for you to simply save the changes to the base form.</span></span> <span data-ttu-id="c967e-106">Aby utworzyć projekt, wybierz **kompilacji** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="c967e-106">To build a project, choose **Build** from the **Build** menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c967e-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="c967e-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c967e-108">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="c967e-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c967e-109">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="c967e-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
 <span data-ttu-id="c967e-110">Modyfikacje wprowadzone do formularza podstawowego w czasie wykonywania mają nie będzie miała wpływu na odziedziczone formularze, które już są tworzone.</span><span class="sxs-lookup"><span data-stu-id="c967e-110">Modifications made to the base form at run time have no affect on inherited forms that are already instantiated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c967e-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c967e-111">See Also</span></span>  
 [<span data-ttu-id="c967e-112">base</span><span class="sxs-lookup"><span data-stu-id="c967e-112">base</span></span>](~/docs/csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="c967e-113">Instrukcje: dziedziczenie formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c967e-113">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [<span data-ttu-id="c967e-114">Formularze Windows Forms — dziedziczenie wizualizacji</span><span class="sxs-lookup"><span data-stu-id="c967e-114">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
