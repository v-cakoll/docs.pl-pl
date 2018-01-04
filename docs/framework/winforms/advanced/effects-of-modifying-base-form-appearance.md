---
title: "Efekty modyfikowania formularza podstawowego &#39; wygląd s"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parent forms [Windows Forms]
- inherited forms [Windows Forms], modifications to base form
- Windows Forms, base form appearance
- base forms
- inheritance [Windows Forms], forms
ms.assetid: 1c3f2b29-a05c-4c6f-aa1a-4e66b94f343a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b808d10cd393d84ed29cb5e1cccfcff9c6c098d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="effects-of-modifying-a-base-form39s-appearance"></a><span data-ttu-id="cc12d-102">Efekty modyfikowania formularza podstawowego &#39; wygląd s</span><span class="sxs-lookup"><span data-stu-id="cc12d-102">Effects of Modifying a Base Form&#39;s Appearance</span></span>
<span data-ttu-id="cc12d-103">Podczas tworzenia aplikacji, może być często konieczne zmienianie wyglądu formularza podstawowego, z którego są dziedziczone innych formularzy w projekcie (lub w innych projektów).</span><span class="sxs-lookup"><span data-stu-id="cc12d-103">During application development, you may often need to change the appearance of the base form from which other forms in the project (or in other projects) are inheriting.</span></span>  
  
 <span data-ttu-id="cc12d-104">W czasie projektowania, zmienia się na wygląd formularza podstawowego (jest to ustawienie właściwości lub dodawania i odejmowania formantów) są uwzględniane w formularzach dziedziczone po utworzeniu projektu zawierającego formularza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="cc12d-104">At design time, changes to the base form's appearance (be it the setting of properties or the addition and subtraction of controls) are reflected on inherited forms when the project containing the base form is built.</span></span> <span data-ttu-id="cc12d-105">Nie jest wystarczające po prostu zapisać zmiany w podstawowej postaci.</span><span class="sxs-lookup"><span data-stu-id="cc12d-105">It is not sufficient for you to simply save the changes to the base form.</span></span> <span data-ttu-id="cc12d-106">Aby utworzyć projekt, wybierz **kompilacji** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="cc12d-106">To build a project, choose **Build** from the **Build** menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc12d-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="cc12d-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="cc12d-108">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="cc12d-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="cc12d-109">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="cc12d-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
 <span data-ttu-id="cc12d-110">Modyfikacje formularza podstawowego w czasie wykonywania ma nie wpływa na odziedziczone formularze, które zostały już utworzone.</span><span class="sxs-lookup"><span data-stu-id="cc12d-110">Modifications made to the base form at run time have no affect on inherited forms that are already instantiated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc12d-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc12d-111">See Also</span></span>  
 [<span data-ttu-id="cc12d-112">base</span><span class="sxs-lookup"><span data-stu-id="cc12d-112">base</span></span>](~/docs/csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="cc12d-113">Instrukcje: dziedziczenie formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc12d-113">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [<span data-ttu-id="cc12d-114">Formularze Windows Forms — dziedziczenie wizualizacji</span><span class="sxs-lookup"><span data-stu-id="cc12d-114">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
