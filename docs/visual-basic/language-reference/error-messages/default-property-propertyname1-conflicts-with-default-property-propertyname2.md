---
title: Właściwość domyślna „<propertyname1>" powoduje konflikt z właściwością domyślną „<propertyname2>” w „<classname>" i dlatego należy ją zadeklarować jako „Shadows”
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: c964003217e7b96cf25288e2ae6ae6a2fb07a6c3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651378"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a><span data-ttu-id="c711a-102">Właściwość domyślna "\<propertyname1 >" powoduje konflikt z właściwością domyślną "\<NazwaWłaściwości2 >' w '\<nazwa_klasy >" i dlatego powinien być zadeklarowany jako "Shadows"</span><span class="sxs-lookup"><span data-stu-id="c711a-102">Default property '\<propertyname1>' conflicts with default property '\<propertyname2>' in '\<classname>' and so should be declared 'Shadows'</span></span>
<span data-ttu-id="c711a-103">Właściwość jest zadeklarowany z taką samą nazwę jak właściwość zdefiniowana w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="c711a-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="c711a-104">W takiej sytuacji właściwości tej klasy należy w tle właściwości klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="c711a-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="c711a-105">Ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="c711a-105">This message is a warning.</span></span> <span data-ttu-id="c711a-106">`Shadows` zakłada, że domyślnie.</span><span class="sxs-lookup"><span data-stu-id="c711a-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="c711a-107">Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c711a-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c711a-108">**Identyfikator błędu:** BC40007</span><span class="sxs-lookup"><span data-stu-id="c711a-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c711a-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c711a-109">To correct this error</span></span>  
  
- <span data-ttu-id="c711a-110">Dodaj `Shadows` — słowo kluczowe do deklaracji lub zmień nazwę właściwości został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="c711a-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c711a-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c711a-111">See also</span></span>

- [<span data-ttu-id="c711a-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="c711a-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="c711a-113">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c711a-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
