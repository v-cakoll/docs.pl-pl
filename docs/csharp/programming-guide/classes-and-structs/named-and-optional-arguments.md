---
title: Argumenty nazwane i opcjonalne — przewodnik programowania języka C#
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
ms.openlocfilehash: 15b685248730c1f742035612a201d97d180bbc41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399813"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="bbc12-102">Argumenty nazwane i opcjonalne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="bbc12-102">Named and Optional Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="bbc12-103">C# 4 wprowadza nazwane i opcjonalne argumenty.</span><span class="sxs-lookup"><span data-stu-id="bbc12-103">C# 4 introduces named and optional arguments.</span></span> <span data-ttu-id="bbc12-104">*Nazwane argumenty* umożliwiają określenie argumentu dla określonego parametru, kojarząc argument z nazwą parametru, a nie z pozycją parametru na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="bbc12-104">*Named arguments* enable you to specify an argument for a particular parameter by associating the argument with the parameter's name rather than with the parameter's position in the parameter list.</span></span> <span data-ttu-id="bbc12-105">*Opcjonalne argumenty* umożliwiają pominięcie argumentów dla niektórych parametrów.</span><span class="sxs-lookup"><span data-stu-id="bbc12-105">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="bbc12-106">Obie techniki mogą być używane z metodami, indeksatorów, konstruktorów i delegatów.</span><span class="sxs-lookup"><span data-stu-id="bbc12-106">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>  
  
 <span data-ttu-id="bbc12-107">W przypadku używania argumentów nazwanych i opcjonalnych argumenty są oceniane w kolejności, w jakiej pojawiają się na liście argumentów, a nie na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="bbc12-107">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>  
  
 <span data-ttu-id="bbc12-108">Parametry nazwane i opcjonalne, gdy są używane razem, umożliwiają dostarczanie argumentów tylko dla kilku parametrów z listy parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="bbc12-108">Named and optional parameters, when used together, enable you to supply arguments for only a few parameters from a list of optional parameters.</span></span> <span data-ttu-id="bbc12-109">Ta funkcja znacznie ułatwia wywołania interfejsów COM, takich jak interfejsy API automatyzacji pakietu Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="bbc12-109">This capability greatly facilitates calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>  
  
## <a name="named-arguments"></a><span data-ttu-id="bbc12-110">Nazwane argumenty</span><span class="sxs-lookup"><span data-stu-id="bbc12-110">Named Arguments</span></span>  
 <span data-ttu-id="bbc12-111">Nazwane argumenty uwalniają cię od konieczności zapamiętywania lub wyszukiwania kolejności parametrów na listach parametrów wywoływanych metod.</span><span class="sxs-lookup"><span data-stu-id="bbc12-111">Named arguments free you from the need to remember or to look up the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="bbc12-112">Parametr dla każdego argumentu można określić według nazwy parametru.</span><span class="sxs-lookup"><span data-stu-id="bbc12-112">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="bbc12-113">Na przykład funkcja, która drukuje szczegóły zamówienia (takie jak nazwa sprzedającego, numer zamówienia & nazwa produktu) można wywołać w standardowy sposób, wysyłając argumenty według pozycji, w kolejności zdefiniowanej przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="bbc12-113">For example, a function that prints order details (such as, seller name, order number & product name) can be called in the standard way by sending arguments by position, in the order defined by the function.</span></span>
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 <span data-ttu-id="bbc12-114">Jeśli nie pamiętasz kolejności parametrów, ale znasz ich nazwy, możesz wysłać argumenty w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="bbc12-114">If you do not remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 <span data-ttu-id="bbc12-115">Nazwane argumenty również poprawić czytelność kodu, identyfikując, co reprezentuje każdy argument.</span><span class="sxs-lookup"><span data-stu-id="bbc12-115">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="bbc12-116">W poniższej metodzie `sellerName` przykładowej nie może być null lub biały znak.</span><span class="sxs-lookup"><span data-stu-id="bbc12-116">In the example method below, the `sellerName` cannot be null or white space.</span></span> <span data-ttu-id="bbc12-117">Ponieważ `sellerName` oba `productName` i są typy ciągów, zamiast wysyłania argumentów według pozycji, ma sens użycie nazwanych argumentów do rozróżniania dwóch i zmniejszyć zamieszanie dla każdego, kto czyta kod.</span><span class="sxs-lookup"><span data-stu-id="bbc12-117">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
 <span data-ttu-id="bbc12-118">Nazwane argumenty, używane z argumentami pozycyjnymi, są prawidłowe tak długo, jak</span><span class="sxs-lookup"><span data-stu-id="bbc12-118">Named arguments, when used with positional arguments, are valid as long as</span></span>

