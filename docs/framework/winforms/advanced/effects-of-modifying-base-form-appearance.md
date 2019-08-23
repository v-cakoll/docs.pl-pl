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
ms.openlocfilehash: b24bd2db564c7acb0a748c47095ee0777ea1eb88
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955146"
---
# <a name="effects-of-modifying-a-base-forms-appearance"></a><span data-ttu-id="fa00d-102">Efekty modyfikowania wyglądu formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="fa00d-102">Effects of modifying a base form's appearance</span></span>

<span data-ttu-id="fa00d-103">Podczas opracowywania aplikacji może być konieczna zmiana wyglądu formularza podstawowego, z którego są dziedziczone inne formularze w projekcie (lub w innych projektach).</span><span class="sxs-lookup"><span data-stu-id="fa00d-103">During application development, you may often need to change the appearance of the base form from which other forms in the project (or in other projects) are inheriting.</span></span>

<span data-ttu-id="fa00d-104">W czasie projektowania zmiany w wyglądzie formularza podstawowego (są to ustawienia właściwości, a Dodawanie i odejmowanie kontrolek) są odzwierciedlone w formularzach dziedziczonych po skompilowaniu projektu zawierającego formularz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="fa00d-104">At design time, changes to the base form's appearance (be it the setting of properties or the addition and subtraction of controls) are reflected on inherited forms when the project containing the base form is built.</span></span> <span data-ttu-id="fa00d-105">Po prostu zapisanie zmian w formularzu podstawowym nie jest wystarczające.</span><span class="sxs-lookup"><span data-stu-id="fa00d-105">It is not sufficient for you to simply save the changes to the base form.</span></span> <span data-ttu-id="fa00d-106">Aby skompilować projekt, wybierz opcję **Kompiluj** z menu **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="fa00d-106">To build a project, choose **Build** from the **Build** menu.</span></span>

<span data-ttu-id="fa00d-107">Modyfikacje wprowadzone w formularzu podstawowym w czasie wykonywania nie mają wpływu na dziedziczone formularze, które zostały już utworzone.</span><span class="sxs-lookup"><span data-stu-id="fa00d-107">Modifications made to the base form at run time have no affect on inherited forms that are already instantiated.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa00d-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa00d-108">See also</span></span>

- [<span data-ttu-id="fa00d-109">base</span><span class="sxs-lookup"><span data-stu-id="fa00d-109">base</span></span>](../../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="fa00d-110">Instrukcje: Dziedzicz Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fa00d-110">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
- [<span data-ttu-id="fa00d-111">Formularze Windows Forms — dziedziczenie wizualizacji</span><span class="sxs-lookup"><span data-stu-id="fa00d-111">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
