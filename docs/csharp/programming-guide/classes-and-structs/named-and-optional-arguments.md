---
title: "Argumenty nazwane i opcjonalne (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
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
caps.latest.revision: "43"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4c57efa4027af5dd6b0476eb65845a39fc0b691
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="8685c-102">Argumenty nazwane i opcjonalne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="8685c-102">Named and Optional Arguments (C# Programming Guide)</span></span>
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]<span data-ttu-id="8685c-103">wprowadza argumenty nazwane i opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="8685c-103"> introduces named and optional arguments.</span></span> <span data-ttu-id="8685c-104">*Argumenty nazwane o* można określić argumentu dla parametru określonego przez skojarzenie argument o nazwie parametru, a nie parametru pozycji na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="8685c-104">*Named arguments* enable you to specify an argument for a particular parameter by associating the argument with the parameter's name rather than with the parameter's position in the parameter list.</span></span> <span data-ttu-id="8685c-105">*Argumenty opcjonalne* można pominąć argumenty dla niektórych parametrów.</span><span class="sxs-lookup"><span data-stu-id="8685c-105">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="8685c-106">Obie techniki można używać z metod, indeksatorów konstruktory i delegatów.</span><span class="sxs-lookup"><span data-stu-id="8685c-106">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>  
  
 <span data-ttu-id="8685c-107">Użycie argumentów nazwanych i opcjonalnych argumentach są oceniane w kolejności, w którym są wyświetlane na liście argumentów nie listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="8685c-107">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>  
  
 <span data-ttu-id="8685c-108">Parametry nazwane i opcjonalne, gdy jest używany razem umożliwiają podać argumenty tylko kilka parametrów z listy parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="8685c-108">Named and optional parameters, when used together, enable you to supply arguments for only a few parameters from a list of optional parameters.</span></span> <span data-ttu-id="8685c-109">Ta funkcja znacznie ułatwia wywołania do interfejsów modelu COM, takie jak interfejsy API Microsoft Office automatyzacji.</span><span class="sxs-lookup"><span data-stu-id="8685c-109">This capability greatly facilitates calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>  
  
## <a name="named-arguments"></a><span data-ttu-id="8685c-110">Argumenty nazwane</span><span class="sxs-lookup"><span data-stu-id="8685c-110">Named Arguments</span></span>  
 <span data-ttu-id="8685c-111">Argumenty nazwane pozbawione potrzebę do zapamiętania lub wyszukania kolejność parametrów na listach parametrem wywoływane metody.</span><span class="sxs-lookup"><span data-stu-id="8685c-111">Named arguments free you from the need to remember or to look up the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="8685c-112">Parametr dla każdego argumentu można określić nazwę parametru.</span><span class="sxs-lookup"><span data-stu-id="8685c-112">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="8685c-113">Na przykład funkcja, która wyświetla szczegóły zamówienia (takich jak nazwy sprzedawcy, kolejność numer & produktu nazwy), wysyłając argumentów według pozycji w kolejności, zdefiniowany przez funkcję można wywołać w sposób standardowy.</span><span class="sxs-lookup"><span data-stu-id="8685c-113">For example, a function that prints order details (such as, seller name, order number & product name) can be called in the standard way by sending arguments by position, in the order defined by the function.</span></span>
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 <span data-ttu-id="8685c-114">Jeśli nie pamięta kolejność parametrów, ale znasz ich nazw, możesz wysłać argumenty w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="8685c-114">If you do not remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 <span data-ttu-id="8685c-115">Argumenty nazwane również poprawić czytelność kodu, określając reprezentuje każdy argument.</span><span class="sxs-lookup"><span data-stu-id="8685c-115">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="8685c-116">W metodzie przykładzie poniżej `sellerName` nie może mieć wartości null ani być odstępem.</span><span class="sxs-lookup"><span data-stu-id="8685c-116">In the example method below, the `sellerName` cannot be null or whitespace.</span></span> <span data-ttu-id="8685c-117">Jednocześnie jako `sellerName` i `productName` są typu ciąg, zamiast wysyłać argumentów według pozycji, warto użyć nazwane argumenty do odróżniania dwóch i uniknąć pomyłek dla każdego odczytywania kod.</span><span class="sxs-lookup"><span data-stu-id="8685c-117">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
 <span data-ttu-id="8685c-118">Nazwane argumenty, gdy jest używany z argumenty pozycyjne, są prawidłowe tak długo, jak</span><span class="sxs-lookup"><span data-stu-id="8685c-118">Named arguments, when used with positional arguments, are valid as long as</span></span> 