- <span data-ttu-id="bbc12-119">nie następują po nimi żadne argumenty pozycyjne, lub</span><span class="sxs-lookup"><span data-stu-id="bbc12-119">they're not followed by any positional arguments, or</span></span>

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- <span data-ttu-id="bbc12-120">_począwszy od C# 7.2_, są one używane we właściwej pozycji.</span><span class="sxs-lookup"><span data-stu-id="bbc12-120">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="bbc12-121">W poniższym przykładzie `orderNum` parametr znajduje się we właściwej pozycji, ale nie jest jawnie nazwany.</span><span class="sxs-lookup"><span data-stu-id="bbc12-121">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 <span data-ttu-id="bbc12-122">Argumenty pozycyjne, które następują po wszystkich poza kolejnością nazwanych argumentów są nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="bbc12-122">Positional arguments that follow any out-of-order named arguments are invalid.</span></span>

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a><span data-ttu-id="bbc12-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="bbc12-123">Example</span></span>  
 <span data-ttu-id="bbc12-124">Poniższy kod implementuje przykłady z tej sekcji wraz z kilkoma dodatkowymi.</span><span class="sxs-lookup"><span data-stu-id="bbc12-124">The following code implements the examples from this section along with some additional ones.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a><span data-ttu-id="bbc12-125">Argumenty opcjonalne</span><span class="sxs-lookup"><span data-stu-id="bbc12-125">Optional Arguments</span></span>  
 <span data-ttu-id="bbc12-126">Definicja metody, konstruktora, indeksatora lub delegata można określić, że jego parametry są wymagane lub że są one opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="bbc12-126">The definition of a method, constructor, indexer, or delegate can specify that its parameters are required or that they are optional.</span></span> <span data-ttu-id="bbc12-127">Każde wywołanie musi zawierać argumenty dla wszystkich wymaganych parametrów, ale można pominąć argumenty dla parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="bbc12-127">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>  
  
 <span data-ttu-id="bbc12-128">Każdy parametr opcjonalny ma wartość domyślną jako część jego definicji.</span><span class="sxs-lookup"><span data-stu-id="bbc12-128">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="bbc12-129">Jeśli dla tego parametru nie zostanie wysłany żaden argument, używana jest wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="bbc12-129">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="bbc12-130">Wartość domyślna musi być jednym z następujących typów wyrażeń:</span><span class="sxs-lookup"><span data-stu-id="bbc12-130">A default value must be one of the following types of expressions:</span></span>  
  
- <span data-ttu-id="bbc12-131">wyrażenie stałe;</span><span class="sxs-lookup"><span data-stu-id="bbc12-131">a constant expression;</span></span>  
  
- <span data-ttu-id="bbc12-132">wyrażenie formularza `new ValType()`, gdzie `ValType` jest typem wartości, takim jak [wyliczenie](../../language-reference/builtin-types/enum.md) lub [struktura;](../../language-reference/builtin-types/struct.md)</span><span class="sxs-lookup"><span data-stu-id="bbc12-132">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../language-reference/builtin-types/enum.md) or a [struct](../../language-reference/builtin-types/struct.md);</span></span>  
  
