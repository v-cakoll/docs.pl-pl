---
title: Metody rozszerzeń (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: c34108b9eb53da77a48afb5d270dce9a32289c99
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731117"
---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="15cb2-102">Metody rozszerzeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15cb2-102">Extension Methods (Visual Basic)</span></span>
<span data-ttu-id="15cb2-103">Metody rozszerzające umożliwiają programistom dodawanie niestandardowych funkcji do typów danych, które są już zdefiniowane bez tworzenia nowego typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="15cb2-103">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="15cb2-104">Metody rozszerzające umożliwiają napisanie metody, która może być wywoływany tak, jakby jego była wystąpieniem metody istniejącego typu.</span><span class="sxs-lookup"><span data-stu-id="15cb2-104">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15cb2-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15cb2-105">Remarks</span></span>  
 <span data-ttu-id="15cb2-106">Metoda rozszerzenia może być tylko `Sub` procedury lub `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="15cb2-106">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="15cb2-107">Nie można zdefiniować właściwości rozszerzenia, pola lub zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="15cb2-107">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="15cb2-108">Wszystkie metody rozszerzenia muszą być oznaczone atrybutem rozszerzenia `<Extension()>` z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="15cb2-108">All extension methods must be marked with the extension attribute `<Extension()>` from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="15cb2-109">Pierwszy parametr w definicji metody rozszerzenie Określa typ danych, które rozszerza metoda.</span><span class="sxs-lookup"><span data-stu-id="15cb2-109">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="15cb2-110">Gdy metoda jest uruchomiona, pierwszy parametr jest powiązany do wystąpienia typu danych, który wywołuje tę metodę.</span><span class="sxs-lookup"><span data-stu-id="15cb2-110">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15cb2-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="15cb2-111">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="15cb2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="15cb2-112">Description</span></span>  
 <span data-ttu-id="15cb2-113">W poniższym przykładzie zdefiniowano `Print` rozszerzenie <xref:System.String> — typ danych.</span><span class="sxs-lookup"><span data-stu-id="15cb2-113">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="15cb2-114">Metoda używa `Console.WriteLine` do wyświetlenia ciągu.</span><span class="sxs-lookup"><span data-stu-id="15cb2-114">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="15cb2-115">Wartość parametru `Print` metody `aString`, ustala, że metoda rozszerza <xref:System.String> klasy.</span><span class="sxs-lookup"><span data-stu-id="15cb2-115">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#1](./codesnippet/VisualBasic/extension-methods_1.vb)]  
  
 <span data-ttu-id="15cb2-116">Należy zauważyć, że definicja metody rozszerzenia jest oznaczona atrybutem rozszerzenia `<Extension()>`.</span><span class="sxs-lookup"><span data-stu-id="15cb2-116">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="15cb2-117">Oznaczanie modułu, w którym metoda jest określona jest opcjonalne, ale każda metoda rozszerzenia musi być oznaczona.</span><span class="sxs-lookup"><span data-stu-id="15cb2-117">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <span data-ttu-id="15cb2-118"><xref:System.Runtime.CompilerServices> muszą być importowane w celu uzyskania dostępu do atrybutu rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="15cb2-118"><xref:System.Runtime.CompilerServices> must be imported in order to access the extension attribute.</span></span>  
  
 <span data-ttu-id="15cb2-119">Metody rozszerzenia mogą być deklarowane tylko w modułach.</span><span class="sxs-lookup"><span data-stu-id="15cb2-119">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="15cb2-120">Zazwyczaj moduł, w którym zdefiniowano metody rozszerzenia nie jest tym samym module, w którym jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="15cb2-120">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="15cb2-121">Zamiast tego modułu, który zawiera metodę rozszerzająca jest importowany, jeśli wymagane jest, aby wprowadzić dane do zakresu.</span><span class="sxs-lookup"><span data-stu-id="15cb2-121">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="15cb2-122">Po tym jak moduł zawierający `Print` jest w zakresie, można wywołać metody, tak jakby był metodą instancji zwykłej, która nie przyjmuje żadnych argumentów, takich jak `ToUpper`:</span><span class="sxs-lookup"><span data-stu-id="15cb2-122">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#2](./codesnippet/VisualBasic/extension-methods_2.vb)]  
  
 <span data-ttu-id="15cb2-123">Następny przykład `PrintAndPunctuate`, również jest rozszerzeniem <xref:System.String>, tym razem zdefiniowane za pomocą dwóch parametrów.</span><span class="sxs-lookup"><span data-stu-id="15cb2-123">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="15cb2-124">Pierwszy parametr `aString`, ustala, że metoda rozszerzenia rozszerza <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="15cb2-124">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="15cb2-125">Drugi parametr `punc`, ma być ciągiem znaków interpunkcyjnych, który jest przekazywany jako argument przy wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="15cb2-125">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="15cb2-126">Metoda wyświetla ciąg, a następnie znaków interpunkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="15cb2-126">The method displays the string followed by the punctuation marks.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#3](./codesnippet/VisualBasic/extension-methods_3.vb)]  
  
 <span data-ttu-id="15cb2-127">Metoda jest wywoływana przez wysłanie argumentu ciągu dla `punc`: `example.PrintAndPunctuate(".")`</span><span class="sxs-lookup"><span data-stu-id="15cb2-127">The method is called by sending in a string argument for `punc`: `example.PrintAndPunctuate(".")`</span></span>  
  
 <span data-ttu-id="15cb2-128">W poniższym przykładzie przedstawiono `Print` i `PrintAndPunctuate` zdefiniowane i wywoływane.</span><span class="sxs-lookup"><span data-stu-id="15cb2-128">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <span data-ttu-id="15cb2-129"><xref:System.Runtime.CompilerServices> jest importowany w module definicji w celu umożliwienia dostępu do atrybutu rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="15cb2-129"><xref:System.Runtime.CompilerServices> is imported in the definition module in order to enable access to the extension attribute.</span></span>  
  
### <a name="code"></a><span data-ttu-id="15cb2-130">Kod</span><span class="sxs-lookup"><span data-stu-id="15cb2-130">Code</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
  
    <Extension()>   
    Public Sub Print(ByVal aString As String)  
        Console.WriteLine(aString)  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="15cb2-131">Następnie metody rozszerzające są dostosowane do zakresu i o nazwie.</span><span class="sxs-lookup"><span data-stu-id="15cb2-131">Next, the extension methods are brought into scope and called.</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="15cb2-132">Komentarze</span><span class="sxs-lookup"><span data-stu-id="15cb2-132">Comments</span></span>  
 <span data-ttu-id="15cb2-133">Wszystko co jest wymagane, aby można było uruchomić te lub podobne metody rozszerzenia jest, aby były one w zakresie.</span><span class="sxs-lookup"><span data-stu-id="15cb2-133">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="15cb2-134">Jeśli moduł, który zawiera metodę rozszerzającą znajduje się w zakresie, jest widoczny w technologii IntelliSense i może być wywoływany tak, jakby był metodą instancji zwykłej.</span><span class="sxs-lookup"><span data-stu-id="15cb2-134">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>  
  
 <span data-ttu-id="15cb2-135">Należy zauważyć, że gdy metody są wywołane, żaden argument nie jest wysyłany jako pierwszy parametr.</span><span class="sxs-lookup"><span data-stu-id="15cb2-135">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="15cb2-136">Parametr `aString` w poprzedniej metody jest powiązana definicje `example`, wystąpienie `String` które je wywołuje.</span><span class="sxs-lookup"><span data-stu-id="15cb2-136">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="15cb2-137">Kompilator będzie używał `example` jako argumentu wysyłanego do pierwszego parametru.</span><span class="sxs-lookup"><span data-stu-id="15cb2-137">The compiler will use `example` as the argument sent to the first parameter.</span></span>  
  
 <span data-ttu-id="15cb2-138">Jeśli metoda rozszerzająca zostanie wywołana dla obiektu, który jest ustawiony na `Nothing`, metoda rozszerzająca zostanie wykonana.</span><span class="sxs-lookup"><span data-stu-id="15cb2-138">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="15cb2-139">To nie ma zastosowania do metod zwykłego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="15cb2-139">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="15cb2-140">Możesz jawnie szukać `Nothing` w metodzie rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="15cb2-140">You can explicitly check for `Nothing` in the extension method.</span></span>  
  
## <a name="types-that-can-be-extended"></a><span data-ttu-id="15cb2-141">Typy, które mogą zostać rozszerzone</span><span class="sxs-lookup"><span data-stu-id="15cb2-141">Types That Can Be Extended</span></span>  
 <span data-ttu-id="15cb2-142">Można zdefiniować metodę rozszerzenia w większości typów, które mogą być reprezentowane w liście parametrów języka Visual Basic, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="15cb2-142">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>  
  
-   <span data-ttu-id="15cb2-143">Klasy (typy odwołań)</span><span class="sxs-lookup"><span data-stu-id="15cb2-143">Classes (reference types)</span></span>  
  
-   <span data-ttu-id="15cb2-144">Struktury (typy wartości)</span><span class="sxs-lookup"><span data-stu-id="15cb2-144">Structures (value types)</span></span>  
  
-   <span data-ttu-id="15cb2-145">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="15cb2-145">Interfaces</span></span>  
  
-   <span data-ttu-id="15cb2-146">Delegaty</span><span class="sxs-lookup"><span data-stu-id="15cb2-146">Delegates</span></span>  
  
-   <span data-ttu-id="15cb2-147">Argumenty ByRef i ByVal</span><span class="sxs-lookup"><span data-stu-id="15cb2-147">ByRef and ByVal arguments</span></span>  
  
-   <span data-ttu-id="15cb2-148">Parametry metody ogólnej</span><span class="sxs-lookup"><span data-stu-id="15cb2-148">Generic method parameters</span></span>  
  
-   <span data-ttu-id="15cb2-149">Tablice</span><span class="sxs-lookup"><span data-stu-id="15cb2-149">Arrays</span></span>  
  
 <span data-ttu-id="15cb2-150">Ponieważ pierwszy parametr określa typ danych, który rozszerza metoda rozszerzenia, jest wymagana i nie może być opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="15cb2-150">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="15cb2-151">Z tego powodu `Optional` parametrów i `ParamArray` parametrów nie może być pierwszym parametrem na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="15cb2-151">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="15cb2-152">Metody rozszerzenia nie są uwzględniane w późnym wiązaniu.</span><span class="sxs-lookup"><span data-stu-id="15cb2-152">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="15cb2-153">W poniższym przykładzie instrukcja `anObject.PrintMe()` zgłasza <xref:System.MissingMemberException> wyjątek, ten sam wyjątek zostałby wyświetlony, gdyby drugi `PrintMe` definicja metody rozszerzenia zostały usunięte.</span><span class="sxs-lookup"><span data-stu-id="15cb2-153">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#9](./codesnippet/VisualBasic/extension-methods_4.vb)]  
  
## <a name="best-practices"></a><span data-ttu-id="15cb2-154">Najlepsze praktyki</span><span class="sxs-lookup"><span data-stu-id="15cb2-154">Best Practices</span></span>  
 <span data-ttu-id="15cb2-155">Metody rozszerzenia zapewniają wygodny, zaawansowany sposób rozszerzenia istniejącego typu.</span><span class="sxs-lookup"><span data-stu-id="15cb2-155">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="15cb2-156">Aby ich używać, istnieją pewne kwestie do rozważenia.</span><span class="sxs-lookup"><span data-stu-id="15cb2-156">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="15cb2-157">Te zagadnienia dotyczą głównie autorów bibliotek klas, ale mogą mieć wpływ na dowolnej aplikacji, która wykorzystuje metody rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="15cb2-157">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>  
  
 <span data-ttu-id="15cb2-158">Najogólniej mówiąc metody rozszerzenia, które można dodać do typów, które nie są jego własnością są bardziej narażone niż metody rozszerzające dodane do typów, które możesz kontrolować.</span><span class="sxs-lookup"><span data-stu-id="15cb2-158">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="15cb2-159">Kilka rzeczy, może wystąpić w klasach, których nie jesteś właścicielem, które mogą zakłócać Twoje rozszerzenia metody.</span><span class="sxs-lookup"><span data-stu-id="15cb2-159">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>  
  
-   <span data-ttu-id="15cb2-160">Jeśli istnieje jakikolwiek dostępny członek wystąpienia, który ma podpis, który jest zgodny z argumentami w instrukcji wywołujące, bez konwersji zawężającej wymaganej od argumentu do parametru, metoda wystąpienia będą używane zamiast dowolnej metody.</span><span class="sxs-lookup"><span data-stu-id="15cb2-160">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="15cb2-161">W związku z tym jeśli odpowiednia metoda wystąpienia jest dodawany do klasy w jakimś momencie, istniejący element członkowski rozszerzenia, które korzystają z może stać się niedostępny.</span><span class="sxs-lookup"><span data-stu-id="15cb2-161">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>  
  
-   <span data-ttu-id="15cb2-162">Autor metody rozszerzenia nie może uniemożliwić innym programistom od pisania niezgodnych metod rozszerzeń, które mogą mieć pierwszeństwo nad oryginalnym rozszerzeniem.</span><span class="sxs-lookup"><span data-stu-id="15cb2-162">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>  
  
-   <span data-ttu-id="15cb2-163">Możesz ulepszyć odporność umieszczając metody rozszerzeń w ich przestrzeniach nazw.</span><span class="sxs-lookup"><span data-stu-id="15cb2-163">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="15cb2-164">Konsumenci biblioteki mogą następnie włączyć obszar nazw lub go wykluczyć lub wybrać wśród obszarów nazw, niezależnie od pozostałej części biblioteki.</span><span class="sxs-lookup"><span data-stu-id="15cb2-164">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>  
  
-   <span data-ttu-id="15cb2-165">Bezpieczniejsze może być rozszerzenie interfejsów niż rozszerzenie klas, zwłaszcza, jeśli nie posiadasz interfejsu lub klasy.</span><span class="sxs-lookup"><span data-stu-id="15cb2-165">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="15cb2-166">Zmiany w interfejsie dotyczą każdej klasy, która implementuje go.</span><span class="sxs-lookup"><span data-stu-id="15cb2-166">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="15cb2-167">W związku z tym Autor może być mniej prawdopodobne dodać lub zmienić metodę w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="15cb2-167">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="15cb2-168">Jeśli jednak klasa implementuje dwa interfejsy, które mają metodę rozszerzającą o tej samej sygnaturze, żadna metoda rozszerzenia jest widoczne.</span><span class="sxs-lookup"><span data-stu-id="15cb2-168">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>  
  
-   <span data-ttu-id="15cb2-169">Rozszerz najbardziej szczegółowy typ. możesz.</span><span class="sxs-lookup"><span data-stu-id="15cb2-169">Extend the most specific type you can.</span></span> <span data-ttu-id="15cb2-170">W hierarchii typów, w przypadku wybrania typu, od których pochodzą wiele innych typów, istnieją warstwy możliwości wprowadzenia metod instancji lub innych metod rozszerzających, które mogą kolidować z Twoimi.</span><span class="sxs-lookup"><span data-stu-id="15cb2-170">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>  
  
## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="15cb2-171">Metody rozszerzające, wystąpienia metod i właściwości</span><span class="sxs-lookup"><span data-stu-id="15cb2-171">Extension Methods, Instance Methods, and Properties</span></span>  
 <span data-ttu-id="15cb2-172">Gdy w zakresie metoda wystąpień posiada oznaczenie, które są zgodne z argumentami instrukcji wywołania, metoda wystąpienia jest wybierana mieszcząca wszystkich metod rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="15cb2-172">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="15cb2-173">Metoda instancji ma pierwszeństwo, nawet jeśli metoda rozszerzenia ma lepsze dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="15cb2-173">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="15cb2-174">W poniższym przykładzie `ExampleClass` zawiera metodę instancji o nazwie `ExampleMethod` posiadającą jeden parametr typu `Integer`.</span><span class="sxs-lookup"><span data-stu-id="15cb2-174">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="15cb2-175">Metoda rozszerzenia `ExampleMethod` rozszerza `ExampleClass`, i ma jeden parametr typu `Long`.</span><span class="sxs-lookup"><span data-stu-id="15cb2-175">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#4](./codesnippet/VisualBasic/extension-methods_5.vb)]  
  
 <span data-ttu-id="15cb2-176">Pierwsze wywołanie `ExampleMethod` w poniższym kodzie wywołuje metodę rozszerzenia, ponieważ `arg1` jest `Long` i jest zgodny tylko z `Long` parametru w metodzie rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="15cb2-176">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="15cb2-177">Drugie wywołanie `ExampleMethod` ma `Integer` argument `arg2`, i wywołuje metodę wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="15cb2-177">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#5](./codesnippet/VisualBasic/extension-methods_6.vb)]  
  
 <span data-ttu-id="15cb2-178">Teraz Odwróć typy danych parametrów w dwóch metod:</span><span class="sxs-lookup"><span data-stu-id="15cb2-178">Now reverse the data types of the parameters in the two methods:</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#6](./codesnippet/VisualBasic/extension-methods_7.vb)]  
  
 <span data-ttu-id="15cb2-179">Tym razem z kodem w `Main` wywołuje metodę wystąpienia w obu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="15cb2-179">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="15cb2-180">Jest to spowodowane zarówno `arg1` i `arg2` umożliwiać konwersję rozszerzającą do `Long`, i metoda wystąpienia ma pierwszeństwo przez metoda rozszerzenia w obu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="15cb2-180">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#7](./codesnippet/VisualBasic/extension-methods_8.vb)]  
  
 <span data-ttu-id="15cb2-181">W związku z tym metody rozszerzenia nie może zastąpić istniejącej metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="15cb2-181">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="15cb2-182">Jednakże gdy metoda rozszerzająca ma taką samą nazwę jak metoda wystąpienia, ale podpisy nie będą w konflikcie, obie metody są dostępne.</span><span class="sxs-lookup"><span data-stu-id="15cb2-182">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="15cb2-183">Na przykład jeśli klasa `ExampleClass` zawiera metodę o nazwie `ExampleMethod` która nie przyjmuje argumentów, metody rozszerzające o tej samej nazwie, ale różnych dopuszczalne są, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="15cb2-183">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#8](./codesnippet/VisualBasic/extension-methods_9.vb)]  
  
 <span data-ttu-id="15cb2-184">Dane wyjściowe z tego kodu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="15cb2-184">The output from this code is as follows:</span></span>  
  
 `Extension method`  
  
 `Instance method`  
  
 <span data-ttu-id="15cb2-185">Ta sytuacja jest prostsza w przypadku właściwości: Jeżeli metoda rozszerzająca ma taką samą nazwę jak właściwość klasy którą rozszerza, metoda rozszerzenia nie jest widoczna i nie są dostępne.</span><span class="sxs-lookup"><span data-stu-id="15cb2-185">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>  
  
## <a name="extension-method-precedence"></a><span data-ttu-id="15cb2-186">Pierwszeństwo metody rozszerzającej</span><span class="sxs-lookup"><span data-stu-id="15cb2-186">Extension Method Precedence</span></span>  
 <span data-ttu-id="15cb2-187">Gdy dwie metody rozszerzające, posiadające identyczne oznaczenie są z zakresie oraz są dostępne, co o wyższym priorytecie zostanie wywołany.</span><span class="sxs-lookup"><span data-stu-id="15cb2-187">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="15cb2-188">Pierwszeństwo metody rozszerzenia opiera się na mechanizmie zastosowanym w celu dostosowania metody do zakresu.</span><span class="sxs-lookup"><span data-stu-id="15cb2-188">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="15cb2-189">Na poniższej liście przedstawiono hierarchię pierwszeństwa, od najwyższego do najniższego.</span><span class="sxs-lookup"><span data-stu-id="15cb2-189">The following list shows the precedence hierarchy, from highest to lowest.</span></span>  
  
1.  <span data-ttu-id="15cb2-190">Metody rozszerzające zdefiniowane wewnątrz bieżącego modułu.</span><span class="sxs-lookup"><span data-stu-id="15cb2-190">Extension methods defined inside the current module.</span></span>  
  
2.  <span data-ttu-id="15cb2-191">Metody rozszerzające zdefiniowane wewnątrz typów danych w bieżącej przestrzeni nazw lub jednego z elementów nadrzędnych za pomocą podrzędne przestrzenie nazw mającą wyższy priorytet niż nadrzędna przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="15cb2-191">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>  
  
3.  <span data-ttu-id="15cb2-192">Metody rozszerzające zdefiniowane wewnątrz dowolnego typu importu w bieżącym pliku.</span><span class="sxs-lookup"><span data-stu-id="15cb2-192">Extension methods defined inside any type imports in the current file.</span></span>  
  
4.  <span data-ttu-id="15cb2-193">Metody rozszerzające zdefiniowane wewnątrz dowolnej importowanej przestrzeni nazw w bieżącym pliku.</span><span class="sxs-lookup"><span data-stu-id="15cb2-193">Extension methods defined inside any namespace imports in the current file.</span></span>  
  
5.  <span data-ttu-id="15cb2-194">Metody rozszerzające zdefiniowane wewnątrz dowolnej importowanej typu na poziomie projektu.</span><span class="sxs-lookup"><span data-stu-id="15cb2-194">Extension methods defined inside any project-level type imports.</span></span>  
  
6.  <span data-ttu-id="15cb2-195">Metody rozszerzające zdefiniowane wewnątrz dowolnej importowanej przestrzeni nazw na poziomie projektu.</span><span class="sxs-lookup"><span data-stu-id="15cb2-195">Extension methods defined inside any project-level namespace imports.</span></span>  
  
 <span data-ttu-id="15cb2-196">Jeśli pierwszeństwo nie rozwiązuje niejasności, można użyć w pełni kwalifikowana nazwa, aby określić metodę, którą wywołujesz.</span><span class="sxs-lookup"><span data-stu-id="15cb2-196">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="15cb2-197">Jeśli `Print` metoda we wcześniejszym przykładzie jest zdefiniowana w module o nazwie `StringExtensions`, w pełni kwalifikowana nazwa to `StringExtensions.Print(example)` zamiast `example.Print()`.</span><span class="sxs-lookup"><span data-stu-id="15cb2-197">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15cb2-198">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15cb2-198">See also</span></span>
- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="15cb2-199">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="15cb2-199">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [<span data-ttu-id="15cb2-200">Instrukcja Module</span><span class="sxs-lookup"><span data-stu-id="15cb2-200">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="15cb2-201">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="15cb2-201">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="15cb2-202">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="15cb2-202">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="15cb2-203">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="15cb2-203">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="15cb2-204">Omówienie atrybuty</span><span class="sxs-lookup"><span data-stu-id="15cb2-204">Attributes overview</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="15cb2-205">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15cb2-205">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
