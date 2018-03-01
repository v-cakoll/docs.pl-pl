---
title: Ansi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aa5724eb9123b2776c3a579e4244c55b3129816b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="ba9e6-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba9e6-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="ba9e6-103">Określa, że Visual Basic powinien kierować wszystkie ciągi jako wartości American National Standards Institute (ANSI) niezależnie od tego, nazwę procedury zewnętrznej, został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="ba9e6-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="ba9e6-104">Po wywołaniu procedury zdefiniowany poza projektem, kompilator Visual Basic nie ma dostępu do informacji wymaganych do wywołania tej procedury poprawnie.</span><span class="sxs-lookup"><span data-stu-id="ba9e6-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="ba9e6-105">Informacje te obejmują lokalizacji procedurą, jak określono, jego sekwencja wywoływania oraz zwracany typ i ciąg znaków ustaw go używa.</span><span class="sxs-lookup"><span data-stu-id="ba9e6-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="ba9e6-106">[Instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i przekazywać te informacje niezbędne.</span><span class="sxs-lookup"><span data-stu-id="ba9e6-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="ba9e6-107">`charsetmodifier` Części w `Declare` instrukcji dostarcza informacji zestaw znaków dla organizowanie ciągów podczas wywoływania procedury zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="ba9e6-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="ba9e6-108">Wpływa to również na jak Visual Basic wyszukuje plik zewnętrznych dla nazwę procedury zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="ba9e6-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="ba9e6-109">`Ansi` Modyfikator Określa, że Visual Basic powinien kierować wszystkie ciągi jako wartości ANSI i sprawdzić procedurę bez modyfikowania jej nazwy podczas wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="ba9e6-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="ba9e6-110">Jeśli określono nie modyfikator zestawu znaków, `Ansi` jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="ba9e6-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba9e6-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ba9e6-111">Remarks</span></span>  
 <span data-ttu-id="ba9e6-112">`Ansi` Modyfikatora można używać w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="ba9e6-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="ba9e6-113">DECLARE — instrukcja</span><span class="sxs-lookup"><span data-stu-id="ba9e6-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="ba9e6-114">Uwagi dla deweloperów inteligentnych urządzeń</span><span class="sxs-lookup"><span data-stu-id="ba9e6-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="ba9e6-115">To słowo kluczowe nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ba9e6-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba9e6-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ba9e6-116">See Also</span></span>  
 [<span data-ttu-id="ba9e6-117">Automatycznie</span><span class="sxs-lookup"><span data-stu-id="ba9e6-117">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)  
 [<span data-ttu-id="ba9e6-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="ba9e6-118">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [<span data-ttu-id="ba9e6-119">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="ba9e6-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
