---
title: Właściwość domyślna &#39; &lt;propertyname1&gt; &#39; powoduje konflikt z właściwością domyślną &#39; &lt;NazwaWłaściwości2&gt; &#39; w &#39; &lt;classname&gt; &#39;i dlatego powinien być zadeklarowany jako &#39;cieni&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 3099467fa3c5a162c13c9235fb8d55375953ba3a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521429"
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a><span data-ttu-id="b2d60-102">Właściwość domyślna &#39; &lt;propertyname1&gt; &#39; powoduje konflikt z właściwością domyślną &#39; &lt;NazwaWłaściwości2&gt; &#39; w &#39; &lt;classname&gt; &#39;i dlatego powinien być zadeklarowany jako &#39;cieni&#39;</span><span class="sxs-lookup"><span data-stu-id="b2d60-102">Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;</span></span>
<span data-ttu-id="b2d60-103">Właściwość jest zadeklarowany z taką samą nazwę jak właściwość zdefiniowana w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="b2d60-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="b2d60-104">W takiej sytuacji właściwości tej klasy należy w tle właściwości klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="b2d60-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="b2d60-105">Ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="b2d60-105">This message is a warning.</span></span> <span data-ttu-id="b2d60-106">`Shadows` zakłada, że domyślnie.</span><span class="sxs-lookup"><span data-stu-id="b2d60-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="b2d60-107">Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b2d60-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="b2d60-108">**Identyfikator błędu:** BC40007</span><span class="sxs-lookup"><span data-stu-id="b2d60-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b2d60-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b2d60-109">To correct this error</span></span>  
  
-   <span data-ttu-id="b2d60-110">Dodaj `Shadows` — słowo kluczowe do deklaracji lub zmień nazwę właściwości został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="b2d60-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2d60-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2d60-111">See also</span></span>
- [<span data-ttu-id="b2d60-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="b2d60-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="b2d60-113">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b2d60-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
