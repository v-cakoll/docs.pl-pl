---
title: Właściwość domyślna „<propertyname1>" powoduje konflikt z właściwością domyślną „<propertyname2>” w „<classname>" i dlatego należy ją zadeklarować jako „Shadows”
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: ab45278b2e1199282e3066c34828b9bda716e162
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813174"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a><span data-ttu-id="6861e-102">Właściwość domyślna "\<propertyname1 >" powoduje konflikt z właściwością domyślną "\<NazwaWłaściwości2 >' w '\<nazwa_klasy >" i dlatego powinien być zadeklarowany jako "Shadows"</span><span class="sxs-lookup"><span data-stu-id="6861e-102">Default property '\<propertyname1>' conflicts with default property '\<propertyname2>' in '\<classname>' and so should be declared 'Shadows'</span></span>
<span data-ttu-id="6861e-103">Właściwość jest zadeklarowany z taką samą nazwę jak właściwość zdefiniowana w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="6861e-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="6861e-104">W takiej sytuacji właściwości tej klasy należy w tle właściwości klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="6861e-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="6861e-105">Ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="6861e-105">This message is a warning.</span></span> <span data-ttu-id="6861e-106">`Shadows` zakłada, że domyślnie.</span><span class="sxs-lookup"><span data-stu-id="6861e-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="6861e-107">Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6861e-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="6861e-108">**Identyfikator błędu:** BC40007</span><span class="sxs-lookup"><span data-stu-id="6861e-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6861e-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6861e-109">To correct this error</span></span>  
  
-   <span data-ttu-id="6861e-110">Dodaj `Shadows` — słowo kluczowe do deklaracji lub zmień nazwę właściwości został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="6861e-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6861e-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6861e-111">See also</span></span>

- [<span data-ttu-id="6861e-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="6861e-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="6861e-113">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6861e-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
