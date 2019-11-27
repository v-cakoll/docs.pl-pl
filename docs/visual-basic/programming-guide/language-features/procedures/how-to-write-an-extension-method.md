---
title: 'Porady: zapisywanie metody rozszerzenia'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 697508f86ff4ff0a89150b65782121395d0fed12
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346017"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="314cf-102">Porady: zapisywanie metody rozszerzenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="314cf-102">How to: Write an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="314cf-103">Metody rozszerzające umożliwiają dodawanie metod do istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="314cf-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="314cf-104">Metodę rozszerzenia można wywołać tak, jakby była wystąpieniem tej klasy.</span><span class="sxs-lookup"><span data-stu-id="314cf-104">The extension method can be called as if it were an instance of that class.</span></span>

### <a name="to-define-an-extension-method"></a><span data-ttu-id="314cf-105">Aby zdefiniować metodę rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="314cf-105">To define an extension method</span></span>

1. <span data-ttu-id="314cf-106">Otwórz nową lub istniejącą aplikację Visual Basic w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="314cf-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>

2. <span data-ttu-id="314cf-107">W górnej części pliku, w którym ma zostać zdefiniowana Metoda rozszerzenia, należy uwzględnić następujące instrukcje importu:</span><span class="sxs-lookup"><span data-stu-id="314cf-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. <span data-ttu-id="314cf-108">W module w nowej lub istniejącej aplikacji Rozpocznij Definiowanie metody z atrybutem [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) :</span><span class="sxs-lookup"><span data-stu-id="314cf-108">Within a module in your new or existing application, begin the method definition with the [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) attribute:</span></span>

    ```vb
    <Extension()>
    ```

    <span data-ttu-id="314cf-109">Należy zauważyć, że atrybut `Extension` może być stosowany tylko do metody (`Sub` lub `Function` procedurze) w [Module](../../../language-reference/statements/module-statement.md)Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="314cf-109">Note that the `Extension` attribute can only be applied to a method (a `Sub` or `Function` procedure) in a Visual Basic [Module](../../../language-reference/statements/module-statement.md).</span></span> <span data-ttu-id="314cf-110">Jeśli zastosujesz go do metody w `Class` lub `Structure`, kompilator Visual Basic generuje błąd [BC36551](../../../misc/bc36551.md), "metody rozszerzające można definiować tylko w modułach".</span><span class="sxs-lookup"><span data-stu-id="314cf-110">If you apply it to a method in a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules."</span></span>

4. <span data-ttu-id="314cf-111">Zadeklaruj metodę w zwykły sposób, z tą różnicą, że typ pierwszego parametru musi być typem danych, który ma zostać rozszerzona.</span><span class="sxs-lookup"><span data-stu-id="314cf-111">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>

    ```vb
    <Extension()>
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a><span data-ttu-id="314cf-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="314cf-112">Example</span></span>

<span data-ttu-id="314cf-113">Poniższy przykład deklaruje metodę rozszerzającą w module `StringExtensions`.</span><span class="sxs-lookup"><span data-stu-id="314cf-113">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="314cf-114">Drugi moduł, `Module1`, importuje `StringExtensions` i wywołuje metodę.</span><span class="sxs-lookup"><span data-stu-id="314cf-114">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="314cf-115">Metoda rozszerzająca musi znajdować się w zakresie, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="314cf-115">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="314cf-116">Metoda rozszerzająca `PrintAndPunctuate` rozszerza klasę <xref:System.String> za pomocą metody, która wyświetla wystąpienie ciągu, a następuje ciąg symboli interpunkcyjnych wysłanych jako parametr.</span><span class="sxs-lookup"><span data-stu-id="314cf-116">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>

```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

```vb
' Import the module that holds the extension method you want to use,
' and call it.

Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example = "Hello"
        example.PrintAndPunctuate("?")
        example.PrintAndPunctuate("!!!!")
    End Sub

End Module
```

<span data-ttu-id="314cf-117">Należy zauważyć, że metoda jest zdefiniowana z dwoma parametrami i wywoływana z tylko jedną.</span><span class="sxs-lookup"><span data-stu-id="314cf-117">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="314cf-118">Pierwszy parametr, `aString`w definicji metody jest powiązany z `example`, wystąpienie `String`, które wywołuje metodę.</span><span class="sxs-lookup"><span data-stu-id="314cf-118">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="314cf-119">Dane wyjściowe przykładu są następujące:</span><span class="sxs-lookup"><span data-stu-id="314cf-119">The output of the example is as follows:</span></span>

```console
Hello?
Hello!!!!
```

## <a name="see-also"></a><span data-ttu-id="314cf-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="314cf-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="314cf-121">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="314cf-121">Extension Methods</span></span>](extension-methods.md)
- [<span data-ttu-id="314cf-122">Module, instrukcja</span><span class="sxs-lookup"><span data-stu-id="314cf-122">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="314cf-123">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="314cf-123">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="314cf-124">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="314cf-124">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
