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
ms.openlocfilehash: 3d26932c23299c6fbcb53b1389abd7694f529eef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963332"
---
# <a name="withend-with-statement-visual-basic"></a><span data-ttu-id="255b5-102">With...End With — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="255b5-102">With...End With Statement (Visual Basic)</span></span>
<span data-ttu-id="255b5-103">Wykonuje szereg instrukcji, które wielokrotnie odwołują się do pojedynczego obiektu lub struktury, dzięki czemu instrukcje mogą używać uproszczonej składni podczas uzyskiwania dostępu do członków obiektu lub struktury.</span><span class="sxs-lookup"><span data-stu-id="255b5-103">Executes a series of statements that repeatedly refer to a single object or structure so that the statements can use a simplified syntax when accessing members of the object or structure.</span></span>  <span data-ttu-id="255b5-104">W przypadku użycia struktury można odczytać tylko wartości elementów członkowskich lub wywołać metody, a w przypadku próby przypisania wartości do elementów członkowskich struktury używanej w `With...End With` instrukcji należy uzyskać błąd.</span><span class="sxs-lookup"><span data-stu-id="255b5-104">When using a structure, you can only read the values of members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="255b5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="255b5-105">Syntax</span></span>  
  
```  
With objectExpression  
    [ statements ]  
End With  
```  
  
## <a name="parts"></a><span data-ttu-id="255b5-106">Części</span><span class="sxs-lookup"><span data-stu-id="255b5-106">Parts</span></span>  
  
