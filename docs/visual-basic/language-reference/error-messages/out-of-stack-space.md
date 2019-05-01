---
title: Za mało miejsca na stosie (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 29dbdf74808fc98bb856483c3fd8e3a09a72113b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925583"
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="610a6-102">Za mało miejsca na stosie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="610a6-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="610a6-103">Stos jest pracy obszaru pamięci, która zwiększania lub zmniejszania dynamicznie z zapotrzebowaniem na zasoby wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="610a6-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="610a6-104">Przekroczono limit.</span><span class="sxs-lookup"><span data-stu-id="610a6-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="610a6-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="610a6-105">To correct this error</span></span>  
  
1. <span data-ttu-id="610a6-106">Sprawdź, czy procedury nie są zagnieżdżone zbyt głęboko.</span><span class="sxs-lookup"><span data-stu-id="610a6-106">Check that procedures are not nested too deeply.</span></span>  
  
2. <span data-ttu-id="610a6-107">Upewnij się, że procedury rekurencyjne kończą się poprawnie.</span><span class="sxs-lookup"><span data-stu-id="610a6-107">Make sure recursive procedures terminate properly.</span></span>  
  
3. <span data-ttu-id="610a6-108">Jeśli zmienne lokalne wymagają lokalnej zmiennej miejsca niż dostępna, spróbuj deklarowanie niektóre zmienne na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="610a6-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="610a6-109">Można również zadeklarować wszystkie zmienne w procedurze statyczne poprzedzając `Property`, `Sub`, lub `Function` — słowo kluczowe z `Static`.</span><span class="sxs-lookup"><span data-stu-id="610a6-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="610a6-110">Możesz też `Static` instrukcję, aby zadeklarować poszczególnych zmiennych statycznych w ramach procedur.</span><span class="sxs-lookup"><span data-stu-id="610a6-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4. <span data-ttu-id="610a6-111">Niektóre z Twoimi ciągami o stałej długości, jako ciągi o zmiennej długości przedefiniować jako ciągi o stałej długości Użyj więcej miejsca na stosie niż ciągi o zmiennej długości.</span><span class="sxs-lookup"><span data-stu-id="610a6-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="610a6-112">Można również zdefiniować ciąg na poziomie modułu wymagającym nie obszar stosu.</span><span class="sxs-lookup"><span data-stu-id="610a6-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5. <span data-ttu-id="610a6-113">Sprawdź liczbę zagnieżdżonych `DoEvents` funkcję wywołania, przy użyciu `Calls` okno dialogowe do widoku, które procedury są aktywne na stosie.</span><span class="sxs-lookup"><span data-stu-id="610a6-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6. <span data-ttu-id="610a6-114">Upewnij się, że nie był przyczyną "cascade zdarzeń", wyzwalając zdarzenie, które wywołuje procedury zdarzenia już na stosie.</span><span class="sxs-lookup"><span data-stu-id="610a6-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="610a6-115">Kaskadowe zdarzeń jest podobny do niezakończony cykliczne wywołanie procedury, ale jest mniej oczywistych, ponieważ jest nawiązywane połączenie, zamiast jawnego wywołania w kodzie języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="610a6-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span></span> <span data-ttu-id="610a6-116">Użyj `Calls` okno dialogowe do widoku, które procedury są aktywne na stosie.</span><span class="sxs-lookup"><span data-stu-id="610a6-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="610a6-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="610a6-117">See also</span></span>

- [<span data-ttu-id="610a6-118">Okna pamięci</span><span class="sxs-lookup"><span data-stu-id="610a6-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)
