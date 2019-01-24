---
title: Auto (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: c128ab9982ae7ccd5fff34020f2750f703da16a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664606"
---
# <a name="auto-visual-basic"></a><span data-ttu-id="90ef3-102">Auto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90ef3-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="90ef3-103">Określa, że Visual Basic powinien kierować ciągi zgodnie z regułami programu .NET Framework, na podstawie nazwy zewnętrznej procedury zewnętrznego został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="90ef3-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="90ef3-104">Po wywołaniu procedury zdefiniowane poza projektem, kompilator Visual Basic nie ma dostępu do informacji, muszą mieć próby wywołania tej procedury poprawnie.</span><span class="sxs-lookup"><span data-stu-id="90ef3-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="90ef3-105">Informacje te obejmują, gdzie znajduje się procedura, sposób jego identyfikacji, jego sekwencja wywoływania i zwracany typ i zestaw znaków ciągu, od go używa.</span><span class="sxs-lookup"><span data-stu-id="90ef3-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="90ef3-106">[Instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i dostarcza to informacje niezbędne.</span><span class="sxs-lookup"><span data-stu-id="90ef3-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="90ef3-107">`charsetmodifier` Wchodzi w skład w `Declare` instrukcji dostarcza informacji zestaw znaków dla marshaling ciągów podczas wywoływania procedury zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="90ef3-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="90ef3-108">Ma to również wpływ jak języka Visual Basic poszukuje zewnętrznego pliku, aby uzyskać nazwę procedury zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="90ef3-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="90ef3-109">`Auto` Modyfikator Określa, że Visual Basic powinien kierować ciągi zgodnie z regułami programu .NET Framework i, należy określić, podstawowego znak zestawu usługi platformy uruchomieniowej i możliwie zmodyfikować nazwę procedury zewnętrznej, jeśli początkowe wyszukiwanie kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="90ef3-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="90ef3-110">Aby uzyskać więcej informacji, zobacz "Zestawach znaków" w [instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="90ef3-110">For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="90ef3-111">Jeśli określono nie modyfikator zestawu znaków, `Ansi` jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="90ef3-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90ef3-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="90ef3-112">Remarks</span></span>  
 <span data-ttu-id="90ef3-113">`Auto` Modyfikatora można używać w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="90ef3-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="90ef3-114">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="90ef3-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="90ef3-115">Uwagi dla deweloperów urządzeń inteligentnych</span><span class="sxs-lookup"><span data-stu-id="90ef3-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="90ef3-116">This — słowo kluczowe nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="90ef3-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90ef3-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90ef3-117">See also</span></span>
- [<span data-ttu-id="90ef3-118">Ansi</span><span class="sxs-lookup"><span data-stu-id="90ef3-118">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="90ef3-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="90ef3-119">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)
- [<span data-ttu-id="90ef3-120">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="90ef3-120">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
