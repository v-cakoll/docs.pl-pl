---
title: Argumenty nazwane i opcjonalne — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
ms.openlocfilehash: d31cec602516b7cf3e4b358fa4b3f10e167e6e17
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202739"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="87a61-102">Argumenty nazwane i opcjonalne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="87a61-102">Named and Optional Arguments (C# Programming Guide)</span></span>
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] <span data-ttu-id="87a61-103">wprowadza argumentów nazwanych i opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="87a61-103">introduces named and optional arguments.</span></span> <span data-ttu-id="87a61-104">*Argumenty nazwane* umożliwiają określenie argumentu dla parametru określonego argumentu można skojarzyć z nazwą parametru, a nie za pomocą parametru pozycji na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="87a61-104">*Named arguments* enable you to specify an argument for a particular parameter by associating the argument with the parameter's name rather than with the parameter's position in the parameter list.</span></span> <span data-ttu-id="87a61-105">*Argumenty opcjonalne* umożliwia pominięcie argumentów dla niektórych parametrów.</span><span class="sxs-lookup"><span data-stu-id="87a61-105">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="87a61-106">Obu tych technik może służyć za pomocą metod, indeksatorów, konstruktorów i delegatów.</span><span class="sxs-lookup"><span data-stu-id="87a61-106">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>  
  
 <span data-ttu-id="87a61-107">Użycie argumentów nazwanych i opcjonalnych, argumenty są obliczane w kolejności, w jakiej są wyświetlane na liście argumentów nie listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="87a61-107">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>  
  
 <span data-ttu-id="87a61-108">Parametry nazwane i opcjonalne, gdy jest używana razem umożliwiają podać argumenty tylko kilka parametrów z listy parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="87a61-108">Named and optional parameters, when used together, enable you to supply arguments for only a few parameters from a list of optional parameters.</span></span> <span data-ttu-id="87a61-109">Ta funkcja znacznie ułatwia wywołania interfejsów COM, takich jak interfejsów API automatyzacji usługi Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="87a61-109">This capability greatly facilitates calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>  
  
## <a name="named-arguments"></a><span data-ttu-id="87a61-110">Argumenty nazwane</span><span class="sxs-lookup"><span data-stu-id="87a61-110">Named Arguments</span></span>  
 <span data-ttu-id="87a61-111">Argumenty nazwane pozbawione potrzebę Pamiętaj lub wyszukać kolejność parametrów na liście parametrów wywoływanych metod.</span><span class="sxs-lookup"><span data-stu-id="87a61-111">Named arguments free you from the need to remember or to look up the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="87a61-112">Parametr dla każdego argumentu można określić nazwę parametru.</span><span class="sxs-lookup"><span data-stu-id="87a61-112">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="87a61-113">Na przykład funkcja, która wyświetla szczegóły zamówienia (takie jak nazwa sprzedawcy, nazwa produktu & liczby zamówienia) może zostać wywołany w sposób standardowy, wysyłając argumentów według pozycji w kolejności, zdefiniowanych przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="87a61-113">For example, a function that prints order details (such as, seller name, order number & product name) can be called in the standard way by sending arguments by position, in the order defined by the function.</span></span>
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 <span data-ttu-id="87a61-114">Jeśli nie pamiętasz kolejności parametrów, ale znasz ich nazw, można wysyłać argumenty w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="87a61-114">If you do not remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 <span data-ttu-id="87a61-115">Argumenty nazwane również poprawić czytelność kodu, określając, co reprezentuje każdy argument.</span><span class="sxs-lookup"><span data-stu-id="87a61-115">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="87a61-116">W metodzie przykład poniżej `sellerName` nie może mieć wartość null lub biały znak.</span><span class="sxs-lookup"><span data-stu-id="87a61-116">In the example method below, the `sellerName` cannot be null or white space.</span></span> <span data-ttu-id="87a61-117">Oba `sellerName` i `productName` są typami parametrów, zamiast wysyłać argumentów według pozycji, dobrym pomysłem będzie używać argumentów nazwanych do odróżniania dwóch i unikanie pomyłek dla każdego, kto kodu.</span><span class="sxs-lookup"><span data-stu-id="87a61-117">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
 <span data-ttu-id="87a61-118">Nazwane argumenty, gdy jest używane z argumentów pozycyjnych, są prawidłowe tak długo, jak</span><span class="sxs-lookup"><span data-stu-id="87a61-118">Named arguments, when used with positional arguments, are valid as long as</span></span> 

