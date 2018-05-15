---
title: Parametry opcjonalne (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [Visual Basic], optional
- Visual Basic code, procedures
- procedures [Visual Basic], optional arguments
- optional arguments
- named arguments [Visual Basic], and optional arguments
- optional parameters
- Optional keyword [Visual Basic], optional arguments
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], and named arguments
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
ms.openlocfilehash: a438455668310769c5267a6d42a2e694bb7b01dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="optional-parameters-visual-basic"></a><span data-ttu-id="f47ed-102">Parametry opcjonalne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f47ed-102">Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="f47ed-103">Możesz określić, że parametr procedury jest opcjonalny i nie trzeba do niego przekazywać żadnego argumentu w momencie wywołania procedury.</span><span class="sxs-lookup"><span data-stu-id="f47ed-103">You can specify that a procedure parameter is optional and no argument has to be supplied for it when the procedure is called.</span></span> <span data-ttu-id="f47ed-104">*Parametry opcjonalne* są wskazywane przez `Optional` — słowo kluczowe w definicji procedury.</span><span class="sxs-lookup"><span data-stu-id="f47ed-104">*Optional parameters* are indicated by the `Optional` keyword in the procedure definition.</span></span> <span data-ttu-id="f47ed-105">Mają zastosowanie następujące zasady:</span><span class="sxs-lookup"><span data-stu-id="f47ed-105">The following rules apply:</span></span>  
  
-   <span data-ttu-id="f47ed-106">Każdy parametr opcjonalny w definicji procedury musi określać wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="f47ed-106">Every optional parameter in the procedure definition must specify a default value.</span></span>  
  
-   <span data-ttu-id="f47ed-107">Wartość domyślna dla opcjonalnego parametru musi być wyrażeniem stałym.</span><span class="sxs-lookup"><span data-stu-id="f47ed-107">The default value for an optional parameter must be a constant expression.</span></span>  
  
-   <span data-ttu-id="f47ed-108">Każdy parametr występujący w definicji procedury po opcjonalnym parametrze również musi być opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f47ed-108">Every parameter following an optional parameter in the procedure definition must also be optional.</span></span>  
  
 <span data-ttu-id="f47ed-109">Deklaracja procedury z opcjonalnym parametrem ma następującą składnię:</span><span class="sxs-lookup"><span data-stu-id="f47ed-109">The following syntax shows a procedure declaration with an optional parameter:</span></span>  
  
