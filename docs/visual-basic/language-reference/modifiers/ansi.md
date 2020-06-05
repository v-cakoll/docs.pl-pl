---
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 67792e52c21555bef46548e9ab0a6ebd32061071
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373203"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="8dfe4-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8dfe4-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="8dfe4-103">Określa, że Visual Basic powinny kierować wszystkie ciągi do wartości American National Standards Institute (ANSI), niezależnie od nazwy zadeklarowanej procedury zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="8dfe4-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="8dfe4-104">Po wywołaniu procedury zdefiniowanej poza projektem kompilator Visual Basic nie ma dostępu do informacji potrzebnych do poprawnego wywołania procedury.</span><span class="sxs-lookup"><span data-stu-id="8dfe4-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="8dfe4-105">Informacje te obejmują miejsce, w którym znajduje się procedura, sposób jego identyfikacji, jego sekwencję wywoływania i zwracany typ oraz zestaw znaków użytych w ciągu.</span><span class="sxs-lookup"><span data-stu-id="8dfe4-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="8dfe4-106">[Instrukcja DECLARE](../statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i dostarcza te niezbędne informacje.</span><span class="sxs-lookup"><span data-stu-id="8dfe4-106">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="8dfe4-107">`charsetmodifier`Część w `Declare` instrukcji dostarcza informacje zestawu znaków do organizowania ciągów podczas wywołania procedury zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="8dfe4-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="8dfe4-108">Ma także wpływ na to, w jaki sposób Visual Basic przeszukuje zewnętrzny plik dla nazwy procedury zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="8dfe4-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="8dfe4-109">`Ansi`Modyfikator określa, że Visual Basic powinny kierować wszystkie ciągi do wartości ANSI i należy odszukać procedurę bez modyfikowania jej nazwy podczas wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="8dfe4-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="8dfe4-110">Jeśli nie określono modyfikatora zestawu znaków, `Ansi` jest to ustawienie domyślne.</span><span class="sxs-lookup"><span data-stu-id="8dfe4-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8dfe4-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8dfe4-111">Remarks</span></span>  
 <span data-ttu-id="8dfe4-112">`Ansi`Modyfikator może być używany w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="8dfe4-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="8dfe4-113">Declare — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="8dfe4-113">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="8dfe4-114">Uwagi dla deweloperów inteligentnych urządzeń</span><span class="sxs-lookup"><span data-stu-id="8dfe4-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="8dfe4-115">To słowo kluczowe nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="8dfe4-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dfe4-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dfe4-116">See also</span></span>

- [<span data-ttu-id="8dfe4-117">Automatycznie</span><span class="sxs-lookup"><span data-stu-id="8dfe4-117">Auto</span></span>](auto.md)
- [<span data-ttu-id="8dfe4-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="8dfe4-118">Unicode</span></span>](unicode.md)
- [<span data-ttu-id="8dfe4-119">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="8dfe4-119">Keywords</span></span>](../keywords/index.md)