- <span data-ttu-id="87a61-119">mogą one nie następuje argumenty pozycyjne, lub</span><span class="sxs-lookup"><span data-stu-id="87a61-119">they're not followed by any positional arguments, or</span></span>

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- <span data-ttu-id="87a61-120">_począwszy od C# 7.2_, są używane w poprawnej pozycji.</span><span class="sxs-lookup"><span data-stu-id="87a61-120">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="87a61-121">W przykładzie poniżej, parametr `orderNum` jest w prawidłowym położeniu, ale nie jest jawnie nazwane.</span><span class="sxs-lookup"><span data-stu-id="87a61-121">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 <span data-ttu-id="87a61-122">Jednak argumenty nazwane poza kolejnością jest nieprawidłowy, jeśli masz następuje argumentów pozycyjnych.</span><span class="sxs-lookup"><span data-stu-id="87a61-122">However, out-of-order named arguments are invalid if they're followed by positional arguments.</span></span>

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a><span data-ttu-id="87a61-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="87a61-123">Example</span></span>  
 <span data-ttu-id="87a61-124">Poniższy kod implementuje przykłady w tej sekcji oraz dodatkowe niektóre z nich.</span><span class="sxs-lookup"><span data-stu-id="87a61-124">The following code implements the examples from this section along with some additional ones.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a><span data-ttu-id="87a61-125">Argumenty opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="87a61-125">Optional Arguments</span></span>  
 <span data-ttu-id="87a61-126">Definicję metody, konstruktora, indeksatora lub delegata można określić, że jej parametry są wymagane lub czy są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="87a61-126">The definition of a method, constructor, indexer, or delegate can specify that its parameters are required or that they are optional.</span></span> <span data-ttu-id="87a61-127">Każde wywołanie należy podać argumenty dla wszystkich wymaganych parametrów, ale można pominąć argumenty dla parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="87a61-127">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>  
  
 <span data-ttu-id="87a61-128">Każdy parametr opcjonalny ma wartość domyślną, jako część jego definicji.</span><span class="sxs-lookup"><span data-stu-id="87a61-128">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="87a61-129">Jeśli żaden argument nie zostanie wysłany dla tego parametru, wartością domyślną jest używany.</span><span class="sxs-lookup"><span data-stu-id="87a61-129">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="87a61-130">Wartość domyślna musi być jedną z następujących typów wyrażeń:</span><span class="sxs-lookup"><span data-stu-id="87a61-130">A default value must be one of the following types of expressions:</span></span>  
  
-   <span data-ttu-id="87a61-131">wyrażenie stałe;</span><span class="sxs-lookup"><span data-stu-id="87a61-131">a constant expression;</span></span>  
  
-   <span data-ttu-id="87a61-132">wyrażenie w formie `new ValType()`, gdzie `ValType` jest typem wartości, takich jak [wyliczenia](../../../csharp/language-reference/keywords/enum.md) lub [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md);</span><span class="sxs-lookup"><span data-stu-id="87a61-132">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../../csharp/language-reference/keywords/enum.md) or a [struct](../../../csharp/programming-guide/classes-and-structs/structs.md);</span></span>  
  