```vb  
Sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## <a name="calling-procedures-with-optional-parameters"></a><span data-ttu-id="f47ed-110">Wywoływanie procedur z opcjonalnymi parametrami</span><span class="sxs-lookup"><span data-stu-id="f47ed-110">Calling Procedures with Optional Parameters</span></span>  
 <span data-ttu-id="f47ed-111">Gdy wywołujesz procedurę z opcjonalnym parametrem, możesz wybrać, czy podać argument.</span><span class="sxs-lookup"><span data-stu-id="f47ed-111">When you call a procedure with an optional parameter, you can choose whether to supply the argument.</span></span> <span data-ttu-id="f47ed-112">Jeśli tego nie zrobisz, procedura użyje wartości domyślnej zadeklarowanej dla tego parametru.</span><span class="sxs-lookup"><span data-stu-id="f47ed-112">If you do not, the procedure uses the default value declared for that parameter.</span></span>  
  
 <span data-ttu-id="f47ed-113">Jeżeli pomijasz jeden lub więcej argumentów opcjonalnych na liście argumentów, użyj kolejnych średników do oznaczania ich położenia.</span><span class="sxs-lookup"><span data-stu-id="f47ed-113">When you omit one or more optional arguments in the argument list, you use successive commas to mark their positions.</span></span> <span data-ttu-id="f47ed-114">Następujący przykład wywołania dostarcza pierwszy i czwarty argument, a pomija drugi i trzeci:</span><span class="sxs-lookup"><span data-stu-id="f47ed-114">The following example call supplies the first and fourth arguments but not the second or third:</span></span>  
  
```vb  
Sub name(argument 1, , , argument 4)  
```  
  
 <span data-ttu-id="f47ed-115">Poniższy przykład powoduje, że wiele wywołań `MsgBox` funkcji.</span><span class="sxs-lookup"><span data-stu-id="f47ed-115">The following example makes several calls to the `MsgBox` function.</span></span> <span data-ttu-id="f47ed-116">`MsgBox` ma jeden wymagany parametr i dwa parametry opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="f47ed-116">`MsgBox` has one required parameter and two optional parameters.</span></span>  
  
 <span data-ttu-id="f47ed-117">Pierwsze wywołanie w celu `MsgBox` dostarcza wszystkich trzech argumentów w kolejności, która `MsgBox` definiuje je.</span><span class="sxs-lookup"><span data-stu-id="f47ed-117">The first call to `MsgBox` supplies all three arguments in the order that `MsgBox` defines them.</span></span> <span data-ttu-id="f47ed-118">Drugie wywołanie dostarcza tylko wymagany argument.</span><span class="sxs-lookup"><span data-stu-id="f47ed-118">The second call supplies only the required argument.</span></span> <span data-ttu-id="f47ed-119">Wywołania trzecie i czwarte dostarczają argumenty pierwszy i trzeci.</span><span class="sxs-lookup"><span data-stu-id="f47ed-119">The third and fourth calls supply the first and third arguments.</span></span> <span data-ttu-id="f47ed-120">Trzecie wywołanie robi to według pozycji, a czwarte wywołanie — według nazwy.</span><span class="sxs-lookup"><span data-stu-id="f47ed-120">The third call does this by position, and the fourth call does it by name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#47](./codesnippet/VisualBasic/optional-parameters_1.vb)]  
  
## <a name="determining-whether-an-optional-argument-is-present"></a><span data-ttu-id="f47ed-121">Określenie, czy opcjonalny argument jest obecny</span><span class="sxs-lookup"><span data-stu-id="f47ed-121">Determining Whether an Optional Argument Is Present</span></span>  
 <span data-ttu-id="f47ed-122">Procedura nie może wykryć w czasie wykonywania, czy podany argument został pominięty lub kod wywołujący ma jawnie przekazywaną wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="f47ed-122">A procedure cannot detect at run time whether a given argument has been omitted or the calling code has explicitly supplied the default value.</span></span> <span data-ttu-id="f47ed-123">Jeśli potrzebujesz takiego rozróżnienia, możesz ustawić mało prawdopodobną wartość jako domyślną.</span><span class="sxs-lookup"><span data-stu-id="f47ed-123">If you need to make this distinction, you can set an unlikely value as the default.</span></span> <span data-ttu-id="f47ed-124">Opcjonalny parametr definiuje procedurę `office`, a testy na wartość domyślną `QJZ`, aby zobaczyć, czy ma został pominięty w wywołaniu:</span><span class="sxs-lookup"><span data-stu-id="f47ed-124">The following procedure defines the optional parameter `office`, and tests for its default value, `QJZ`, to see if it has been omitted in the call:</span></span>  
  
 [!code-vb[VbVbcnProcedures#46](./codesnippet/VisualBasic/optional-parameters_2.vb)]  
  
 <span data-ttu-id="f47ed-125">Jeśli parametr opcjonalny jest typem referencyjnym, takich jak `String`, można użyć `Nothing` jako wartość domyślną, pod warunkiem nie jest oczekiwana wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="f47ed-125">If the optional parameter is a reference type such as a `String`, you can use `Nothing` as the default value, provided this is not an expected value for the argument.</span></span>  
  
## <a name="optional-parameters-and-overloading"></a><span data-ttu-id="f47ed-126">Parametry opcjonalne i przeciążenie</span><span class="sxs-lookup"><span data-stu-id="f47ed-126">Optional Parameters and Overloading</span></span>  
 <span data-ttu-id="f47ed-127">Innym sposobem zdefiniowania procedury z opcjonalnymi parametrami jest używanie przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="f47ed-127">Another way to define a procedure with optional parameters is to use overloading.</span></span> <span data-ttu-id="f47ed-128">Jeśli masz jeden parametr opcjonalny, możesz zdefiniować dwie przeciążone wersje procedury, jedną przyjmującą parametr i jedną bez niego.</span><span class="sxs-lookup"><span data-stu-id="f47ed-128">If you have one optional parameter, you can define two overloaded versions of the procedure, one accepting the parameter and one without it.</span></span> <span data-ttu-id="f47ed-129">Takie podejście staje się bardziej skomplikowane w miarę wzrostu liczby parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="f47ed-129">This approach becomes more complicated as the number of optional parameters increases.</span></span> <span data-ttu-id="f47ed-130">Jej zaletą jest jednak, że możesz mieć absolutną pewność, czy program wywołujący dostarcza każdy opcjonalny argument.</span><span class="sxs-lookup"><span data-stu-id="f47ed-130">However, its advantage is that you can be absolutely sure whether the calling program supplied each optional argument.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f47ed-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f47ed-131">See Also</span></span>  
 [<span data-ttu-id="f47ed-132">Procedury</span><span class="sxs-lookup"><span data-stu-id="f47ed-132">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="f47ed-133">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="f47ed-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="f47ed-134">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="f47ed-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="f47ed-135">Przekazywanie argumentów według pozycji i według nazwy</span><span class="sxs-lookup"><span data-stu-id="f47ed-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="f47ed-136">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="f47ed-136">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="f47ed-137">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="f47ed-137">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="f47ed-138">Optional</span><span class="sxs-lookup"><span data-stu-id="f47ed-138">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [<span data-ttu-id="f47ed-139">ParamArray</span><span class="sxs-lookup"><span data-stu-id="f47ed-139">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