- <span data-ttu-id="bbc12-133">wyrażenie domyślnego formularza [(ValType),](../../language-reference/operators/default.md) `ValType` gdzie jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="bbc12-133">an expression of the form [default(ValType)](../../language-reference/operators/default.md),  where `ValType` is a value type.</span></span>  
  
 <span data-ttu-id="bbc12-134">Parametry opcjonalne są definiowane na końcu listy parametrów, po wszelkich wymaganych parametrach.</span><span class="sxs-lookup"><span data-stu-id="bbc12-134">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="bbc12-135">Jeśli obiekt wywołujący zawiera argument dla jednego z kolejnych parametrów opcjonalnych, musi podać argumenty dla wszystkich poprzednich parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="bbc12-135">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="bbc12-136">Odstępy oddzielone przecinkami na liście argumentów nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="bbc12-136">Comma-separated gaps in the argument list are not supported.</span></span> <span data-ttu-id="bbc12-137">Na przykład w poniższym kodzie metoda `ExampleMethod` wystąpienia jest zdefiniowana z jednym wymaganym i dwoma parametrami opcjonalnymi.</span><span class="sxs-lookup"><span data-stu-id="bbc12-137">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 <span data-ttu-id="bbc12-138">Następujące wywołanie `ExampleMethod` powoduje błąd kompilatora, ponieważ argument jest podany dla trzeciego parametru, ale nie dla drugiego.</span><span class="sxs-lookup"><span data-stu-id="bbc12-138">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 <span data-ttu-id="bbc12-139">Jeśli jednak znasz nazwę trzeciego parametru, możesz użyć nazwanego argumentu do wykonania zadania.</span><span class="sxs-lookup"><span data-stu-id="bbc12-139">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 <span data-ttu-id="bbc12-140">IntelliSense używa nawiasów do wskazywania parametrów opcjonalnych, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="bbc12-140">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration:</span></span>  
  
 ![Zrzut ekranu przedstawiający szybkie informacje intelliSense dla metody ExampleMethod.](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)  
  
> [!NOTE]
> <span data-ttu-id="bbc12-142">Można również zadeklarować parametry opcjonalne <xref:System.Runtime.InteropServices.OptionalAttribute> przy użyciu klasy .NET.</span><span class="sxs-lookup"><span data-stu-id="bbc12-142">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="bbc12-143">`OptionalAttribute`parametry nie wymagają wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="bbc12-143">`OptionalAttribute` parameters do not require a default value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbc12-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="bbc12-144">Example</span></span>  
 <span data-ttu-id="bbc12-145">W poniższym przykładzie konstruktor ma `ExampleClass` jeden parametr, który jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="bbc12-145">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="bbc12-146">Metoda `ExampleMethod` instancji ma jeden `required`wymagany parametr i `optionalstr` dwa `optionalint`parametry opcjonalne i .</span><span class="sxs-lookup"><span data-stu-id="bbc12-146">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="bbc12-147">Kod w `Main` pokazuje różne sposoby, w których można wywołać konstruktora i metody.</span><span class="sxs-lookup"><span data-stu-id="bbc12-147">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a><span data-ttu-id="bbc12-148">Interfejsy COM</span><span class="sxs-lookup"><span data-stu-id="bbc12-148">COM Interfaces</span></span>  
 <span data-ttu-id="bbc12-149">Nazwane i opcjonalne argumenty, a także obsługa obiektów dynamicznych i innych ulepszeń znacznie zwiększają współdziałanie z interfejsami ComI, takimi jak interfejsy API automatyzacji pakietu Office.</span><span class="sxs-lookup"><span data-stu-id="bbc12-149">Named and optional arguments, along with support for dynamic objects and other enhancements, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>  
  
 <span data-ttu-id="bbc12-150">Na przykład <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> metoda w interfejsie <xref:Microsoft.Office.Interop.Excel.Range> programu Microsoft Office Excel ma siedem parametrów, z których wszystkie są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="bbc12-150">For example, the <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method in the Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="bbc12-151">Parametry te przedstawiono na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="bbc12-151">These parameters are shown in the following illustration:</span></span>  
  
 ![Zrzut ekranu przedstawiający szybkie informacje intelliSense dla metody Autoformatowania.](./media/named-and-optional-arguments/autoformat-method-parameters.png)  
  
 <span data-ttu-id="bbc12-153">W języku C# 3.0 i wcześniejszych wersjach dla każdego parametru wymagany jest argument, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bbc12-153">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 <span data-ttu-id="bbc12-154">Można jednak znacznie uprościć `AutoFormat` wywołanie przy użyciu argumentów nazwanych i opcjonalnych, wprowadzonych w języku C# 4.0.</span><span class="sxs-lookup"><span data-stu-id="bbc12-154">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="bbc12-155">Nazwane i opcjonalne argumenty umożliwiają pominięcie argumentu dla parametru opcjonalnego, jeśli nie chcesz zmieniać wartości domyślnej parametru.</span><span class="sxs-lookup"><span data-stu-id="bbc12-155">Named and optional arguments enable you to omit the argument for an optional parameter if you do not want to change the parameter's default value.</span></span> <span data-ttu-id="bbc12-156">W następującym wywołaniu wartość jest określona tylko dla jednego z siedmiu parametrów.</span><span class="sxs-lookup"><span data-stu-id="bbc12-156">In the following call, a value is specified for only one of the seven parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 <span data-ttu-id="bbc12-157">Aby uzyskać więcej informacji i przykładów, zobacz [Jak używać nazwanych i opcjonalnych argumentów w programowaniu pakietu Office](./how-to-use-named-and-optional-arguments-in-office-programming.md) i jak uzyskać dostęp do obiektów pakietu Office [interop przy użyciu funkcji języka C#.](../interop/how-to-access-office-onterop-objects.md)</span><span class="sxs-lookup"><span data-stu-id="bbc12-157">For more information and examples, see [How to use named and optional arguments in Office programming](./how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to access Office interop objects by using C# features](../interop/how-to-access-office-onterop-objects.md).</span></span>  
  
