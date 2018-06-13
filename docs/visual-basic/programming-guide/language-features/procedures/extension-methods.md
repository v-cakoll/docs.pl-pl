---
title: Metody rozszerzeń (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: 1cc2ccef09dd027c6f1e82f60ed4ac5f50db6ebe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655287"
---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="47dd4-102">Metody rozszerzeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47dd4-102">Extension Methods (Visual Basic)</span></span>
<span data-ttu-id="47dd4-103">Metody rozszerzenia umożliwiają deweloperom dodania funkcji niestandardowych do typów danych, które zostały już zdefiniowane bez tworzenia nowego typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="47dd4-103">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="47dd4-104">Metody rozszerzenia umożliwiają napisanie metody, która może być wywołana tak, jakby była metodą wystąpienia istniejącego typu.</span><span class="sxs-lookup"><span data-stu-id="47dd4-104">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47dd4-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="47dd4-105">Remarks</span></span>  
 <span data-ttu-id="47dd4-106">Metody rozszerzenia mogą być tylko `Sub` procedury lub `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="47dd4-106">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="47dd4-107">Nie można zdefiniować właściwości rozszerzenia, pole lub zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="47dd4-107">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="47dd4-108">Wszystkie metody rozszerzenia muszą być oznaczone atrybutem rozszerzenia `<Extension()>` z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="47dd4-108">All extension methods must be marked with the extension attribute `<Extension()>` from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="47dd4-109">Pierwszy parametr w definicji — metoda rozszerzenia Określa typ danych metoda jest rozszerzeniem.</span><span class="sxs-lookup"><span data-stu-id="47dd4-109">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="47dd4-110">Po uruchomieniu metoda pierwszy parametr jest powiązany z wystąpieniem typu danych, która wywołuje metodę.</span><span class="sxs-lookup"><span data-stu-id="47dd4-110">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47dd4-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="47dd4-111">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="47dd4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="47dd4-112">Description</span></span>  
 <span data-ttu-id="47dd4-113">W poniższym przykładzie zdefiniowano `Print` rozszerzenie <xref:System.String> — typ danych.</span><span class="sxs-lookup"><span data-stu-id="47dd4-113">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="47dd4-114">W metodzie `Console.WriteLine` do wyświetlenia ciąg.</span><span class="sxs-lookup"><span data-stu-id="47dd4-114">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="47dd4-115">Parametr `Print` metody `aString`, określa, że metoda jest rozszerzeniem <xref:System.String> klasy.</span><span class="sxs-lookup"><span data-stu-id="47dd4-115">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#1](./codesnippet/VisualBasic/extension-methods_1.vb)]  
  
 <span data-ttu-id="47dd4-116">Zwróć uwagę, że definicji — metoda rozszerzenia jest oznaczony atrybutem rozszerzenia `<Extension()>`.</span><span class="sxs-lookup"><span data-stu-id="47dd4-116">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="47dd4-117">Oznaczenie modułu, w którym zdefiniowana jest metoda jest opcjonalne, ale każda metoda rozszerzenia musi być oznaczona.</span><span class="sxs-lookup"><span data-stu-id="47dd4-117">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <span data-ttu-id="47dd4-118"><xref:System.Runtime.CompilerServices> należy zaimportować tak, aby uzyskać dostęp do atrybutu rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="47dd4-118"><xref:System.Runtime.CompilerServices> must be imported in order to access the extension attribute.</span></span>  
  
 <span data-ttu-id="47dd4-119">Metody rozszerzenia mogą być deklarowane tylko w modułach.</span><span class="sxs-lookup"><span data-stu-id="47dd4-119">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="47dd4-120">Zazwyczaj modułu, w którym jest zdefiniowany — metoda rozszerzenia nie jest tym samym module, w którym jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="47dd4-120">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="47dd4-121">Zamiast tego należy moduł, który zawiera metody rozszerzenia są importowane, jeśli wymagane jest, aby przełączyć go do zakresu.</span><span class="sxs-lookup"><span data-stu-id="47dd4-121">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="47dd4-122">Po moduł, który zawiera `Print` jest w zakresie, można wywołać metody, tak jakby był on metodę zwykłej wystąpienia, który nie przyjmuje żadnych argumentów, takich jak `ToUpper`:</span><span class="sxs-lookup"><span data-stu-id="47dd4-122">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#2](./codesnippet/VisualBasic/extension-methods_2.vb)]  
  
 <span data-ttu-id="47dd4-123">Kolejnym przykładzie `PrintAndPunctuate`, także jest rozszerzeniem <xref:System.String>, teraz zdefiniowany dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="47dd4-123">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="47dd4-124">Pierwszy parametr `aString`, określa, że metodę rozszerzenie rozszerza <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="47dd4-124">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="47dd4-125">Drugi parametr `punc`, jest przeznaczona do postaci ciągu znaków interpunkcyjnych, który jest przekazywany jako argument podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="47dd4-125">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="47dd4-126">Metoda wyświetla ciąg następuje znaków interpunkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="47dd4-126">The method displays the string followed by the punctuation marks.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#3](./codesnippet/VisualBasic/extension-methods_3.vb)]  
  
 <span data-ttu-id="47dd4-127">Metoda jest wywoływana przez wysyłanie argument ciągu `punc`: `example.PrintAndPunctuate(".")`</span><span class="sxs-lookup"><span data-stu-id="47dd4-127">The method is called by sending in a string argument for `punc`: `example.PrintAndPunctuate(".")`</span></span>  
  
 <span data-ttu-id="47dd4-128">W poniższym przykładzie przedstawiono `Print` i `PrintAndPunctuate` zdefiniowany i wywołać.</span><span class="sxs-lookup"><span data-stu-id="47dd4-128">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <span data-ttu-id="47dd4-129"><xref:System.Runtime.CompilerServices> zostaną zaimportowane w module definicji w celu umożliwienia dostępu do atrybutu rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="47dd4-129"><xref:System.Runtime.CompilerServices> is imported in the definition module in order to enable access to the extension attribute.</span></span>  
  
### <a name="code"></a><span data-ttu-id="47dd4-130">Kod</span><span class="sxs-lookup"><span data-stu-id="47dd4-130">Code</span></span>  
  
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
  
 <span data-ttu-id="47dd4-131">Metody rozszerzenia są następnie wejścia zakres i o nazwie.</span><span class="sxs-lookup"><span data-stu-id="47dd4-131">Next, the extension methods are brought into scope and called.</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="47dd4-132">Komentarze</span><span class="sxs-lookup"><span data-stu-id="47dd4-132">Comments</span></span>  
 <span data-ttu-id="47dd4-133">Wymaganiem, aby można było uruchomić te lub podobne metody rozszerzenia jest, aby być w zakresie.</span><span class="sxs-lookup"><span data-stu-id="47dd4-133">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="47dd4-134">Jeśli moduł, który zawiera metody rozszerzenia znajduje się w zakresie, jest widoczny w IntelliSense i można wywołać, tak jakby był on metodę wystąpienia zwykłej.</span><span class="sxs-lookup"><span data-stu-id="47dd4-134">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>  
  
 <span data-ttu-id="47dd4-135">Zwróć uwagę, że gdy metody są wywoływane, Brak argumentu nie są przesyłane pierwszego parametru.</span><span class="sxs-lookup"><span data-stu-id="47dd4-135">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="47dd4-136">Parametr `aString` w metodzie poprzedniej definicje jest powiązany z `example`, wystąpienie `String` , który odwołuje się je.</span><span class="sxs-lookup"><span data-stu-id="47dd4-136">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="47dd4-137">Kompilator użyje `example` jako argument wysyłane do pierwszego parametru.</span><span class="sxs-lookup"><span data-stu-id="47dd4-137">The compiler will use `example` as the argument sent to the first parameter.</span></span>  
  
 <span data-ttu-id="47dd4-138">Jeśli metoda rozszerzenia jest wywoływana dla obiekt, który ma ustawioną wartość `Nothing`, wykonuje metodę rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="47dd4-138">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="47dd4-139">Dotyczy to zwykłych wystąpienia metody.</span><span class="sxs-lookup"><span data-stu-id="47dd4-139">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="47dd4-140">Można jawnie sprawdzaj `Nothing` w metodzie rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="47dd4-140">You can explicitly check for `Nothing` in the extension method.</span></span>  
  
## <a name="types-that-can-be-extended"></a><span data-ttu-id="47dd4-141">Typy, które mogą zostać rozszerzone</span><span class="sxs-lookup"><span data-stu-id="47dd4-141">Types That Can Be Extended</span></span>  
 <span data-ttu-id="47dd4-142">Można zdefiniować metody rozszerzenia większość typów, które może być reprezentowany w liście parametrów języka Visual Basic, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="47dd4-142">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>  
  
-   <span data-ttu-id="47dd4-143">Klasy (typy referencyjne)</span><span class="sxs-lookup"><span data-stu-id="47dd4-143">Classes (reference types)</span></span>  
  
-   <span data-ttu-id="47dd4-144">Struktury (typy wartości)</span><span class="sxs-lookup"><span data-stu-id="47dd4-144">Structures (value types)</span></span>  
  
-   <span data-ttu-id="47dd4-145">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="47dd4-145">Interfaces</span></span>  
  
-   <span data-ttu-id="47dd4-146">Delegaty</span><span class="sxs-lookup"><span data-stu-id="47dd4-146">Delegates</span></span>  
  
-   <span data-ttu-id="47dd4-147">Argumenty ByRef i ByVal</span><span class="sxs-lookup"><span data-stu-id="47dd4-147">ByRef and ByVal arguments</span></span>  
  
-   <span data-ttu-id="47dd4-148">Parametry ogólne — metoda</span><span class="sxs-lookup"><span data-stu-id="47dd4-148">Generic method parameters</span></span>  
  
-   <span data-ttu-id="47dd4-149">Tablice</span><span class="sxs-lookup"><span data-stu-id="47dd4-149">Arrays</span></span>  
  
 <span data-ttu-id="47dd4-150">Ponieważ pierwszy parametr określa typ danych, rozszerzający metody rozszerzenia, jest wymagana i nie może być opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="47dd4-150">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="47dd4-151">Z tego powodu `Optional` parametrów i `ParamArray` parametrów nie może być pierwszym parametrem na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="47dd4-151">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="47dd4-152">Metody rozszerzenia nie są wliczane późne wiązanie.</span><span class="sxs-lookup"><span data-stu-id="47dd4-152">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="47dd4-153">W poniższym przykładzie instrukcja `anObject.PrintMe()` zgłasza <xref:System.MissingMemberException> wyjątek, ten sam wyjątek, zobaczysz, jeśli drugi `PrintMe` definicji — metoda rozszerzenia zostały usunięte.</span><span class="sxs-lookup"><span data-stu-id="47dd4-153">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#9](./codesnippet/VisualBasic/extension-methods_4.vb)]  
  
## <a name="best-practices"></a><span data-ttu-id="47dd4-154">Najlepsze praktyki</span><span class="sxs-lookup"><span data-stu-id="47dd4-154">Best Practices</span></span>  
 <span data-ttu-id="47dd4-155">Metody rozszerzenia udostępniają wygodnym i zaawansowanym sposób rozszerzenia istniejącego typu.</span><span class="sxs-lookup"><span data-stu-id="47dd4-155">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="47dd4-156">W celu użycia pomyślnie istnieją pewne kwestie do rozważenia.</span><span class="sxs-lookup"><span data-stu-id="47dd4-156">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="47dd4-157">Te kwestie głównie autorów bibliotek klas, ale mogą wpłynąć na dowolnej aplikacji, która używa metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="47dd4-157">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>  
  
 <span data-ttu-id="47dd4-158">Metody rozszerzenia, które dodajesz do typów, które nie ma są zazwyczaj, bardziej narażony, niż metody rozszerzenia dodane do typów, które kontrolujesz.</span><span class="sxs-lookup"><span data-stu-id="47dd4-158">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="47dd4-159">Liczba elementów może wystąpić w klasach nie użytkownika, które może zakłócać metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="47dd4-159">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>  
  
-   <span data-ttu-id="47dd4-160">Jeśli żadnego członka dostępne wystąpienia istnieje, która ma podpisu zgodnego z argumentów w instrukcji wywoływania z konwersji zawężającej wymagane od argumentu do parametru, zostanie użyta metoda wystąpienia preferowanego w stosunku do dowolnej metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="47dd4-160">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="47dd4-161">W związku z tym jeśli metoda odpowiednie wystąpienie jest dodawana do klasy, w pewnym momencie, istniejącym elementem członkowskim rozszerzenia, które korzystają z mogą stać się niedostępne.</span><span class="sxs-lookup"><span data-stu-id="47dd4-161">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>  
  
-   <span data-ttu-id="47dd4-162">Autor metody rozszerzenia nie może uniemożliwić zapisywanie metod rozszerzeń powodujące konflikt, które mogą mieć pierwszeństwo nad oryginalne rozszerzenie innych programistów.</span><span class="sxs-lookup"><span data-stu-id="47dd4-162">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>  
  
-   <span data-ttu-id="47dd4-163">Można zwiększyć niezawodność umieszczenie metody rozszerzenia w ich własnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="47dd4-163">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="47dd4-164">Konsumenci biblioteki dołączyć przestrzeni nazw lub go wykluczyć lub wybierz jeden z przestrzeni nazw, niezależnie od pozostałej części biblioteki.</span><span class="sxs-lookup"><span data-stu-id="47dd4-164">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>  
  
-   <span data-ttu-id="47dd4-165">Może być bezpieczniejsze rozszerzenie interfejsów, niż jest rozszerzenie klasy, zwłaszcza, jeśli nie ma interfejsu lub klasy.</span><span class="sxs-lookup"><span data-stu-id="47dd4-165">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="47dd4-166">Zmiana w interfejsie wpływa na każdej klasy, która implementuje go.</span><span class="sxs-lookup"><span data-stu-id="47dd4-166">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="47dd4-167">W związku z tym Autor może być mniej prawdopodobne dodać lub zmienić metody w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="47dd4-167">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="47dd4-168">Jednak jeśli klasa implementuje dwa interfejsy, które mają metody rozszerzenia o tej samej sygnaturze, żadna z tych metod rozszerzenia jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="47dd4-168">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>  
  
-   <span data-ttu-id="47dd4-169">Rozszerzanie najbardziej określonego typu, które można wykonywać następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="47dd4-169">Extend the most specific type you can.</span></span> <span data-ttu-id="47dd4-170">W hierarchii typów Jeśli należy wybrać typ, od których pochodzą wiele innych typów, istnieją warstwy możliwości wprowadzania wystąpienia metody lub innych metod rozszerzenia, które może zakłócać należy do Ciebie.</span><span class="sxs-lookup"><span data-stu-id="47dd4-170">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>  
  
## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="47dd4-171">Metody rozszerzenia, wystąpienie metody i właściwości</span><span class="sxs-lookup"><span data-stu-id="47dd4-171">Extension Methods, Instance Methods, and Properties</span></span>  
 <span data-ttu-id="47dd4-172">Metody wystąpienia w zakresie po podpisie, który jest zgodny z argumentami instrukcji wywoływania metody wystąpienia jest wybierany preferowanego w stosunku do dowolnej metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="47dd4-172">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="47dd4-173">Metoda wystąpienia ma pierwszeństwo, nawet jeśli — metoda rozszerzenia jest lepszym dopasowaniem.</span><span class="sxs-lookup"><span data-stu-id="47dd4-173">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="47dd4-174">W poniższym przykładzie `ExampleClass` zawiera metodę wystąpienia o nazwie `ExampleMethod` który ma jeden parametr typu `Integer`.</span><span class="sxs-lookup"><span data-stu-id="47dd4-174">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="47dd4-175">Metody rozszerzenia `ExampleMethod` rozszerza `ExampleClass`, i ma jeden parametr typu `Long`.</span><span class="sxs-lookup"><span data-stu-id="47dd4-175">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#4](./codesnippet/VisualBasic/extension-methods_5.vb)]  
  
 <span data-ttu-id="47dd4-176">W pierwszym wywołaniu `ExampleMethod` poniższy kod wywołuje metodę rozszerzenia, ponieważ `arg1` jest `Long` i jest zgodna tylko z `Long` parametru w metodzie rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="47dd4-176">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="47dd4-177">Drugie wywołanie `ExampleMethod` ma `Integer` argumentu, `arg2`, i wywołuje metodę wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="47dd4-177">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#5](./codesnippet/VisualBasic/extension-methods_6.vb)]  
  
 <span data-ttu-id="47dd4-178">Teraz wycofywania typów danych parametrów w dwóch metod:</span><span class="sxs-lookup"><span data-stu-id="47dd4-178">Now reverse the data types of the parameters in the two methods:</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#6](./codesnippet/VisualBasic/extension-methods_7.vb)]  
  
 <span data-ttu-id="47dd4-179">Tym razem kod w `Main` wywołuje metodę wystąpienia razem.</span><span class="sxs-lookup"><span data-stu-id="47dd4-179">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="47dd4-180">Jest to spowodowane zarówno `arg1` i `arg2` umożliwiać konwersję rozszerzającą do `Long`, oraz metody wystąpienia mają pierwszeństwo przed — metoda rozszerzenia w obu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="47dd4-180">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#7](./codesnippet/VisualBasic/extension-methods_8.vb)]  
  
 <span data-ttu-id="47dd4-181">W związku z tym metody rozszerzenia nie może zastąpić istniejącą metodę wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="47dd4-181">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="47dd4-182">Jednak gdy metody rozszerzenia ma taką samą nazwę jako metodę wystąpienia, ale nie powodują konfliktu podpisy, obie metody są dostępne.</span><span class="sxs-lookup"><span data-stu-id="47dd4-182">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="47dd4-183">Na przykład jeśli klasa `ExampleClass` zawiera metodę o nazwie `ExampleMethod` pobierającej nie argumentów, metody rozszerzenia o tej samej nazwie, ale różnych podpisów są dozwolone, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="47dd4-183">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#8](./codesnippet/VisualBasic/extension-methods_9.vb)]  
  
 <span data-ttu-id="47dd4-184">Dane wyjściowe z tego kodu jest następujący:</span><span class="sxs-lookup"><span data-stu-id="47dd4-184">The output from this code is as follows:</span></span>  
  
 `Extension method`  
  
 `Instance method`  
  
 <span data-ttu-id="47dd4-185">Sytuacja jest prostsze właściwości: Jeśli metody rozszerzenia ma taką samą nazwę jak właściwość rozszerza klasy, metody rozszerzenia nie jest widoczny i nie są dostępne.</span><span class="sxs-lookup"><span data-stu-id="47dd4-185">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>  
  
## <a name="extension-method-precedence"></a><span data-ttu-id="47dd4-186">Pierwszeństwo — metoda rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="47dd4-186">Extension Method Precedence</span></span>  
 <span data-ttu-id="47dd4-187">Gdy dwie metody rozszerzenia, które mają identyczne podpisy są w zakresie i jest dostępny, zostanie wywołany z wyższy priorytet.</span><span class="sxs-lookup"><span data-stu-id="47dd4-187">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="47dd4-188">Metody rozszerzenia pierwszeństwo jest oparta na mechanizm służący do wprowadzenia metody w zakresie.</span><span class="sxs-lookup"><span data-stu-id="47dd4-188">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="47dd4-189">Na poniższej liście przedstawiono hierarchią pierwszeństwo w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="47dd4-189">The following list shows the precedence hierarchy, from highest to lowest.</span></span>  
  
1.  <span data-ttu-id="47dd4-190">Metody rozszerzenia, zdefiniowane wewnątrz bieżącego modułu.</span><span class="sxs-lookup"><span data-stu-id="47dd4-190">Extension methods defined inside the current module.</span></span>  
  
2.  <span data-ttu-id="47dd4-191">Metody rozszerzenia zdefiniowane wewnątrz danych typów w bieżącej przestrzeni nazw lub jednego z jego elementów nadrzędnych z podrzędne przestrzenie nazw mające wyższy priorytet niż nadrzędny przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="47dd4-191">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>  
  
3.  <span data-ttu-id="47dd4-192">Metody rozszerzenia, zdefiniowane wewnątrz wszystkie Importy typu w bieżącym pliku.</span><span class="sxs-lookup"><span data-stu-id="47dd4-192">Extension methods defined inside any type imports in the current file.</span></span>  
  
4.  <span data-ttu-id="47dd4-193">Metody rozszerzenia, zdefiniowane wewnątrz żadnych importów przestrzeni nazw w bieżącym pliku.</span><span class="sxs-lookup"><span data-stu-id="47dd4-193">Extension methods defined inside any namespace imports in the current file.</span></span>  
  
5.  <span data-ttu-id="47dd4-194">Metody rozszerzenia, zdefiniowane wewnątrz importów dowolnego typu na poziomie projektu.</span><span class="sxs-lookup"><span data-stu-id="47dd4-194">Extension methods defined inside any project-level type imports.</span></span>  
  
6.  <span data-ttu-id="47dd4-195">Metody rozszerzenia zdefiniowany w dowolnym importowane elementy obszaru nazw poziom projektu.</span><span class="sxs-lookup"><span data-stu-id="47dd4-195">Extension methods defined inside any project-level namespace imports.</span></span>  
  
 <span data-ttu-id="47dd4-196">Jeśli pierwszeństwo rozwiązania niejednoznaczności, można w pełni kwalifikowana nazwa Określ metodę, która jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="47dd4-196">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="47dd4-197">Jeśli `Print` poprzedniego przykładu metoda jest zdefiniowany w module o nazwie `StringExtensions`, jest w pełni kwalifikowana nazwa `StringExtensions.Print(example)` zamiast `example.Print()`.</span><span class="sxs-lookup"><span data-stu-id="47dd4-197">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47dd4-198">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47dd4-198">See Also</span></span>  
 <xref:System.Runtime.CompilerServices>  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>  
 [<span data-ttu-id="47dd4-199">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="47dd4-199">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [<span data-ttu-id="47dd4-200">Module, instrukcja</span><span class="sxs-lookup"><span data-stu-id="47dd4-200">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [<span data-ttu-id="47dd4-201">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="47dd4-201">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="47dd4-202">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="47dd4-202">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="47dd4-203">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="47dd4-203">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="47dd4-204">Atrybuty — omówienie</span><span class="sxs-lookup"><span data-stu-id="47dd4-204">Attributes overview</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="47dd4-205">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="47dd4-205">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