- <span data-ttu-id="8685c-119">nie są one następuje argumenty pozycyjne lub</span><span class="sxs-lookup"><span data-stu-id="8685c-119">they're not followed by any positional arguments, or</span></span>

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- <span data-ttu-id="8685c-120">_począwszy od C# 7.2_, są używane w poprawnej pozycji.</span><span class="sxs-lookup"><span data-stu-id="8685c-120">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="8685c-121">W przykładzie poniżej parametr `orderNum` jest w prawidłowym miejscu, ale nie jest jawnie nazwane.</span><span class="sxs-lookup"><span data-stu-id="8685c-121">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 <span data-ttu-id="8685c-122">Jednak poza kolejnością nazwane argumenty są nieprawidłowe, jeśli jest następuje argumenty pozycyjne.</span><span class="sxs-lookup"><span data-stu-id="8685c-122">However, out-of-order named arguments are invalid if they're followed by positional arguments.</span></span>

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a><span data-ttu-id="8685c-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="8685c-123">Example</span></span>  
 <span data-ttu-id="8685c-124">Poniższy kod implementuje przykłady w tej sekcji oraz dodatkowe niektóre z nich.</span><span class="sxs-lookup"><span data-stu-id="8685c-124">The following code implements the examples from this section along with some additional ones.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]  
  
## <a name="optional-arguments"></a><span data-ttu-id="8685c-125">Argumenty opcjonalne</span><span class="sxs-lookup"><span data-stu-id="8685c-125">Optional Arguments</span></span>  
 <span data-ttu-id="8685c-126">Definicja metody, konstruktora, indeksatora lub delegata można określić, czy wymagane są jego parametrów lub że są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="8685c-126">The definition of a method, constructor, indexer, or delegate can specify that its parameters are required or that they are optional.</span></span> <span data-ttu-id="8685c-127">Każde wywołanie podać argumenty dla wszystkich wymaganych parametrów, ale można pominąć argumentów dla parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="8685c-127">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>  
  
 <span data-ttu-id="8685c-128">Każdy opcjonalny parametr ma wartość domyślną w ramach swojej definicji.</span><span class="sxs-lookup"><span data-stu-id="8685c-128">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="8685c-129">Jeśli argument nie jest wysyłany dla tego parametru, zostanie użyta domyślna wartość.</span><span class="sxs-lookup"><span data-stu-id="8685c-129">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="8685c-130">Wartość domyślna musi mieć jedną z następujących typów wyrażeń:</span><span class="sxs-lookup"><span data-stu-id="8685c-130">A default value must be one of the following types of expressions:</span></span>  
  
-   <span data-ttu-id="8685c-131">wyrażenie stałe;</span><span class="sxs-lookup"><span data-stu-id="8685c-131">a constant expression;</span></span>  
  
-   <span data-ttu-id="8685c-132">wyrażenie w postaci `new ValType()`, gdzie `ValType` jest typem wartości, takich jak [wyliczenia](../../../csharp/language-reference/keywords/enum.md) lub [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md);</span><span class="sxs-lookup"><span data-stu-id="8685c-132">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../../csharp/language-reference/keywords/enum.md) or a [struct](../../../csharp/programming-guide/classes-and-structs/structs.md);</span></span>  
  