## <a name="overload-resolution"></a><span data-ttu-id="bbc12-158">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="bbc12-158">Overload Resolution</span></span>  
 <span data-ttu-id="bbc12-159">Użycie nazwanych i opcjonalnych argumentów wpływa na rozpoznawanie przeciążenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bbc12-159">Use of named and optional arguments affects overload resolution in the following ways:</span></span>  
  
- <span data-ttu-id="bbc12-160">Metoda, indeksator lub konstruktor jest kandydatem do wykonania, jeśli każdy z jego parametrów jest opcjonalny lub odpowiada, według nazwy lub pozycji, pojedynczemu argumentowi w instrukcji wywołującej, a ten argument można przekonwertować na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="bbc12-160">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
  
- <span data-ttu-id="bbc12-161">Jeśli zostanie znaleziony więcej niż jeden kandydat, reguły rozpoznawania przeciążenia dla preferowanych konwersji są stosowane do argumentów, które są jawnie określone.</span><span class="sxs-lookup"><span data-stu-id="bbc12-161">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="bbc12-162">Pominięte argumenty dla parametrów opcjonalnych są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="bbc12-162">Omitted arguments for optional parameters are ignored.</span></span>  
  
- <span data-ttu-id="bbc12-163">Jeśli dwóch kandydatów zostanie ocenionych jako równie dobre, preferencja trafia do kandydata, który nie ma opcjonalnych parametrów, dla których argumenty zostały pominięte w zaproszeniu.</span><span class="sxs-lookup"><span data-stu-id="bbc12-163">If two candidates are judged to be equally good, preference goes to a candidate that does not have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="bbc12-164">Jest to konsekwencją ogólnej preferencji w rozpoznawaniu przeciążenia dla kandydatów, którzy mają mniej parametrów.</span><span class="sxs-lookup"><span data-stu-id="bbc12-164">This is a consequence of a general preference in overload resolution for candidates that have fewer parameters.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="bbc12-165">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bbc12-165">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bbc12-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bbc12-166">See also</span></span>

- [<span data-ttu-id="bbc12-167">Porada: użycie argumentów nazwanych i opcjonalnych w programowaniu pakietu Office</span><span class="sxs-lookup"><span data-stu-id="bbc12-167">How to use named and optional arguments in Office programming</span></span>](./how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="bbc12-168">Używanie typu dynamicznego</span><span class="sxs-lookup"><span data-stu-id="bbc12-168">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="bbc12-169">Używanie konstruktorów</span><span class="sxs-lookup"><span data-stu-id="bbc12-169">Using Constructors</span></span>](./using-constructors.md)
- [<span data-ttu-id="bbc12-170">Używanie indeksatorów</span><span class="sxs-lookup"><span data-stu-id="bbc12-170">Using Indexers</span></span>](../indexers/using-indexers.md)
