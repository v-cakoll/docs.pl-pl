---
title: Ansi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: c7037acac58de56a396bd89f595ef897743ff4e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="afe7b-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afe7b-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="afe7b-103">Określa, że Visual Basic powinien kierować wszystkie ciągi jako wartości American National Standards Institute (ANSI) niezależnie od tego, nazwę procedury zewnętrznej, został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="afe7b-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="afe7b-104">Po wywołaniu procedury zdefiniowany poza projektem, kompilator Visual Basic nie ma dostępu do informacji wymaganych do wywołania tej procedury poprawnie.</span><span class="sxs-lookup"><span data-stu-id="afe7b-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="afe7b-105">Informacje te obejmują lokalizacji procedurą, jak określono, jego sekwencja wywoływania oraz zwracany typ i ciąg znaków ustaw go używa.</span><span class="sxs-lookup"><span data-stu-id="afe7b-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="afe7b-106">[Instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i przekazywać te informacje niezbędne.</span><span class="sxs-lookup"><span data-stu-id="afe7b-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="afe7b-107">`charsetmodifier` Części w `Declare` instrukcji dostarcza informacji zestaw znaków dla organizowanie ciągów podczas wywoływania procedury zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="afe7b-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="afe7b-108">Wpływa to również na jak Visual Basic wyszukuje plik zewnętrznych dla nazwę procedury zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="afe7b-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="afe7b-109">`Ansi` Modyfikator Określa, że Visual Basic powinien kierować wszystkie ciągi jako wartości ANSI i sprawdzić procedurę bez modyfikowania jej nazwy podczas wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="afe7b-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="afe7b-110">Jeśli określono nie modyfikator zestawu znaków, `Ansi` jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="afe7b-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afe7b-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="afe7b-111">Remarks</span></span>  
 <span data-ttu-id="afe7b-112">`Ansi` Modyfikatora można używać w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="afe7b-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="afe7b-113">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="afe7b-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="afe7b-114">Uwagi dla deweloperów inteligentnych urządzeń</span><span class="sxs-lookup"><span data-stu-id="afe7b-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="afe7b-115">To słowo kluczowe nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="afe7b-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afe7b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afe7b-116">See Also</span></span>  
 [<span data-ttu-id="afe7b-117">Auto</span><span class="sxs-lookup"><span data-stu-id="afe7b-117">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)  
 [<span data-ttu-id="afe7b-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="afe7b-118">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [<span data-ttu-id="afe7b-119">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="afe7b-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
