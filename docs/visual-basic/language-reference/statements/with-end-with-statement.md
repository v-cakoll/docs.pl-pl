---
title: "With...End With — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.With
helpviewer_keywords:
- With keyword [Visual Basic]
- loop structures [Visual Basic], and With...End With statements
- execution [Visual Basic], on object
- instructions, repeating
- With...End With statements [Visual Basic]
- With statement [Visual Basic]
- With statement [Visual Basic], nesting
- objects [Visual Basic], accessing
- With block
- End keyword [Visual Basic], With...End With statements
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aa1f416e1bfdf6cdb51b098c0e2bd5e9912cb309
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="withend-with-statement-visual-basic"></a><span data-ttu-id="9a155-102">With...End With — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a155-102">With...End With Statement (Visual Basic)</span></span>
<span data-ttu-id="9a155-103">Wykonuje szereg instrukcji, które wielokrotnie odwołują się do pojedynczego obiektu lub struktury, dzięki czemu instrukcje mogą używać uproszczonej składni podczas uzyskiwania dostępu do członków obiektu lub struktury.</span><span class="sxs-lookup"><span data-stu-id="9a155-103">Executes a series of statements that repeatedly refer to a single object or structure so that the statements can use a simplified syntax when accessing members of the object or structure.</span></span>  <span data-ttu-id="9a155-104">Podczas używania struktury można odczytać wartości elementów członkowskich lub tylko wywołania metod i występuje błąd, Jeśli spróbujesz przypisać wartości do elementów członkowskich struktury używane w `With...End With` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9a155-104">When using a structure, you can only read the values of members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a155-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a155-105">Syntax</span></span>  
  
```  
With objectExpression  
    [ statements ]  
End With  
```  
  
## <a name="parts"></a><span data-ttu-id="9a155-106">Części</span><span class="sxs-lookup"><span data-stu-id="9a155-106">Parts</span></span>  
  
