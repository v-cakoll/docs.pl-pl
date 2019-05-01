---
title: Unicode (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: b3c9452f8d144fb18ea3efcb35b85caed80e8692
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778680"
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="b3d09-102">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3d09-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="b3d09-103">Określa, że Visual Basic powinien kierować wszystkie ciągi jako wartości Unicode, niezależnie od nazwy procedury zewnętrznego został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="b3d09-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="b3d09-104">Po wywołaniu procedury zdefiniowane poza projektem, kompilator Visual Basic nie ma dostępu do informacji, że musi mieć, aby prawidłowo wywołać procedurę.</span><span class="sxs-lookup"><span data-stu-id="b3d09-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="b3d09-105">Informacje te obejmują, gdzie znajduje się procedura, sposób jego identyfikacji, jego sekwencja wywoływania i zwracany typ i zestaw znaków ciągu, od go używa.</span><span class="sxs-lookup"><span data-stu-id="b3d09-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="b3d09-106">[Instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i dostarcza to informacje niezbędne.</span><span class="sxs-lookup"><span data-stu-id="b3d09-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="b3d09-107">`charsetmodifier` Wchodzi w skład w `Declare` instrukcji dostarcza informacji zestawu znaków na przeprowadzanie marshalingu ciągów podczas wywoływania procedury zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="b3d09-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="b3d09-108">Ma to również wpływ jak języka Visual Basic poszukuje zewnętrznego pliku, aby uzyskać nazwę procedury zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="b3d09-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="b3d09-109">`Unicode` Modyfikator Określa, że Visual Basic powinien kierować wszystkie ciągi jako wartości Unicode i sprawdzić procedurę bez modyfikowania jej nazwy podczas wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="b3d09-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="b3d09-110">Jeśli określono nie modyfikator zestawu znaków, `Ansi` jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="b3d09-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3d09-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b3d09-111">Remarks</span></span>  
 <span data-ttu-id="b3d09-112">`Unicode` Modyfikatora można używać w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="b3d09-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="b3d09-113">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b3d09-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="b3d09-114">Uwagi dla deweloperów urządzeń inteligentnych</span><span class="sxs-lookup"><span data-stu-id="b3d09-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="b3d09-115">This — słowo kluczowe nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b3d09-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3d09-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3d09-116">See also</span></span>

- [<span data-ttu-id="b3d09-117">Ansi</span><span class="sxs-lookup"><span data-stu-id="b3d09-117">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="b3d09-118">Auto</span><span class="sxs-lookup"><span data-stu-id="b3d09-118">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)
- [<span data-ttu-id="b3d09-119">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="b3d09-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
