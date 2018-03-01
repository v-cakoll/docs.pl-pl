---
title: Unicode (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 042908b8427de2de0de96bbb32df7be018bb915c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="f0f6e-102">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0f6e-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="f0f6e-103">Określa, że Visual Basic powinien kierować wszystkie ciągi jako wartości Unicode, niezależnie od tego, nazwę procedury zewnętrznej, został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="f0f6e-104">Po wywołaniu procedury zdefiniowany poza projektem, kompilator Visual Basic nie ma dostępu do informacji musi mieć w celu wywołania tej procedury poprawnie.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="f0f6e-105">Informacje te obejmują lokalizacji procedurą, jak określono, jego sekwencja wywoływania oraz zwracany typ i ciąg znaków ustaw go używa.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="f0f6e-106">[Instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i przekazywać te informacje niezbędne.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="f0f6e-107">`charsetmodifier` Części w `Declare` instrukcji dostarcza informacje zestaw znaków kierowanie ciągów podczas wywoływania procedury zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="f0f6e-108">Wpływa to również na jak Visual Basic wyszukuje plik zewnętrznych dla nazwę procedury zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="f0f6e-109">`Unicode` Modyfikator Określa, że Visual Basic powinien kierować wszystkie ciągi jako wartości Unicode i sprawdzić procedurę bez modyfikowania jej nazwy podczas wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="f0f6e-110">Jeśli określono nie modyfikator zestawu znaków, `Ansi` jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0f6e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0f6e-111">Remarks</span></span>  
 <span data-ttu-id="f0f6e-112">`Unicode` Modyfikatora można używać w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="f0f6e-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="f0f6e-113">DECLARE — instrukcja</span><span class="sxs-lookup"><span data-stu-id="f0f6e-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="f0f6e-114">Uwagi dla deweloperów inteligentnych urządzeń</span><span class="sxs-lookup"><span data-stu-id="f0f6e-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="f0f6e-115">To słowo kluczowe nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f6e-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f0f6e-116">See Also</span></span>  
 [<span data-ttu-id="f0f6e-117">ANSI</span><span class="sxs-lookup"><span data-stu-id="f0f6e-117">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [<span data-ttu-id="f0f6e-118">Automatycznie</span><span class="sxs-lookup"><span data-stu-id="f0f6e-118">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)  
 [<span data-ttu-id="f0f6e-119">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="f0f6e-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
