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
ms.openlocfilehash: 98dafab3e524ea371bba228eb231e28d46cc3b4e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819458"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="dad54-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dad54-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="dad54-103">Określa, że Visual Basic powinien kierować wszystkie ciągi wartości American National Standards Institute (ANSI), niezależnie od nazwy procedury zewnętrznego został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="dad54-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="dad54-104">Po wywołaniu procedury zdefiniowane poza projektem, kompilator Visual Basic nie ma dostępu do informacji wymaganych do wywołania tej procedury poprawnie.</span><span class="sxs-lookup"><span data-stu-id="dad54-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="dad54-105">Informacje te obejmują, gdzie znajduje się procedura, sposób jego identyfikacji, jego sekwencja wywoływania i zwracany typ i zestaw znaków ciągu, od go używa.</span><span class="sxs-lookup"><span data-stu-id="dad54-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="dad54-106">[Instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i dostarcza to informacje niezbędne.</span><span class="sxs-lookup"><span data-stu-id="dad54-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="dad54-107">`charsetmodifier` Wchodzi w skład w `Declare` instrukcji dostarcza informacji zestaw znaków dla marshaling ciągów podczas wywoływania procedury zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="dad54-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="dad54-108">Ma to również wpływ jak języka Visual Basic poszukuje zewnętrznego pliku, aby uzyskać nazwę procedury zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="dad54-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="dad54-109">`Ansi` Modyfikator Określa, że Visual Basic powinien kierować wszystkie ciągi jako wartości ANSI i sprawdzić procedurę bez modyfikowania jej nazwy podczas wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="dad54-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="dad54-110">Jeśli określono nie modyfikator zestawu znaków, `Ansi` jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="dad54-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dad54-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dad54-111">Remarks</span></span>  
 <span data-ttu-id="dad54-112">`Ansi` Modyfikatora można używać w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="dad54-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="dad54-113">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="dad54-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="dad54-114">Uwagi dla deweloperów urządzeń inteligentnych</span><span class="sxs-lookup"><span data-stu-id="dad54-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="dad54-115">This — słowo kluczowe nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="dad54-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dad54-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dad54-116">See also</span></span>

- [<span data-ttu-id="dad54-117">Auto</span><span class="sxs-lookup"><span data-stu-id="dad54-117">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)
- [<span data-ttu-id="dad54-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="dad54-118">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)
- [<span data-ttu-id="dad54-119">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="dad54-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