-   <span data-ttu-id="8685c-133">wyrażenie w postaci [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md), gdzie `ValType` jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="8685c-133">an expression of the form [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md),  where `ValType` is a value type.</span></span>  
  
 <span data-ttu-id="8685c-134">Parametry opcjonalne są definiowane na końcu listy parametrów po wszelkie wymagane parametry.</span><span class="sxs-lookup"><span data-stu-id="8685c-134">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="8685c-135">Jeśli element wywołujący zapewnia argumentu dla dowolnego kolejne parametry opcjonalne, podaj argumenty dla wszystkich powyższych parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="8685c-135">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="8685c-136">Rozdzielana przecinkami luk w liście argumentów nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="8685c-136">Comma-separated gaps in the argument list are not supported.</span></span> <span data-ttu-id="8685c-137">Na przykład w poniższym kodzie metody wystąpienia `ExampleMethod` jest zdefiniowana z jednym wymagane i dwa parametry opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="8685c-137">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]  
  
 <span data-ttu-id="8685c-138">Następujące wywołanie do `ExampleMethod` powoduje błąd kompilatora, ponieważ argument podano trzeci parametr, ale nie dla drugiego.</span><span class="sxs-lookup"><span data-stu-id="8685c-138">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 <span data-ttu-id="8685c-139">Jednak jeśli znasz nazwę trzeci parametr służy nazwany argument do wykonania zadania.</span><span class="sxs-lookup"><span data-stu-id="8685c-139">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 <span data-ttu-id="8685c-140">IntelliSense używa nawiasów w celu wskazania następujące parametry opcjonalne, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="8685c-140">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="8685c-141">![Szybkie informacje funkcji IntelliSense dla metody ExampleMethod. ] (../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span><span class="sxs-lookup"><span data-stu-id="8685c-141">![IntelliSense Quick Info for method ExampleMethod.](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span></span>  
<span data-ttu-id="8685c-142">Parametry opcjonalne w ExampleMethod</span><span class="sxs-lookup"><span data-stu-id="8685c-142">Optional parameters in ExampleMethod</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8685c-143">Parametry opcjonalne może deklarować także przy użyciu programu .NET <xref:System.Runtime.InteropServices.OptionalAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="8685c-143">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="8685c-144">`OptionalAttribute`Parametry nie wymagają wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="8685c-144">`OptionalAttribute` parameters do not require a default value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8685c-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="8685c-145">Example</span></span>  
 <span data-ttu-id="8685c-146">W poniższym przykładzie, Konstruktor `ExampleClass` ma jeden parametr, który jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="8685c-146">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="8685c-147">Metoda wystąpienia `ExampleMethod` ma jeden wymagany parametr `required`i dwa parametry opcjonalne, `optionalstr` i `optionalint`.</span><span class="sxs-lookup"><span data-stu-id="8685c-147">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="8685c-148">Kod w `Main` przedstawiono różne sposoby, w którym można wywołać konstruktora i metody.</span><span class="sxs-lookup"><span data-stu-id="8685c-148">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]  
  
## <a name="com-interfaces"></a><span data-ttu-id="8685c-149">Interfejsy modelu COM</span><span class="sxs-lookup"><span data-stu-id="8685c-149">COM Interfaces</span></span>  
 <span data-ttu-id="8685c-150">Argumenty nazwane i opcjonalne mechanizmy obiekty dynamiczne i inne rozszerzenia znacznie zwiększyć współdziałanie z interfejsów API modelu COM, takie jak interfejsów API automatyzacji pakietu Office.</span><span class="sxs-lookup"><span data-stu-id="8685c-150">Named and optional arguments, along with support for dynamic objects and other enhancements, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>  
  
 <span data-ttu-id="8685c-151">Na przykład [Autoformatowanie](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.autoformat(v=office.15).aspx) metody w programie Microsoft Office Excel [zakres](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range(v=office.15).aspx) interfejs ma siedmiu parametrów, które są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="8685c-151">For example, the [AutoFormat](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.autoformat(v=office.15).aspx) method in the Microsoft Office Excel [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range(v=office.15).aspx) interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="8685c-152">Te parametry są wyświetlane na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="8685c-152">These parameters are shown in the following illustration.</span></span>  
  
 <span data-ttu-id="8685c-153">![Szybkie informacje funkcji IntelliSense dla metody Autoformatowanie. ] (../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span><span class="sxs-lookup"><span data-stu-id="8685c-153">![IntelliSense Quick Info for the AutoFormat method.](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span></span>  
<span data-ttu-id="8685c-154">Parametry Autoformatowanie</span><span class="sxs-lookup"><span data-stu-id="8685c-154">AutoFormat parameters</span></span>  
  
 <span data-ttu-id="8685c-155">W języku C# 3.0 i wcześniejszych wersjach, wymagany jest argument dla każdego parametru, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8685c-155">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]  
  
 <span data-ttu-id="8685c-156">Jednak może bardzo uprościć wywołanie `AutoFormat` przy użyciu argumentów nazwanych i opcjonalnych wprowadzono w języku C# w wersji 4.0.</span><span class="sxs-lookup"><span data-stu-id="8685c-156">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="8685c-157">Nazwę i opcjonalne argumenty umożliwiają Pomiń argumentu dla parametru opcjonalnego, jeśli nie chcesz zmienić wartość domyślna parametru.</span><span class="sxs-lookup"><span data-stu-id="8685c-157">Named and optional arguments enable you to omit the argument for an optional parameter if you do not want to change the parameter's default value.</span></span> <span data-ttu-id="8685c-158">W poniższym wywołaniu określono wartość tylko dla jednego z parametrów siedem.</span><span class="sxs-lookup"><span data-stu-id="8685c-158">In the following call, a value is specified for only one of the seven parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]  
  
 <span data-ttu-id="8685c-159">Aby uzyskać dodatkowe informacje i przykłady, zobacz [porady: stosowanie nazwanych i argumentów opcjonalnych w programowaniu Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) i [porady: dostępu do obiektów międzyoperacyjności pakietu Office za pomocą Visual C# funkcji](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="8685c-159">For more information and examples, see [How to: Use Named and Optional Arguments in Office Programming](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
## <a name="overload-resolution"></a><span data-ttu-id="8685c-160">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="8685c-160">Overload Resolution</span></span>  
 <span data-ttu-id="8685c-161">Użycie argumentów nazwanych i opcjonalnych wpływa na rozpoznanie przeciążenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8685c-161">Use of named and optional arguments affects overload resolution in the following ways:</span></span>  
  
-   <span data-ttu-id="8685c-162">Metoda, indeksator lub Konstruktor jest kandydatem do wykonania, jeśli każdego z jego parametrów jest opcjonalny, albo odpowiada według nazwy lub stanie pojedynczy argument w instrukcji wywołującego, oraz że argument można przekonwertować na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="8685c-162">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
  
-   <span data-ttu-id="8685c-163">Jeśli zostanie znaleziony więcej niż jednego kandydata, zasady rozpoznawania przeciążenia preferowanych konwersje są stosowane do argumentów, które zostały jawnie określone.</span><span class="sxs-lookup"><span data-stu-id="8685c-163">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="8685c-164">Pominięcia Argumenty opcjonalne parametry są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="8685c-164">Omitted arguments for optional parameters are ignored.</span></span>  
  
-   <span data-ttu-id="8685c-165">Jeśli dwa kandydatów zostaną ocenione jako jednakowo dobry, preferencji prowadzi do kandydujących, który nie ma następujące parametry opcjonalne dla których argumenty zostały pominięte w wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="8685c-165">If two candidates are judged to be equally good, preference goes to a candidate that does not have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="8685c-166">Jest to konsekwencją Ogólne preferencji w wiązaniem dla elementów, które mają mniej parametrów.</span><span class="sxs-lookup"><span data-stu-id="8685c-166">This is a consequence of a general preference in overload resolution for candidates that have fewer parameters.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="8685c-167">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8685c-167">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8685c-168">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8685c-168">See Also</span></span>  
 [<span data-ttu-id="8685c-169">Instrukcje: użycie argumentów nazwanych i opcjonalnych w programowaniu Office</span><span class="sxs-lookup"><span data-stu-id="8685c-169">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
 [<span data-ttu-id="8685c-170">Używanie typu dynamicznego</span><span class="sxs-lookup"><span data-stu-id="8685c-170">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [<span data-ttu-id="8685c-171">Używanie konstruktorów</span><span class="sxs-lookup"><span data-stu-id="8685c-171">Using Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
 [<span data-ttu-id="8685c-172">Używanie indeksatorów</span><span class="sxs-lookup"><span data-stu-id="8685c-172">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)
