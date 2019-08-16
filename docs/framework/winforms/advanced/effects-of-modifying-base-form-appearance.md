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
ms.openlocfilehash: 5239017eb63ca6360ae8811a76497256fafbd1b1
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040136"
---
# <a name="effects-of-modifying-a-base-forms-appearance"></a><span data-ttu-id="8b443-102">Efekty modyfikowania wyglądu formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="8b443-102">Effects of modifying a base form's appearance</span></span>

<span data-ttu-id="8b443-103">Podczas opracowywania aplikacji może być konieczna zmiana wyglądu formularza podstawowego, z którego są dziedziczone inne formularze w projekcie (lub w innych projektach).</span><span class="sxs-lookup"><span data-stu-id="8b443-103">During application development, you may often need to change the appearance of the base form from which other forms in the project (or in other projects) are inheriting.</span></span>

<span data-ttu-id="8b443-104">W czasie projektowania zmiany w wyglądzie formularza podstawowego (są to ustawienia właściwości, a Dodawanie i odejmowanie kontrolek) są odzwierciedlone w formularzach dziedziczonych po skompilowaniu projektu zawierającego formularz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="8b443-104">At design time, changes to the base form's appearance (be it the setting of properties or the addition and subtraction of controls) are reflected on inherited forms when the project containing the base form is built.</span></span> <span data-ttu-id="8b443-105">Po prostu zapisanie zmian w formularzu podstawowym nie jest wystarczające.</span><span class="sxs-lookup"><span data-stu-id="8b443-105">It is not sufficient for you to simply save the changes to the base form.</span></span> <span data-ttu-id="8b443-106">Aby skompilować projekt, wybierz opcję **Kompiluj** z menu **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="8b443-106">To build a project, choose **Build** from the **Build** menu.</span></span>

<span data-ttu-id="8b443-107">Modyfikacje wprowadzone w formularzu podstawowym w czasie wykonywania nie mają wpływu na dziedziczone formularze, które zostały już utworzone.</span><span class="sxs-lookup"><span data-stu-id="8b443-107">Modifications made to the base form at run time have no affect on inherited forms that are already instantiated.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b443-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b443-108">See also</span></span>

- [<span data-ttu-id="8b443-109">base</span><span class="sxs-lookup"><span data-stu-id="8b443-109">base</span></span>](~/docs/csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="8b443-110">Instrukcje: Dziedzicz Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8b443-110">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
- [<span data-ttu-id="8b443-111">Formularze Windows Forms — dziedziczenie wizualizacji</span><span class="sxs-lookup"><span data-stu-id="8b443-111">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
