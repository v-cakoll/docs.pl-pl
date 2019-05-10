---
title: With...End With — Instrukcja (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 38a34a4662d969fd526963744b8bd493952d9cff
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615071"
---
# <a name="withend-with-statement-visual-basic"></a><span data-ttu-id="59d0e-102">With...End With — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59d0e-102">With...End With Statement (Visual Basic)</span></span>
<span data-ttu-id="59d0e-103">Wykonuje szereg instrukcji, które wielokrotnie odwołują się do pojedynczego obiektu lub struktury, dzięki czemu instrukcje mogą używać uproszczonej składni podczas uzyskiwania dostępu do członków obiektu lub struktury.</span><span class="sxs-lookup"><span data-stu-id="59d0e-103">Executes a series of statements that repeatedly refer to a single object or structure so that the statements can use a simplified syntax when accessing members of the object or structure.</span></span>  <span data-ttu-id="59d0e-104">Korzystając ze struktury możesz jedynie odczytać wartości członków lub wywoływać metody i wystąpi błąd, jeśli zostanie podjęta próba przypisania wartości do członków struktury używanych w `With...End With` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="59d0e-104">When using a structure, you can only read the values of members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59d0e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="59d0e-105">Syntax</span></span>  
  
```  
With objectExpression  
    [ statements ]  
End With  
```  
  
## <a name="parts"></a><span data-ttu-id="59d0e-106">Części</span><span class="sxs-lookup"><span data-stu-id="59d0e-106">Parts</span></span>  
  
|<span data-ttu-id="59d0e-107">Termin</span><span class="sxs-lookup"><span data-stu-id="59d0e-107">Term</span></span>|<span data-ttu-id="59d0e-108">Definicja</span><span class="sxs-lookup"><span data-stu-id="59d0e-108">Definition</span></span>|  
|---|---|  
|`objectExpression`|<span data-ttu-id="59d0e-109">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="59d0e-109">Required.</span></span> <span data-ttu-id="59d0e-110">Wyrażenie, które zostaje oszacowane do obiektu.</span><span class="sxs-lookup"><span data-stu-id="59d0e-110">An expression that evaluates to an object.</span></span> <span data-ttu-id="59d0e-111">Wyrażenie może być dowolnie złożone i jest sprawdzane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="59d0e-111">The expression may be arbitrarily complex and is evaluated only once.</span></span> <span data-ttu-id="59d0e-112">Wyrażenie może być dowolnego typu danych, w tym typów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="59d0e-112">The expression can evaluate to any data type, including elementary types.</span></span>|  
|`statements`|<span data-ttu-id="59d0e-113">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="59d0e-113">Optional.</span></span> <span data-ttu-id="59d0e-114">Jedna lub więcej instrukcji między `With` i `End With` które mogą się odwoływać do członków obiektu, który jest wytwarzany przez ocenę `objectExpression`.</span><span class="sxs-lookup"><span data-stu-id="59d0e-114">One or more statements between `With` and `End With` that may refer to members of an object that's produced by the evaluation of `objectExpression`.</span></span>|  
|`End With`|<span data-ttu-id="59d0e-115">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="59d0e-115">Required.</span></span> <span data-ttu-id="59d0e-116">Kończy definicję `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="59d0e-116">Terminates the definition of the `With` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59d0e-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59d0e-117">Remarks</span></span>  
 <span data-ttu-id="59d0e-118">Za pomocą `With...End With`, można wykonać serię instrukcji na określonym obiekcie bez określania nazwy obiektu wiele razy.</span><span class="sxs-lookup"><span data-stu-id="59d0e-118">By using `With...End With`, you can perform a series of statements on a specified object without specifying the name of the object multiple times.</span></span> <span data-ttu-id="59d0e-119">W ramach `With` blok instrukcji, można określić członka obiektu, rozpoczynając od kropki, tak jakby `With` obiektu instrukcji go poprzedzał.</span><span class="sxs-lookup"><span data-stu-id="59d0e-119">Within a `With` statement block, you can specify a member of the object starting with a period, as if the `With` statement object preceded it.</span></span>  
  
 <span data-ttu-id="59d0e-120">Na przykład, aby zmienić wiele właściwości dla pojedynczego obiektu, umieść instrukcje przypisania właściwości wewnątrz `With...End With` bloku, odwołanie do obiektu tylko raz zamiast raz dla każdego przypisania właściwości.</span><span class="sxs-lookup"><span data-stu-id="59d0e-120">For example, to change multiple properties on a single object, place the property assignment statements inside the `With...End With` block, referring to the object only once instead of once for each property assignment.</span></span>  
  
 <span data-ttu-id="59d0e-121">Jeśli kod uzyskuje dostęp do tego samego obiektu w wielu instrukcjach, uzyskasz następujące korzyści za pomocą `With` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="59d0e-121">If your code accesses the same object in multiple statements, you gain the following benefits by using the `With` statement:</span></span>  
  
- <span data-ttu-id="59d0e-122">Nie musisz szacować złożonego wyrażenia wiele razy ani przypisywać wyniku do zmiennej tymczasowej, aby odwołać się do jego członków wiele razy.</span><span class="sxs-lookup"><span data-stu-id="59d0e-122">You don't need to evaluate a complex expression multiple times or assign the result to a temporary variable to refer to its members multiple times.</span></span>  
  
- <span data-ttu-id="59d0e-123">Kod staje się bardziej czytelny dzięki eliminacji powtarzających się wyrażeń kwalifikujących.</span><span class="sxs-lookup"><span data-stu-id="59d0e-123">You make your code more readable by eliminating repetitive qualifying expressions.</span></span>  
  
 <span data-ttu-id="59d0e-124">Typ danych `objectExpression` może być dowolną klasę lub typ struktury lub nawet typ podstawowy języka Visual Basic taką jak `Integer`.</span><span class="sxs-lookup"><span data-stu-id="59d0e-124">The data type of `objectExpression` can be any class or structure type or even a Visual Basic elementary type such as `Integer`.</span></span>  <span data-ttu-id="59d0e-125">Jeśli `objectExpression` wyniki coś innego niż obiekt można tylko odczytać wartości jego członków lub wywoływać metody i wystąpi błąd, jeśli zostanie podjęta próba przypisania wartości do członków struktury używanych w `With...End With` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="59d0e-125">If `objectExpression` results in anything other than an object, you can only read the values of its members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>  <span data-ttu-id="59d0e-126">Jest to ten sam błąd, jeśli wywołano metodę, która zwróciła strukturę i natychmiast uzyskać dostęp i przypisać wartość do członka wyniku funkcji, takich jak `GetAPoint().x = 1`.</span><span class="sxs-lookup"><span data-stu-id="59d0e-126">This is the same error you would get if you invoked a method that returned a structure and immediately accessed and assigned a value to a member of the function’s result, such as `GetAPoint().x = 1`.</span></span>  <span data-ttu-id="59d0e-127">Problem w obu przypadkach jest taki, że struktura istnieje tylko na stosie wywołań i nie ma żadnego sposobu, aby członek zmodyfikowanej struktury w takich sytuacjach mógł pisać do takich lokalizacji, żeby inny kod w programie mógł obserwować zmiany.</span><span class="sxs-lookup"><span data-stu-id="59d0e-127">The problem in both cases is that the structure exists only on the call stack, and there is no way a modified structure member in these situations can write to  a location such that any other code in the program can observe the change.</span></span>  
  
 <span data-ttu-id="59d0e-128">`objectExpression` Jest wykonywane tylko raz, po wejściu do bloku.</span><span class="sxs-lookup"><span data-stu-id="59d0e-128">The `objectExpression` is evaluated once, upon entry into the block.</span></span> <span data-ttu-id="59d0e-129">Nie można ponownie przypisać `objectExpression` z poziomu `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="59d0e-129">You can't reassign the `objectExpression` from within the `With` block.</span></span>  
  
 <span data-ttu-id="59d0e-130">W ramach `With` bloku, jest dostępne metody i właściwości jedynie określonego obiektu bez ich kwalifikowania.</span><span class="sxs-lookup"><span data-stu-id="59d0e-130">Within a `With` block, you can access the methods and properties of only the specified object without qualifying them.</span></span> <span data-ttu-id="59d0e-131">Możesz użyć metod i właściwości innych obiektów, ale musisz je zakwalifikować z ich nazwami obiektów.</span><span class="sxs-lookup"><span data-stu-id="59d0e-131">You can use methods and properties of other objects, but you must qualify them with their object names.</span></span>  
  
 <span data-ttu-id="59d0e-132">Możesz umieścić jedną `With...End With` instrukcji w innym.</span><span class="sxs-lookup"><span data-stu-id="59d0e-132">You can place one `With...End With` statement within another.</span></span> <span data-ttu-id="59d0e-133">Zagnieżdżone `With...End With` instrukcji może być skomplikowane, jeśli obiekty, które są określone, nie są jasne z kontekstu.</span><span class="sxs-lookup"><span data-stu-id="59d0e-133">Nested `With...End With` statements may be confusing if the objects that are being referred to aren't clear from context.</span></span> <span data-ttu-id="59d0e-134">Należy podać w pełni kwalifikowane odwołanie do obiektu, który znajduje się w zewnętrznym `With` zablokować, jeśli odwołanie do obiektu pochodzi z wewnętrznego `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="59d0e-134">You must provide a fully qualified reference to an object that's in an outer `With` block when the object is referenced from within an inner `With` block.</span></span>  
  
 <span data-ttu-id="59d0e-135">Nie można rozgałęzić do `With` bloku instrukcji poza blokiem.</span><span class="sxs-lookup"><span data-stu-id="59d0e-135">You can't branch into a `With` statement block from outside the block.</span></span>  
  
 <span data-ttu-id="59d0e-136">Instrukcje są wykonywane tylko raz, chyba że blok zawiera pętlę.</span><span class="sxs-lookup"><span data-stu-id="59d0e-136">Unless the block contains a loop, the statements run only once.</span></span> <span data-ttu-id="59d0e-137">Możesz zagnieździć różne rodzaje struktur sterujących.</span><span class="sxs-lookup"><span data-stu-id="59d0e-137">You can nest different kinds of control structures.</span></span> <span data-ttu-id="59d0e-138">Aby uzyskać więcej informacji, zobacz [zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="59d0e-138">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59d0e-139">Możesz użyć `With` również słowa kluczowego w inicjatorach obiektów.</span><span class="sxs-lookup"><span data-stu-id="59d0e-139">You can use the `With` keyword in object initializers also.</span></span> <span data-ttu-id="59d0e-140">Aby uzyskać więcej informacji i przykładów, zobacz [inicjatory obiektów: Typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) i [typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="59d0e-140">For more information and examples, see [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
>   
>  <span data-ttu-id="59d0e-141">Jeśli używasz `With` bloku tylko do zainicjowania właściwości lub pól obiektu, który został właśnie utworzony, rozważ użycie zamiast tego inicjatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="59d0e-141">If you're using a `With` block only to initialize the properties or fields of an object that you've just instantiated, consider using an object initializer instead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59d0e-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="59d0e-142">Example</span></span>  
 <span data-ttu-id="59d0e-143">W poniższym przykładzie każdy `With` bloku wykonuje serię instrukcji na pojedynczym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="59d0e-143">In the following example, each `With` block executes a series of statements on a single object.</span></span>  
  
 [!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="59d0e-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="59d0e-144">Example</span></span>  
 <span data-ttu-id="59d0e-145">Poniższy przykład zagnieżdża instrukcje `With…End With` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="59d0e-145">The following example nests `With…End With` statements.</span></span> <span data-ttu-id="59d0e-146">W ramach zagnieżdżonej `With` instrukcji, składnia odnosi się do obiektu wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="59d0e-146">Within the nested `With` statement, the syntax refers to the inner object.</span></span>  
  
 [!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="59d0e-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59d0e-147">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="59d0e-148">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="59d0e-148">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="59d0e-149">Inicjatory obiektów: Typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="59d0e-149">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="59d0e-150">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="59d0e-150">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
