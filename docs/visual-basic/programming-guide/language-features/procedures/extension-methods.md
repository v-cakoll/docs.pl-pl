---
title: Metody rozszerzeń (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: d988ab36703bc20e6960d4b8ecc7a476d95ee9bc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72396012"
---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="11bac-102">Metody rozszerzeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11bac-102">Extension Methods (Visual Basic)</span></span>

<span data-ttu-id="11bac-103">Metody rozszerzające pozwalają deweloperom dodawać niestandardowe funkcje do typów danych, które są już zdefiniowane bez tworzenia nowego typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="11bac-103">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="11bac-104">Metody rozszerzające umożliwiają napisanie metody, która może być wywoływana, tak jakby była to metoda wystąpienia istniejącego typu.</span><span class="sxs-lookup"><span data-stu-id="11bac-104">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>

## <a name="remarks"></a><span data-ttu-id="11bac-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11bac-105">Remarks</span></span>

<span data-ttu-id="11bac-106">Metoda rozszerzenia może być tylko procedurą `Sub` lub `Function`.</span><span class="sxs-lookup"><span data-stu-id="11bac-106">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="11bac-107">Nie można zdefiniować właściwości rozszerzenia, pola lub zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="11bac-107">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="11bac-108">Wszystkie metody rozszerzenia muszą być oznaczone atrybutem rozszerzenia `<Extension>` z przestrzeni nazw <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> i muszą być zdefiniowane w [module](../../../language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="11bac-108">All extension methods must be marked with the extension attribute `<Extension>` from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace and must be defined in a [Module](../../../language-reference/statements/module-statement.md).</span></span> <span data-ttu-id="11bac-109">Jeśli Metoda rozszerzenia jest zdefiniowana poza modułem, kompilator Visual Basic generuje błąd [BC36551](../../../misc/bc36551.md), "metody rozszerzające można definiować tylko w modułach".</span><span class="sxs-lookup"><span data-stu-id="11bac-109">If an extension method is defined outside a module, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules".</span></span>

<span data-ttu-id="11bac-110">Pierwszy parametr w definicji metody rozszerzenia określa typ danych, które rozszerza Metoda.</span><span class="sxs-lookup"><span data-stu-id="11bac-110">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="11bac-111">Gdy metoda jest uruchamiana, pierwszy parametr jest powiązany z wystąpieniem typu danych, który wywołuje metodę.</span><span class="sxs-lookup"><span data-stu-id="11bac-111">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>

<span data-ttu-id="11bac-112">Atrybut `Extension` może być stosowany tylko do Visual Basic [`Module`](../../../language-reference/statements/module-statement.md), [`Sub`](../../../language-reference/statements/sub-statement.md)lub [`Function`](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="11bac-112">The `Extension` attribute can only be applied to a Visual Basic [`Module`](../../../language-reference/statements/module-statement.md), [`Sub`](../../../language-reference/statements/sub-statement.md), or [`Function`](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="11bac-113">Jeśli zastosujesz go do `Class` lub `Structure`, kompilator Visual Basic generuje błąd [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md), atrybut "Extension" może być stosowany tylko do deklaracji "module", "Sub" lub "Function".</span><span class="sxs-lookup"><span data-stu-id="11bac-113">If you apply it to a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md), "'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations".</span></span>

## <a name="example"></a><span data-ttu-id="11bac-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="11bac-114">Example</span></span>

<span data-ttu-id="11bac-115">W poniższym przykładzie zdefiniowano rozszerzenie `Print` dla typu danych <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11bac-115">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="11bac-116">Metoda używa `Console.WriteLine` do wyświetlania ciągu.</span><span class="sxs-lookup"><span data-stu-id="11bac-116">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="11bac-117">Parametr metody `Print` `aString` oznacza, że metoda rozszerza klasę <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11bac-117">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>

[!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]

<span data-ttu-id="11bac-118">Zauważ, że definicja metody rozszerzenia jest oznaczona atrybutem rozszerzenia `<Extension()>`.</span><span class="sxs-lookup"><span data-stu-id="11bac-118">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="11bac-119">Oznaczanie modułu, w którym jest zdefiniowana Metoda jest opcjonalne, ale każda Metoda rozszerzenia musi być oznaczona.</span><span class="sxs-lookup"><span data-stu-id="11bac-119">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <span data-ttu-id="11bac-120">Aby można było uzyskać dostęp do atrybutu rozszerzenia, należy zaimportować <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="11bac-120"><xref:System.Runtime.CompilerServices> must be imported in order to access the extension attribute.</span></span>

<span data-ttu-id="11bac-121">Metody rozszerzające mogą być deklarowane tylko w modułach.</span><span class="sxs-lookup"><span data-stu-id="11bac-121">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="11bac-122">Zazwyczaj moduł, w którym jest zdefiniowana Metoda rozszerzająca, nie jest tym samym modułem, w którym jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="11bac-122">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="11bac-123">Zamiast tego moduł, który zawiera metodę rozszerzenia, jest importowany, jeśli musi być, aby wprowadzić go do zakresu.</span><span class="sxs-lookup"><span data-stu-id="11bac-123">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="11bac-124">Gdy moduł, który zawiera `Print` jest w zakresie, Metoda może zostać wywołana, tak jakby była metodą zwykłego wystąpienia, która nie przyjmuje argumentów, takich jak `ToUpper`:</span><span class="sxs-lookup"><span data-stu-id="11bac-124">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>

[!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]

<span data-ttu-id="11bac-125">Następny przykład, `PrintAndPunctuate`, jest również rozszerzeniem dla <xref:System.String>, ten czas zdefiniowany przez dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="11bac-125">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="11bac-126">Pierwszy parametr, `aString`, określa, że Metoda rozszerzenia rozszerza <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11bac-126">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="11bac-127">Drugi parametr, `punc`, ma być ciągiem znaków interpunkcyjnych, które są przenoszone jako argument, gdy wywoływana jest metoda.</span><span class="sxs-lookup"><span data-stu-id="11bac-127">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="11bac-128">Metoda wyświetla ciąg, po którym następuje znak interpunkcji.</span><span class="sxs-lookup"><span data-stu-id="11bac-128">The method displays the string followed by the punctuation marks.</span></span>

[!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]

<span data-ttu-id="11bac-129">Metoda jest wywoływana przez wysłanie w argumencie ciągu dla `punc`: `example.PrintAndPunctuate(".")`</span><span class="sxs-lookup"><span data-stu-id="11bac-129">The method is called by sending in a string argument for `punc`: `example.PrintAndPunctuate(".")`</span></span>

<span data-ttu-id="11bac-130">Poniższy przykład pokazuje `Print` i `PrintAndPunctuate` zdefiniowane i wywołane.</span><span class="sxs-lookup"><span data-stu-id="11bac-130">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <span data-ttu-id="11bac-131"><xref:System.Runtime.CompilerServices> jest zaimportowana w module definicji w celu umożliwienia dostępu do atrybutu rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="11bac-131"><xref:System.Runtime.CompilerServices> is imported in the definition module in order to enable access to the extension attribute.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions

    <Extension()>
    Public Sub Print(aString As String)
        Console.WriteLine(aString)
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module
```

<span data-ttu-id="11bac-132">Następnie metody rozszerzające są wprowadzane do zakresu i wywoływane:</span><span class="sxs-lookup"><span data-stu-id="11bac-132">Next, the extension methods are brought into scope and called:</span></span>

```vb
Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example As String = "Example string"
        example.Print()

        example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")
    End Sub
End Module
```

<span data-ttu-id="11bac-133">Wszystko, co jest wymagane, aby można było uruchamiać te lub podobne metody rozszerzające, jest w zakresie.</span><span class="sxs-lookup"><span data-stu-id="11bac-133">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="11bac-134">Jeśli moduł, który zawiera metodę rozszerzenia, znajduje się w zakresie, jest widoczny w IntelliSense i może być wywoływany tak, jakby był zwykłą metodą wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="11bac-134">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>

<span data-ttu-id="11bac-135">Zwróć uwagę, że gdy metody są wywoływane, żaden argument nie jest wysyłany w przypadku pierwszego parametru.</span><span class="sxs-lookup"><span data-stu-id="11bac-135">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="11bac-136">Parametr `aString` w poprzednich definicjach metod jest powiązany z `example`, wystąpieniem `String`, które je wywołuje.</span><span class="sxs-lookup"><span data-stu-id="11bac-136">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="11bac-137">Kompilator użyje `example` jako argumentu wysłanego do pierwszego parametru.</span><span class="sxs-lookup"><span data-stu-id="11bac-137">The compiler will use `example` as the argument sent to the first parameter.</span></span>

<span data-ttu-id="11bac-138">Jeśli wywoływana jest metoda rozszerzająca dla obiektu, który jest ustawiony na `Nothing`, Metoda rozszerzenia zostanie wykonana.</span><span class="sxs-lookup"><span data-stu-id="11bac-138">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="11bac-139">Nie dotyczy to zwykłych metod wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="11bac-139">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="11bac-140">Można jawnie sprawdzić, czy `Nothing` w metodzie rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="11bac-140">You can explicitly check for `Nothing` in the extension method.</span></span>

## <a name="types-that-can-be-extended"></a><span data-ttu-id="11bac-141">Typy, które można rozszerzyć</span><span class="sxs-lookup"><span data-stu-id="11bac-141">Types that can be extended</span></span>

<span data-ttu-id="11bac-142">Można zdefiniować metodę rozszerzenia dla większości typów, które mogą być reprezentowane na liście parametrów Visual Basic, w tym następujące:</span><span class="sxs-lookup"><span data-stu-id="11bac-142">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>

- <span data-ttu-id="11bac-143">Klasy (typy referencyjne)</span><span class="sxs-lookup"><span data-stu-id="11bac-143">Classes (reference types)</span></span>
- <span data-ttu-id="11bac-144">Struktury (typy wartości)</span><span class="sxs-lookup"><span data-stu-id="11bac-144">Structures (value types)</span></span>
- <span data-ttu-id="11bac-145">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="11bac-145">Interfaces</span></span>
- <span data-ttu-id="11bac-146">Delegaty</span><span class="sxs-lookup"><span data-stu-id="11bac-146">Delegates</span></span>
- <span data-ttu-id="11bac-147">Argumenty ByRef i ByVal</span><span class="sxs-lookup"><span data-stu-id="11bac-147">ByRef and ByVal arguments</span></span>
- <span data-ttu-id="11bac-148">Parametry metody ogólnej</span><span class="sxs-lookup"><span data-stu-id="11bac-148">Generic method parameters</span></span>
- <span data-ttu-id="11bac-149">Tablice</span><span class="sxs-lookup"><span data-stu-id="11bac-149">Arrays</span></span>

<span data-ttu-id="11bac-150">Ponieważ pierwszy parametr określa typ danych, które rozszerza Metoda rozszerzenia, jest wymagany i nie może być opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="11bac-150">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="11bac-151">Z tego powodu parametry `Optional` i `ParamArray` nie mogą być pierwszym parametrem na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="11bac-151">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>

<span data-ttu-id="11bac-152">Metody rozszerzające nie są brane pod uwagę w późnych powiązaniach.</span><span class="sxs-lookup"><span data-stu-id="11bac-152">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="11bac-153">W poniższym przykładzie instrukcja `anObject.PrintMe()` zgłasza wyjątek <xref:System.MissingMemberException>, ten sam wyjątek, który jest wyświetlany, jeśli druga definicja metody rozszerzenia `PrintMe` została usunięta.</span><span class="sxs-lookup"><span data-stu-id="11bac-153">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>

[!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]

## <a name="best-practices"></a><span data-ttu-id="11bac-154">Najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="11bac-154">Best practices</span></span>

<span data-ttu-id="11bac-155">Metody rozszerzające zapewniają wygodny i zaawansowany sposób rozszerzania istniejącego typu.</span><span class="sxs-lookup"><span data-stu-id="11bac-155">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="11bac-156">Aby jednak użyć ich pomyślnie, należy wziąć pod uwagę pewne kwestie.</span><span class="sxs-lookup"><span data-stu-id="11bac-156">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="11bac-157">Te zagadnienia dotyczą głównie autorów bibliotek klas, ale mogą mieć wpływ na dowolną aplikację korzystającą z metod rozszerzających.</span><span class="sxs-lookup"><span data-stu-id="11bac-157">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>

<span data-ttu-id="11bac-158">Ogólnie rzecz biorąc, metody rozszerzające dodawane do typów, które nie są własnością, są bardziej podatne na metody rozszerzające, które są dodawane do kontrolowanych typów.</span><span class="sxs-lookup"><span data-stu-id="11bac-158">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="11bac-159">Wiele rzeczy może wystąpić w klasach, które nie są właścicielami, które mogą zakłócać metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="11bac-159">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>

- <span data-ttu-id="11bac-160">Jeśli istnieje jakikolwiek dostępny element członkowski wystąpienia, który ma sygnaturę zgodną z argumentami w instrukcji wywołującej, bez konwersji zawężających wymagane z argumentu do parametru, metoda wystąpienia zostanie użyta w preferencjach do dowolnej metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="11bac-160">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="11bac-161">W związku z tym, Jeśli odpowiednia metoda wystąpienia jest dodawana do klasy w pewnym momencie, istniejący element członkowski rozszerzenia, na którym bazuje, może stać się niedostępny.</span><span class="sxs-lookup"><span data-stu-id="11bac-161">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>

- <span data-ttu-id="11bac-162">Autor metody rozszerzenia nie może uniemożliwić innym programistom pisanie sprzecznych metod rozszerzenia, które mogą mieć pierwszeństwo przed oryginalnym rozszerzeniem.</span><span class="sxs-lookup"><span data-stu-id="11bac-162">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>

- <span data-ttu-id="11bac-163">Niezawodność można poprawić, umieszczając metody rozszerzające w ich własnym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="11bac-163">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="11bac-164">Odbiorcy biblioteki mogą następnie dołączyć przestrzeń nazw lub wykluczyć ją lub wybrać między przestrzeniami nazw, niezależnie od reszty biblioteki.</span><span class="sxs-lookup"><span data-stu-id="11bac-164">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>

- <span data-ttu-id="11bac-165">Może być bezpieczniejsze, aby można było zwiększyć interfejsy niż w celu zwiększenia klas, zwłaszcza jeśli nie jesteś własnością interfejsu lub klasy.</span><span class="sxs-lookup"><span data-stu-id="11bac-165">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="11bac-166">Zmiana w interfejsie ma wpływ na każdą klasę, która ją implementuje.</span><span class="sxs-lookup"><span data-stu-id="11bac-166">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="11bac-167">W związku z tym autor może być mniej prawdopodobnie dodawać lub zmieniać metody w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="11bac-167">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="11bac-168">Jeśli jednak Klasa implementuje dwa interfejsy, które mają metody rozszerzające o tej samej sygnaturze, żadna metoda rozszerzająca nie jest widoczna.</span><span class="sxs-lookup"><span data-stu-id="11bac-168">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>

- <span data-ttu-id="11bac-169">Rozwiń najbardziej konkretny typ.</span><span class="sxs-lookup"><span data-stu-id="11bac-169">Extend the most specific type you can.</span></span> <span data-ttu-id="11bac-170">W hierarchii typów, jeśli wybierzesz typ, z którego pochodzą wiele innych typów, istnieją warstwy możliwości do wprowadzenia metod wystąpienia lub innych metod rozszerzających, które mogą zakłócać pracę.</span><span class="sxs-lookup"><span data-stu-id="11bac-170">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>

## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="11bac-171">Metody rozszerzające, metody wystąpień i właściwości</span><span class="sxs-lookup"><span data-stu-id="11bac-171">Extension methods, instance methods, and properties</span></span>

<span data-ttu-id="11bac-172">Gdy metoda wystąpienia w zakresie ma sygnaturę zgodną z argumentami instrukcji wywołującej, metoda wystąpienia jest wybierana w preferencjach dla dowolnej metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="11bac-172">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="11bac-173">Metoda wystąpienia ma pierwszeństwo, nawet jeśli Metoda rozszerzenia jest lepszym dopasowaniem.</span><span class="sxs-lookup"><span data-stu-id="11bac-173">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="11bac-174">W poniższym przykładzie `ExampleClass` zawiera metodę wystąpienia o nazwie `ExampleMethod`, która ma jeden parametr typu `Integer`.</span><span class="sxs-lookup"><span data-stu-id="11bac-174">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="11bac-175">Metoda rozszerzająca `ExampleMethod` rozszerza `ExampleClass` i ma jeden parametr typu `Long`.</span><span class="sxs-lookup"><span data-stu-id="11bac-175">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>

[!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]

<span data-ttu-id="11bac-176">Pierwsze wywołanie `ExampleMethod` w poniższym kodzie wywołuje metodę rozszerzenia, ponieważ `arg1` jest `Long` i jest zgodny tylko z parametrem `Long` w metodzie rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="11bac-176">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="11bac-177">Drugie wywołanie `ExampleMethod` ma argument `Integer`, `arg2` i wywołuje metodę wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="11bac-177">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>

[!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]

<span data-ttu-id="11bac-178">Teraz należy odwrócić typy danych parametrów w dwóch metodach:</span><span class="sxs-lookup"><span data-stu-id="11bac-178">Now reverse the data types of the parameters in the two methods:</span></span>

[!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]

<span data-ttu-id="11bac-179">Tym razem kod w `Main` wywołuje metodę wystąpienia jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="11bac-179">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="11bac-180">Dzieje się tak, ponieważ obie `arg1` i `arg2` mają konwersję rozszerzającą na `Long`, a metoda wystąpienia ma pierwszeństwo przed metodą rozszerzenia w obu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="11bac-180">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>

[!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]

<span data-ttu-id="11bac-181">W związku z tym Metoda rozszerzająca nie może zastąpić istniejącej metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="11bac-181">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="11bac-182">Jednak jeśli Metoda rozszerzenia ma taką samą nazwę jak metoda wystąpienia, ale podpisy nie powodują konfliktu, można uzyskać dostęp do obu metod.</span><span class="sxs-lookup"><span data-stu-id="11bac-182">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="11bac-183">Na przykład jeśli Klasa `ExampleClass` zawiera metodę o nazwie `ExampleMethod`, która nie przyjmuje argumentów, metody rozszerzające o tej samej nazwie, ale różne podpisy są dozwolone, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="11bac-183">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>

[!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]

<span data-ttu-id="11bac-184">Dane wyjściowe z tego kodu są następujące:</span><span class="sxs-lookup"><span data-stu-id="11bac-184">The output from this code is as follows:</span></span>

```console
Extension method
Instance method
```

<span data-ttu-id="11bac-185">Sytuacja jest prostsza z właściwościami: Jeśli Metoda rozszerzenia ma taką samą nazwę jak właściwość klasy, która rozszerza, Metoda rozszerzenia nie jest widoczna i nie można uzyskać do niej dostępu.</span><span class="sxs-lookup"><span data-stu-id="11bac-185">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>

## <a name="extension-method-precedence"></a><span data-ttu-id="11bac-186">Pierwszeństwo metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="11bac-186">Extension method precedence</span></span>

<span data-ttu-id="11bac-187">Gdy dwie metody rozszerzające, które mają identyczne podpisy są w zakresie i są dostępne, zostanie wywołana wartość o wyższym priorytecie.</span><span class="sxs-lookup"><span data-stu-id="11bac-187">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="11bac-188">Pierwszeństwo metody rozszerzenia opiera się na mechanizmie używanym do przenoszenia metody do zakresu.</span><span class="sxs-lookup"><span data-stu-id="11bac-188">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="11bac-189">Na poniższej liście przedstawiono hierarchię pierwszeństwa, od najwyższego do najniższego.</span><span class="sxs-lookup"><span data-stu-id="11bac-189">The following list shows the precedence hierarchy, from highest to lowest.</span></span>

1. <span data-ttu-id="11bac-190">Metody rozszerzające zdefiniowane wewnątrz bieżącego modułu.</span><span class="sxs-lookup"><span data-stu-id="11bac-190">Extension methods defined inside the current module.</span></span>

2. <span data-ttu-id="11bac-191">Metody rozszerzające zdefiniowane wewnątrz typów danych w bieżącej przestrzeni nazw lub w jednym z jej obiektów nadrzędnych, z podrzędnymi przestrzeniami nazw mającymi wyższy priorytet niż nadrzędne przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="11bac-191">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>

3. <span data-ttu-id="11bac-192">Metody rozszerzające zdefiniowane wewnątrz dowolnego typu Importy w bieżącym pliku.</span><span class="sxs-lookup"><span data-stu-id="11bac-192">Extension methods defined inside any type imports in the current file.</span></span>

4. <span data-ttu-id="11bac-193">Metody rozszerzające zdefiniowane wewnątrz dowolnego importu przestrzeni nazw w bieżącym pliku.</span><span class="sxs-lookup"><span data-stu-id="11bac-193">Extension methods defined inside any namespace imports in the current file.</span></span>

5. <span data-ttu-id="11bac-194">Metody rozszerzające zdefiniowane wewnątrz dowolnego typu importu na poziomie projektu.</span><span class="sxs-lookup"><span data-stu-id="11bac-194">Extension methods defined inside any project-level type imports.</span></span>

6. <span data-ttu-id="11bac-195">Metody rozszerzające zdefiniowane wewnątrz dowolnego importu przestrzeni nazw na poziomie projektu.</span><span class="sxs-lookup"><span data-stu-id="11bac-195">Extension methods defined inside any project-level namespace imports.</span></span>

<span data-ttu-id="11bac-196">Jeśli pierwszeństwo nie rozwiąże niejednoznaczności, można użyć w pełni kwalifikowanej nazwy, aby określić wywoływaną metodę.</span><span class="sxs-lookup"><span data-stu-id="11bac-196">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="11bac-197">Jeśli metoda `Print` w poprzednim przykładzie jest zdefiniowana w module o nazwie `StringExtensions`, w pełni kwalifikowana nazwa to `StringExtensions.Print(example)` zamiast `example.Print()`.</span><span class="sxs-lookup"><span data-stu-id="11bac-197">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>

## <a name="see-also"></a><span data-ttu-id="11bac-198">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11bac-198">See also</span></span>

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="11bac-199">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="11bac-199">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [<span data-ttu-id="11bac-200">Module, instrukcja</span><span class="sxs-lookup"><span data-stu-id="11bac-200">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="11bac-201">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="11bac-201">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="11bac-202">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="11bac-202">Optional Parameters</span></span>](optional-parameters.md)
- [<span data-ttu-id="11bac-203">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="11bac-203">Parameter Arrays</span></span>](parameter-arrays.md)
- [<span data-ttu-id="11bac-204">Przegląd atrybutów</span><span class="sxs-lookup"><span data-stu-id="11bac-204">Attributes overview</span></span>](../../concepts/attributes/index.md)
- [<span data-ttu-id="11bac-205">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="11bac-205">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
