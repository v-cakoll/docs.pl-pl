---
title: "&#39; Pobierz &#39; Akcesor właściwości &#39; &lt;propertyname&gt;&#39; nie jest dostępny"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords: BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 167e040570af1fc78ce48f5e930e54981ba909ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39get39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a><span data-ttu-id="1d51b-102">&#39; Pobierz &#39; Akcesor właściwości &#39; &lt;propertyname&gt;&#39; nie jest dostępny</span><span class="sxs-lookup"><span data-stu-id="1d51b-102">&#39;Get&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible</span></span>
<span data-ttu-id="1d51b-103">Instrukcję próbuje pobrać wartość właściwości, gdy nie ma dostępu do właściwości `Get` procedury.</span><span class="sxs-lookup"><span data-stu-id="1d51b-103">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>  
  
 <span data-ttu-id="1d51b-104">Jeśli [instrukcja Get](../../../visual-basic/language-reference/statements/get-statement.md) jest oznaczony atrybutem bardziej restrykcyjnego dostępu niż poziom jego [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md), próba odczytu wartości właściwości może zakończyć się niepowodzeniem w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="1d51b-104">If the [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>  
  
-   <span data-ttu-id="1d51b-105">`Get` Instrukcji jest oznaczony jako [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) i kod wywołujący znajduje się poza klasy lub struktury, w którym właściwość jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="1d51b-105">The `Get` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
-   <span data-ttu-id="1d51b-106">`Get` Instrukcji jest oznaczony jako [chronione](../../../visual-basic/language-reference/modifiers/protected.md) i kod wywołujący nie w klasy lub struktury, w którym jest zdefiniowana właściwość ani w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="1d51b-106">The `Get` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
-   <span data-ttu-id="1d51b-107">`Get` Instrukcji jest oznaczony jako [Friend](../../../visual-basic/language-reference/modifiers/friend.md) i kod wywołujący nie jest w tym samym zestawie, w którym właściwość jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="1d51b-107">The `Get` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="1d51b-108">**Identyfikator błędu:** BC31103</span><span class="sxs-lookup"><span data-stu-id="1d51b-108">**Error ID:** BC31103</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1d51b-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="1d51b-109">To correct this error</span></span>  
  
-   <span data-ttu-id="1d51b-110">Jeśli masz kontroli kodu źródłowego Definiowanie właściwości, zaleca się zadeklarowanie `Get` procedurę za pomocą tego samego poziomu dostępu, co samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="1d51b-110">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>  
  
-   <span data-ttu-id="1d51b-111">Jeśli nie masz kontroli kodu źródłowego Definiowanie właściwości lub należy ograniczyć `Get` procedury więcej niż właściwość, spróbuj przenieść instrukcji, która odczytuje wartość właściwości region kodu, który ma lepszy dostęp do poziomu dostępu Właściwość.</span><span class="sxs-lookup"><span data-stu-id="1d51b-111">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d51b-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d51b-112">See Also</span></span>  
 [<span data-ttu-id="1d51b-113">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="1d51b-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="1d51b-114">Porady: deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="1d51b-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