|<span data-ttu-id="9a155-107">Termin</span><span class="sxs-lookup"><span data-stu-id="9a155-107">Term</span></span>|<span data-ttu-id="9a155-108">Definicja</span><span class="sxs-lookup"><span data-stu-id="9a155-108">Definition</span></span>|  
|---|---|  
|`objectExpression`|<span data-ttu-id="9a155-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="9a155-109">Required.</span></span> <span data-ttu-id="9a155-110">Wyrażenie, które zostaje oszacowane do obiektu.</span><span class="sxs-lookup"><span data-stu-id="9a155-110">An expression that evaluates to an object.</span></span> <span data-ttu-id="9a155-111">Wyrażenie może być dowolnie złożone i jest sprawdzane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="9a155-111">The expression may be arbitrarily complex and is evaluated only once.</span></span> <span data-ttu-id="9a155-112">Wyrażenie może być dowolnego typu danych, w tym typów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="9a155-112">The expression can evaluate to any data type, including elementary types.</span></span>|  
|`statements`|<span data-ttu-id="9a155-113">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9a155-113">Optional.</span></span> <span data-ttu-id="9a155-114">Co najmniej jeden instrukcji między `With` i `End With` może odwołujące się do elementów członkowskich obiektu, który jest generowany przez ocenę `objectExpression`.</span><span class="sxs-lookup"><span data-stu-id="9a155-114">One or more statements between `With` and `End With` that may refer to members of an object that's produced by the evaluation of `objectExpression`.</span></span>|  
|`End With`|<span data-ttu-id="9a155-115">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="9a155-115">Required.</span></span> <span data-ttu-id="9a155-116">Kończy definicję `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="9a155-116">Terminates the definition of the `With` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a155-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a155-117">Remarks</span></span>  
 <span data-ttu-id="9a155-118">Przy użyciu `With...End With`, można wykonać serię instrukcji na określony obiekt bez określania nazwy obiektu wiele razy.</span><span class="sxs-lookup"><span data-stu-id="9a155-118">By using `With...End With`, you can perform a series of statements on a specified object without specifying the name of the object multiple times.</span></span> <span data-ttu-id="9a155-119">W ramach `With` blok instrukcji, można określić elementu członkowskiego obiektu, rozpoczynając od okresu, tak jakby `With` obiektu instrukcji poprzedzające go.</span><span class="sxs-lookup"><span data-stu-id="9a155-119">Within a `With` statement block, you can specify a member of the object starting with a period, as if the `With` statement object preceded it.</span></span>  
  
 <span data-ttu-id="9a155-120">Na przykład, aby zmienić wiele właściwości w jednym obiekcie, umieść instrukcje przypisania właściwości wewnątrz `With...End With` bloku, odwołanie do obiektu tylko raz zamiast raz dla każdego przydziału właściwości.</span><span class="sxs-lookup"><span data-stu-id="9a155-120">For example, to change multiple properties on a single object, place the property assignment statements inside the `With...End With` block, referring to the object only once instead of once for each property assignment.</span></span>  
  
 <span data-ttu-id="9a155-121">Jeśli kod uzyskuje dostęp do tego samego obiektu wiele instrukcji, za pomocą zyskać następujące korzyści `With` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="9a155-121">If your code accesses the same object in multiple statements, you gain the following benefits by using the `With` statement:</span></span>  
  
-   <span data-ttu-id="9a155-122">Nie musisz szacować złożonego wyrażenia wiele razy ani przypisywać wyniku do zmiennej tymczasowej, aby odwołać się do jego członków wiele razy.</span><span class="sxs-lookup"><span data-stu-id="9a155-122">You don't need to evaluate a complex expression multiple times or assign the result to a temporary variable to refer to its members multiple times.</span></span>  
  
-   <span data-ttu-id="9a155-123">Kod staje się bardziej czytelny dzięki eliminacji powtarzających się wyrażeń kwalifikujących.</span><span class="sxs-lookup"><span data-stu-id="9a155-123">You make your code more readable by eliminating repetitive qualifying expressions.</span></span>  
  
 <span data-ttu-id="9a155-124">Typ danych miary `objectExpression` może być dowolną klasę lub typ struktury lub nawet typu podstawowe języka Visual Basic takich jak `Integer`.</span><span class="sxs-lookup"><span data-stu-id="9a155-124">The data type of `objectExpression` can be any class or structure type or even a Visual Basic elementary type such as `Integer`.</span></span>  <span data-ttu-id="9a155-125">Jeśli `objectExpression` wyniki w innym niż obiekt można odczytać wartości jego elementów członkowskich lub tylko wywołania metod i występuje błąd, Jeśli spróbujesz przypisać wartości do elementów członkowskich struktury używane w `With...End With` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9a155-125">If `objectExpression` results in anything other than an object, you can only read the values of its members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>  <span data-ttu-id="9a155-126">Jest to ten sam błąd, jeśli należy wywołać metodę zwrócił strukturę i od razu dostępne i przypisywać wartości do elementu członkowskiego wyniku funkcji, takich jak `GetAPoint().x = 1`.</span><span class="sxs-lookup"><span data-stu-id="9a155-126">This is the same error you would get if you invoked a method that returned a structure and immediately accessed and assigned a value to a member of the function’s result, such as `GetAPoint().x = 1`.</span></span>  <span data-ttu-id="9a155-127">Problem w obu przypadkach jest taki, że struktura istnieje tylko na stosie wywołań i nie ma żadnego sposobu, aby członek zmodyfikowanej struktury w takich sytuacjach mógł pisać do takich lokalizacji, żeby inny kod w programie mógł obserwować zmiany.</span><span class="sxs-lookup"><span data-stu-id="9a155-127">The problem in both cases is that the structure exists only on the call stack, and there is no way a modified structure member in these situations can write to  a location such that any other code in the program can observe the change.</span></span>  
  
 <span data-ttu-id="9a155-128">`objectExpression` Jest oceniane, po wejściu do bloku.</span><span class="sxs-lookup"><span data-stu-id="9a155-128">The `objectExpression` is evaluated once, upon entry into the block.</span></span> <span data-ttu-id="9a155-129">Nie można przepisać `objectExpression` z poziomu `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="9a155-129">You can't reassign the `objectExpression` from within the `With` block.</span></span>  
  
 <span data-ttu-id="9a155-130">W ramach `With` bloku, użytkownik ma dostęp do metod i właściwości określonego obiektu bez kwalifikujących się je.</span><span class="sxs-lookup"><span data-stu-id="9a155-130">Within a `With` block, you can access the methods and properties of only the specified object without qualifying them.</span></span> <span data-ttu-id="9a155-131">Możesz użyć metod i właściwości innych obiektów, ale musisz je zakwalifikować z ich nazwami obiektów.</span><span class="sxs-lookup"><span data-stu-id="9a155-131">You can use methods and properties of other objects, but you must qualify them with their object names.</span></span>  
  
 <span data-ttu-id="9a155-132">Możesz umieścić jedną `With...End With` instrukcji w innym.</span><span class="sxs-lookup"><span data-stu-id="9a155-132">You can place one `With...End With` statement within another.</span></span> <span data-ttu-id="9a155-133">Zagnieżdżone `With...End With` instrukcji może być mylące, jeśli obiekty, które są określone nie jest jasne z kontekstu.</span><span class="sxs-lookup"><span data-stu-id="9a155-133">Nested `With...End With` statements may be confusing if the objects that are being referred to aren't clear from context.</span></span> <span data-ttu-id="9a155-134">Należy podać pełną odwołanie do obiektu, który znajduje się w zewnętrznym `With` zablokować, jeśli obiekt jest wywoływany przez w wewnętrzny `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="9a155-134">You must provide a fully qualified reference to an object that's in an outer `With` block when the object is referenced from within an inner `With` block.</span></span>  
  
 <span data-ttu-id="9a155-135">Nie można rozgałęzić do `With` blok instrukcji z poza blokiem.</span><span class="sxs-lookup"><span data-stu-id="9a155-135">You can't branch into a `With` statement block from outside the block.</span></span>  
  
 <span data-ttu-id="9a155-136">Instrukcje są wykonywane tylko raz, chyba że blok zawiera pętlę.</span><span class="sxs-lookup"><span data-stu-id="9a155-136">Unless the block contains a loop, the statements run only once.</span></span> <span data-ttu-id="9a155-137">Możesz zagnieździć różne rodzaje struktur sterujących.</span><span class="sxs-lookup"><span data-stu-id="9a155-137">You can nest different kinds of control structures.</span></span> <span data-ttu-id="9a155-138">Aby uzyskać więcej informacji, zobacz [zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="9a155-138">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a155-139">Można użyć `With` — słowo kluczowe w obiekt również inicjatory.</span><span class="sxs-lookup"><span data-stu-id="9a155-139">You can use the `With` keyword in object initializers also.</span></span> <span data-ttu-id="9a155-140">Aby uzyskać dodatkowe informacje i przykłady, zobacz [inicjatory obiektów: typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) i [typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="9a155-140">For more information and examples, see [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
>   
>  <span data-ttu-id="9a155-141">Jeśli używasz `With` bloku tylko zainicjować właściwości lub pola obiektu, który właśnie został uruchomiony, rozważ użycie zamiast tego inicjatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="9a155-141">If you're using a `With` block only to initialize the properties or fields of an object that you've just instantiated, consider using an object initializer instead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a155-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a155-142">Example</span></span>  
 <span data-ttu-id="9a155-143">W poniższym przykładzie każdy `With` bloku uruchamia serię instrukcji na pojedynczy obiekt.</span><span class="sxs-lookup"><span data-stu-id="9a155-143">In the following example, each `With` block executes a series of statements on a single object.</span></span>  
  
 [!code-vb[VbVbalrWithStatement#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/with-end-with-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="9a155-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a155-144">Example</span></span>  
 <span data-ttu-id="9a155-145">Następujące zagnieżdża przykład `With…End With` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="9a155-145">The following example nests `With…End With` statements.</span></span> <span data-ttu-id="9a155-146">W ramach zagnieżdżone `With` , składnia odwołuje się do obiektu wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="9a155-146">Within the nested `With` statement, the syntax refers to the inner object.</span></span>  
  
 [!code-vb[VbVbalrWithStatement#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/with-end-with-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9a155-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a155-147">See Also</span></span>  
 <xref:System.Collections.Generic.List%601>  
 [<span data-ttu-id="9a155-148">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="9a155-148">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="9a155-149">Inicjatory obiektów: Typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="9a155-149">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="9a155-150">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="9a155-150">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
