---
title: Właściwość domyślna „<propertyname1>" powoduje konflikt z właściwością domyślną „<propertyname2>” w „<classname>" i dlatego należy ją zadeklarować jako „Shadows”
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 37f98ce8120d5861552819690f9d5f22c9959a0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409728"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a><span data-ttu-id="25db0-102">Właściwość domyślna „\<propertyname1>" powoduje konflikt z właściwością domyślną „\<propertyname2>” w „\<classname>" i dlatego należy ją zadeklarować jako „Shadows”</span><span class="sxs-lookup"><span data-stu-id="25db0-102">Default property '\<propertyname1>' conflicts with default property '\<propertyname2>' in '\<classname>' and so should be declared 'Shadows'</span></span>
<span data-ttu-id="25db0-103">Właściwość jest zadeklarowana z taką samą nazwą jak Właściwość zdefiniowana w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="25db0-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="25db0-104">W tej sytuacji właściwość w tej klasie powinna zasłaniać właściwość klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="25db0-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="25db0-105">Ten komunikat jest ostrzeżeniem.</span><span class="sxs-lookup"><span data-stu-id="25db0-105">This message is a warning.</span></span> <span data-ttu-id="25db0-106">`Shadows`jest domyślnie przyjmowana.</span><span class="sxs-lookup"><span data-stu-id="25db0-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="25db0-107">Aby uzyskać więcej informacji na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędów, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="25db0-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="25db0-108">**Identyfikator błędu:** BC40007</span><span class="sxs-lookup"><span data-stu-id="25db0-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="25db0-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="25db0-109">To correct this error</span></span>  
  
- <span data-ttu-id="25db0-110">Dodaj `Shadows` słowo kluczowe do deklaracji lub Zmień nazwę zadeklarowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="25db0-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25db0-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25db0-111">See also</span></span>

- [<span data-ttu-id="25db0-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="25db0-112">Shadows</span></span>](../modifiers/shadows.md)
- [<span data-ttu-id="25db0-113">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25db0-113">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
