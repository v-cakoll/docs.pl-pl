---
title: "Domyślne właściwości &#39; &lt;propertyname1&gt;&#39; powoduje konflikt z właściwością domyślną &#39;&lt; NazwaWłaściwości2&gt;&#39; w &#39;&lt; ClassName&gt;&#39; i dlatego powinien być zadeklarowany jako &#39; Shadows &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af92c06f6d07b6ea64a05b9043547a46e3679111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a><span data-ttu-id="d1828-102">Domyślne właściwości &#39; &lt;propertyname1&gt;&#39; powoduje konflikt z właściwością domyślną &#39;&lt; NazwaWłaściwości2&gt;&#39; w &#39;&lt; ClassName&gt;&#39; i dlatego powinien być zadeklarowany jako &#39; Shadows &#39;</span><span class="sxs-lookup"><span data-stu-id="d1828-102">Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;</span></span>
<span data-ttu-id="d1828-103">Właściwość zadeklarowana z taką samą nazwę jak właściwość zdefiniowaną w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="d1828-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="d1828-104">W takiej sytuacji właściwości tej klasy należy obserwować właściwości klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="d1828-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="d1828-105">Ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="d1828-105">This message is a warning.</span></span> <span data-ttu-id="d1828-106">`Shadows`przyjęto, że domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d1828-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="d1828-107">Aby uzyskać więcej informacji na temat ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d1828-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d1828-108">**Identyfikator błędu:** BC40007</span><span class="sxs-lookup"><span data-stu-id="d1828-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d1828-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d1828-109">To correct this error</span></span>  
  
-   <span data-ttu-id="d1828-110">Dodaj `Shadows` — słowo kluczowe do deklaracji lub zmień nazwę właściwości został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="d1828-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1828-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1828-111">See Also</span></span>  
 [<span data-ttu-id="d1828-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="d1828-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="d1828-113">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d1828-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