-   <span data-ttu-id="87a61-133">wyrażenie w formie [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md), gdzie `ValType` jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="87a61-133">an expression of the form [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md),  where `ValType` is a value type.</span></span>  
  
 <span data-ttu-id="87a61-134">Opcjonalne parametry są definiowane na końcu listy parametrów po wszelkie wymagane parametry.</span><span class="sxs-lookup"><span data-stu-id="87a61-134">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="87a61-135">Obiekt wywołujący dostarcza argumentu jednego z kolejnych następujące parametry opcjonalne, wymagają podania dla wszystkich poprzednich parametry opcjonalne argumenty.</span><span class="sxs-lookup"><span data-stu-id="87a61-135">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="87a61-136">Rozdzielana przecinkami przerwy na liście argumentów nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="87a61-136">Comma-separated gaps in the argument list are not supported.</span></span> <span data-ttu-id="87a61-137">Na przykład w poniższym kodzie metodę wystąpienia `ExampleMethod` jest zdefiniowana za pomocą jednego wymagany i dwa parametry opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="87a61-137">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 <span data-ttu-id="87a61-138">Następujące wywołanie `ExampleMethod` powoduje błąd kompilatora, ponieważ argument zostanie podany, trzeci parametr, ale nie do drugiego.</span><span class="sxs-lookup"><span data-stu-id="87a61-138">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 <span data-ttu-id="87a61-139">Jednak jeśli znasz nazwę trzeci parametr służy nazwany argument do wykonania zadania.</span><span class="sxs-lookup"><span data-stu-id="87a61-139">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 <span data-ttu-id="87a61-140">Funkcja IntelliSense używa nawiasów, aby wskazać parametry opcjonalne, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="87a61-140">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="87a61-141">![Szybkie informacje technologii IntelliSense dla metody ExampleMethod. ](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span><span class="sxs-lookup"><span data-stu-id="87a61-141">![IntelliSense Quick Info for method ExampleMethod.](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span></span>  
<span data-ttu-id="87a61-142">Parametry opcjonalne w ExampleMethod</span><span class="sxs-lookup"><span data-stu-id="87a61-142">Optional parameters in ExampleMethod</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87a61-143">Można również zadeklarować następujące parametry opcjonalne przy użyciu platformy .NET <xref:System.Runtime.InteropServices.OptionalAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="87a61-143">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="87a61-144">`OptionalAttribute` Parametry nie wymagają wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="87a61-144">`OptionalAttribute` parameters do not require a default value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87a61-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="87a61-145">Example</span></span>  
 <span data-ttu-id="87a61-146">W poniższym przykładzie, Konstruktor `ExampleClass` ma jeden parametr, który jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="87a61-146">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="87a61-147">Metodę wystąpienia `ExampleMethod` ma jeden parametr wymagany, `required`i dwa parametry opcjonalne, `optionalstr` i `optionalint`.</span><span class="sxs-lookup"><span data-stu-id="87a61-147">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="87a61-148">Kod w `Main` pokazano różne sposoby, w którym można wywołać konstruktora i metody.</span><span class="sxs-lookup"><span data-stu-id="87a61-148">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a><span data-ttu-id="87a61-149">Interfejsy modelu COM</span><span class="sxs-lookup"><span data-stu-id="87a61-149">COM Interfaces</span></span>  
 <span data-ttu-id="87a61-150">Argumenty nazwane i opcjonalne oraz obsługę obiektów dynamicznych i inne ulepszenia znacznie poprawić współdziałanie z interfejsów API modelu COM, takich jak interfejsy API usługi Automation pakietu Office.</span><span class="sxs-lookup"><span data-stu-id="87a61-150">Named and optional arguments, along with support for dynamic objects and other enhancements, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>  
  
 <span data-ttu-id="87a61-151">Na przykład <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> metodę w programie Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interfejs ma siedem parametry, z których wszystkie są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="87a61-151">For example, the <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method in the Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="87a61-152">Te parametry są wyświetlane na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="87a61-152">These parameters are shown in the following illustration.</span></span>  
  
 <span data-ttu-id="87a61-153">![Szybkie informacje technologii IntelliSense dla metody AutoFormat. ](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span><span class="sxs-lookup"><span data-stu-id="87a61-153">![IntelliSense Quick Info for the AutoFormat method.](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span></span>  
<span data-ttu-id="87a61-154">Autoformat — parametry</span><span class="sxs-lookup"><span data-stu-id="87a61-154">AutoFormat parameters</span></span>  
  
 <span data-ttu-id="87a61-155">W języku C# 3.0 i wcześniejszych wersjach argument jest wymagany dla każdego parametru, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="87a61-155">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 <span data-ttu-id="87a61-156">Jednak znacznie upraszczają wywołanie `AutoFormat` przy użyciu argumentów nazwanych i opcjonalnych, wprowadzona w języku C# 4.0.</span><span class="sxs-lookup"><span data-stu-id="87a61-156">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="87a61-157">Nazwę i opcjonalne argumenty umożliwiają pominięcia argumentu dla parametru opcjonalnego, jeśli nie chcesz zmienić wartość domyślną parametru.</span><span class="sxs-lookup"><span data-stu-id="87a61-157">Named and optional arguments enable you to omit the argument for an optional parameter if you do not want to change the parameter's default value.</span></span> <span data-ttu-id="87a61-158">W poniższym wywołaniu określono wartość tylko dla jednego z siedmiu parametrów.</span><span class="sxs-lookup"><span data-stu-id="87a61-158">In the following call, a value is specified for only one of the seven parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 <span data-ttu-id="87a61-159">Aby uzyskać więcej informacji i przykładów, zobacz [jak: Użycie argumentów nazwanych i opcjonalnych w programowaniu Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) i [jak: Dostęp do obiektów międzyoperacyjności pakietu Office przy użyciu Visual C# funkcji](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="87a61-159">For more information and examples, see [How to: Use Named and Optional Arguments in Office Programming](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
## <a name="overload-resolution"></a><span data-ttu-id="87a61-160">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="87a61-160">Overload Resolution</span></span>  
 <span data-ttu-id="87a61-161">Użycie argumentów nazwanych i opcjonalnych wpływa na rozpoznanie przeciążenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="87a61-161">Use of named and optional arguments affects overload resolution in the following ways:</span></span>  
  
-   <span data-ttu-id="87a61-162">Metoda, indeksator lub Konstruktor jest kandydatem do wykonywania w przypadku każdego z jego parametrów jest opcjonalny albo odpowiada według nazwy lub pozycji, aby jeden argument w instrukcji wywołujące, i że argument można przekonwertować na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="87a61-162">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
  
-   <span data-ttu-id="87a61-163">Jeśli zostanie znalezione więcej niż jeden Release candidate, zasady rozpoznawania przeciążenia preferowanych konwersje są stosowane do argumentów, które są jawnie określone.</span><span class="sxs-lookup"><span data-stu-id="87a61-163">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="87a61-164">Pominięty Argumenty opcjonalne parametry są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="87a61-164">Omitted arguments for optional parameters are ignored.</span></span>  
  
-   <span data-ttu-id="87a61-165">Jeśli dwa kandydatów zostaną ocenione one równie dobrze, preferencji jest przesyłany do Release candidate, który nie ma parametrów opcjonalnych, które zostały pominięte argumentów w wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="87a61-165">If two candidates are judged to be equally good, preference goes to a candidate that does not have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="87a61-166">Jest to konsekwencją Ogólne preferencji w przeciążeniu rozdzielczości dla kandydatów, które mają mniej parametrów.</span><span class="sxs-lookup"><span data-stu-id="87a61-166">This is a consequence of a general preference in overload resolution for candidates that have fewer parameters.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="87a61-167">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="87a61-167">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="87a61-168">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87a61-168">See also</span></span>

- [<span data-ttu-id="87a61-169">Instrukcje: Użycie argumentów nazwanych i opcjonalnych w programowaniu Office</span><span class="sxs-lookup"><span data-stu-id="87a61-169">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="87a61-170">Używanie typu dynamicznego</span><span class="sxs-lookup"><span data-stu-id="87a61-170">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="87a61-171">Używanie konstruktorów</span><span class="sxs-lookup"><span data-stu-id="87a61-171">Using Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)
- [<span data-ttu-id="87a61-172">Używanie indeksatorów</span><span class="sxs-lookup"><span data-stu-id="87a61-172">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)