|<span data-ttu-id="255b5-107">Termin</span><span class="sxs-lookup"><span data-stu-id="255b5-107">Term</span></span>|<span data-ttu-id="255b5-108">Definicja</span><span class="sxs-lookup"><span data-stu-id="255b5-108">Definition</span></span>|  
|---|---|  
|`objectExpression`|<span data-ttu-id="255b5-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="255b5-109">Required.</span></span> <span data-ttu-id="255b5-110">Wyrażenie, które zostaje oszacowane do obiektu.</span><span class="sxs-lookup"><span data-stu-id="255b5-110">An expression that evaluates to an object.</span></span> <span data-ttu-id="255b5-111">Wyrażenie może być dowolnie złożone i jest sprawdzane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="255b5-111">The expression may be arbitrarily complex and is evaluated only once.</span></span> <span data-ttu-id="255b5-112">Wyrażenie może być dowolnego typu danych, w tym typów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="255b5-112">The expression can evaluate to any data type, including elementary types.</span></span>|  
|`statements`|<span data-ttu-id="255b5-113">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="255b5-113">Optional.</span></span> <span data-ttu-id="255b5-114">Jedna lub więcej instrukcji między `With` i `End With` , które mogą odwoływać się do elementów członkowskich obiektu, który jest `objectExpression`produkowany przez ocenę.</span><span class="sxs-lookup"><span data-stu-id="255b5-114">One or more statements between `With` and `End With` that may refer to members of an object that's produced by the evaluation of `objectExpression`.</span></span>|  
|`End With`|<span data-ttu-id="255b5-115">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="255b5-115">Required.</span></span> <span data-ttu-id="255b5-116">Kończy definicję `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="255b5-116">Terminates the definition of the `With` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="255b5-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="255b5-117">Remarks</span></span>  
 <span data-ttu-id="255b5-118">Za pomocą `With...End With`, można wykonać serię instrukcji dla określonego obiektu bez podawania nazwy obiektu wiele razy.</span><span class="sxs-lookup"><span data-stu-id="255b5-118">By using `With...End With`, you can perform a series of statements on a specified object without specifying the name of the object multiple times.</span></span> <span data-ttu-id="255b5-119">W bloku `With` instrukcji można określić element członkowski obiektu, rozpoczynając od kropki, tak jakby obiekt instrukcji poprzedzał go. `With`</span><span class="sxs-lookup"><span data-stu-id="255b5-119">Within a `With` statement block, you can specify a member of the object starting with a period, as if the `With` statement object preceded it.</span></span>  
  
 <span data-ttu-id="255b5-120">Na przykład aby zmienić wiele właściwości dla pojedynczego obiektu, umieść instrukcje przypisania właściwości wewnątrz `With...End With` bloku, odwołując się do obiektu tylko raz, a nie raz dla każdego przypisania właściwości.</span><span class="sxs-lookup"><span data-stu-id="255b5-120">For example, to change multiple properties on a single object, place the property assignment statements inside the `With...End With` block, referring to the object only once instead of once for each property assignment.</span></span>  
  
 <span data-ttu-id="255b5-121">Jeśli kod uzyskuje dostęp do tego samego obiektu w wielu instrukcjach, uzyskasz następujące korzyści przy użyciu `With` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="255b5-121">If your code accesses the same object in multiple statements, you gain the following benefits by using the `With` statement:</span></span>  
  
- <span data-ttu-id="255b5-122">Nie musisz szacować złożonego wyrażenia wiele razy ani przypisywać wyniku do zmiennej tymczasowej, aby odwołać się do jego członków wiele razy.</span><span class="sxs-lookup"><span data-stu-id="255b5-122">You don't need to evaluate a complex expression multiple times or assign the result to a temporary variable to refer to its members multiple times.</span></span>  
  
- <span data-ttu-id="255b5-123">Kod staje się bardziej czytelny dzięki eliminacji powtarzających się wyrażeń kwalifikujących.</span><span class="sxs-lookup"><span data-stu-id="255b5-123">You make your code more readable by eliminating repetitive qualifying expressions.</span></span>  
  
 <span data-ttu-id="255b5-124">Typem `objectExpression` danych może być dowolna klasa lub typ struktury, a nawet Visual Basic typ podstawowy, taki jak `Integer`.</span><span class="sxs-lookup"><span data-stu-id="255b5-124">The data type of `objectExpression` can be any class or structure type or even a Visual Basic elementary type such as `Integer`.</span></span>  <span data-ttu-id="255b5-125">Jeśli `objectExpression` wynikiem jest coś innego niż obiekt, można odczytać tylko wartości swoich elementów członkowskich lub wywołać metody, a w przypadku próby przypisania wartości do elementów członkowskich struktury użytej `With...End With` w instrukcji zostanie wyświetlony komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="255b5-125">If `objectExpression` results in anything other than an object, you can only read the values of its members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>  <span data-ttu-id="255b5-126">Jest to ten sam błąd, który można uzyskać w przypadku wywołania metody, która zwróciła strukturę i od razu uzyskuje dostęp do elementu członkowskiego wyniku funkcji, na przykład `GetAPoint().x = 1`.</span><span class="sxs-lookup"><span data-stu-id="255b5-126">This is the same error you would get if you invoked a method that returned a structure and immediately accessed and assigned a value to a member of the function’s result, such as `GetAPoint().x = 1`.</span></span>  <span data-ttu-id="255b5-127">Problem w obu przypadkach jest taki, że struktura istnieje tylko na stosie wywołań i nie ma żadnego sposobu, aby członek zmodyfikowanej struktury w takich sytuacjach mógł pisać do takich lokalizacji, żeby inny kod w programie mógł obserwować zmiany.</span><span class="sxs-lookup"><span data-stu-id="255b5-127">The problem in both cases is that the structure exists only on the call stack, and there is no way a modified structure member in these situations can write to  a location such that any other code in the program can observe the change.</span></span>  
  
 <span data-ttu-id="255b5-128">Ten `objectExpression` element jest obliczany raz, po umieszczeniu w bloku.</span><span class="sxs-lookup"><span data-stu-id="255b5-128">The `objectExpression` is evaluated once, upon entry into the block.</span></span> <span data-ttu-id="255b5-129">Nie można ponownie przypisać `objectExpression` elementu z `With` wewnątrz bloku.</span><span class="sxs-lookup"><span data-stu-id="255b5-129">You can't reassign the `objectExpression` from within the `With` block.</span></span>  
  
 <span data-ttu-id="255b5-130">`With` W bloku można uzyskać dostęp do metod i właściwości tylko określonego obiektu bez ich kwalifikowania.</span><span class="sxs-lookup"><span data-stu-id="255b5-130">Within a `With` block, you can access the methods and properties of only the specified object without qualifying them.</span></span> <span data-ttu-id="255b5-131">Możesz użyć metod i właściwości innych obiektów, ale musisz je zakwalifikować z ich nazwami obiektów.</span><span class="sxs-lookup"><span data-stu-id="255b5-131">You can use methods and properties of other objects, but you must qualify them with their object names.</span></span>  
  
 <span data-ttu-id="255b5-132">Można umieścić jedną `With...End With` instrukcję w innej.</span><span class="sxs-lookup"><span data-stu-id="255b5-132">You can place one `With...End With` statement within another.</span></span> <span data-ttu-id="255b5-133">Zagnieżdżone `With...End With` instrukcje mogą być mylące, jeśli obiekty, do których odwołuje się nie są jasne z kontekstu.</span><span class="sxs-lookup"><span data-stu-id="255b5-133">Nested `With...End With` statements may be confusing if the objects that are being referred to aren't clear from context.</span></span> <span data-ttu-id="255b5-134">Musisz podać w pełni kwalifikowane odwołanie do obiektu znajdującego się w bloku zewnętrznym `With` , gdy odwołanie do obiektu następuje w bloku wewnętrznym. `With`</span><span class="sxs-lookup"><span data-stu-id="255b5-134">You must provide a fully qualified reference to an object that's in an outer `With` block when the object is referenced from within an inner `With` block.</span></span>  
  
 <span data-ttu-id="255b5-135">Nie można rozgałęzić `With` bloku instrukcji spoza bloku.</span><span class="sxs-lookup"><span data-stu-id="255b5-135">You can't branch into a `With` statement block from outside the block.</span></span>  
  
 <span data-ttu-id="255b5-136">Instrukcje są wykonywane tylko raz, chyba że blok zawiera pętlę.</span><span class="sxs-lookup"><span data-stu-id="255b5-136">Unless the block contains a loop, the statements run only once.</span></span> <span data-ttu-id="255b5-137">Możesz zagnieździć różne rodzaje struktur sterujących.</span><span class="sxs-lookup"><span data-stu-id="255b5-137">You can nest different kinds of control structures.</span></span> <span data-ttu-id="255b5-138">Aby uzyskać więcej informacji, zobacz [struktury formantów zagnieżdżonych](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="255b5-138">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="255b5-139">Możesz również użyć `With` słowa kluczowego w inicjatorach obiektów.</span><span class="sxs-lookup"><span data-stu-id="255b5-139">You can use the `With` keyword in object initializers also.</span></span> <span data-ttu-id="255b5-140">Aby uzyskać więcej informacji i przykładów, [zobacz Inicjatory obiektów: Typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) nazwane i anonimowe oraz [Typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="255b5-140">For more information and examples, see [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
>   
>  <span data-ttu-id="255b5-141">Jeśli używasz `With` bloku tylko do inicjowania właściwości lub pól obiektu, który został właśnie utworzony, rozważ użycie inicjatora obiektów.</span><span class="sxs-lookup"><span data-stu-id="255b5-141">If you're using a `With` block only to initialize the properties or fields of an object that you've just instantiated, consider using an object initializer instead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="255b5-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="255b5-142">Example</span></span>  
 <span data-ttu-id="255b5-143">W poniższym przykładzie każdy `With` blok wykonuje serię instrukcji na pojedynczym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="255b5-143">In the following example, each `With` block executes a series of statements on a single object.</span></span>  
  
 [!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="255b5-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="255b5-144">Example</span></span>  
 <span data-ttu-id="255b5-145">Poniższy przykład zagnieżdża `With…End With` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="255b5-145">The following example nests `With…End With` statements.</span></span> <span data-ttu-id="255b5-146">W instrukcji zagnieżdżonej `With` składnia odwołuje się do obiektu wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="255b5-146">Within the nested `With` statement, the syntax refers to the inner object.</span></span>  
  
 [!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="255b5-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="255b5-147">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="255b5-148">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="255b5-148">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="255b5-149">Inicjatory obiektów: Typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="255b5-149">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="255b5-150">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="255b5-150">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
