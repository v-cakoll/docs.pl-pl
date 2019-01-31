---
title: Efekty modyfikowania wyglądu formularza podstawowego
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms [Windows Forms]
- inherited forms [Windows Forms], modifications to base form
- Windows Forms, base form appearance
- base forms
- inheritance [Windows Forms], forms
ms.assetid: 1c3f2b29-a05c-4c6f-aa1a-4e66b94f343a
ms.openlocfilehash: fc0edaa8ca115a09eb6d8382a12d9a7c0c0db7f6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260167"
---
# <a name="effects-of-modifying-a-base-forms-appearance"></a><span data-ttu-id="13b5b-102">Efekty modyfikowania wyglądu formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="13b5b-102">Effects of Modifying a Base Form's Appearance</span></span>
<span data-ttu-id="13b5b-103">Podczas opracowywania aplikacji często konieczne może być zmiana wyglądu formularza podstawowego, z której dziedziczą inne formy w projekcie (lub w innych projektach).</span><span class="sxs-lookup"><span data-stu-id="13b5b-103">During application development, you may often need to change the appearance of the base form from which other forms in the project (or in other projects) are inheriting.</span></span>  
  
 <span data-ttu-id="13b5b-104">W czasie projektowania, zmienia się na wygląd formularza podstawowego (jest to ustawienie właściwości lub dodawania i odejmowania formantów) są odzwierciedlane na odziedziczone formularze, podczas kompilowania projektu zawierającego formularz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="13b5b-104">At design time, changes to the base form's appearance (be it the setting of properties or the addition and subtraction of controls) are reflected on inherited forms when the project containing the base form is built.</span></span> <span data-ttu-id="13b5b-105">Nie jest wystarczające, umożliwiające po prostu zapisać zmiany w podstawowej postaci.</span><span class="sxs-lookup"><span data-stu-id="13b5b-105">It is not sufficient for you to simply save the changes to the base form.</span></span> <span data-ttu-id="13b5b-106">Aby utworzyć projekt, wybierz **kompilacji** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="13b5b-106">To build a project, choose **Build** from the **Build** menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13b5b-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="13b5b-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="13b5b-108">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="13b5b-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="13b5b-109">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="13b5b-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
 <span data-ttu-id="13b5b-110">Modyfikacje wprowadzone do formularza podstawowego w czasie wykonywania mają nie będzie miała wpływu na odziedziczone formularze, które już są tworzone.</span><span class="sxs-lookup"><span data-stu-id="13b5b-110">Modifications made to the base form at run time have no affect on inherited forms that are already instantiated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13b5b-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13b5b-111">See also</span></span>
- [<span data-ttu-id="13b5b-112">base</span><span class="sxs-lookup"><span data-stu-id="13b5b-112">base</span></span>](~/docs/csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="13b5b-113">Instrukcje: Dziedziczenie formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="13b5b-113">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)
- [<span data-ttu-id="13b5b-114">Formularze Windows Forms — dziedziczenie wizualizacji</span><span class="sxs-lookup"><span data-stu-id="13b5b-114">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
