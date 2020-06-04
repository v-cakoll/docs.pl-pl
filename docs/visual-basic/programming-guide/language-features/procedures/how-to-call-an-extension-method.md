---
title: 'Porady: wywoływanie metody rozszerzenia'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 54419c99ae08c9ca2e3cfa86993dc99bc02bbb64
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388663"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a><span data-ttu-id="f92e0-102">Porady: wywoływanie metody rozszerzenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f92e0-102">How to: Call an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="f92e0-103">Metody rozszerzające umożliwiają dodawanie metod do istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="f92e0-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="f92e0-104">Po zadeklarowaniu i wejściu do zakresu metody rozszerzenia można wywołać ją jak metodę wystąpienia typu, który rozszerza.</span><span class="sxs-lookup"><span data-stu-id="f92e0-104">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span></span> <span data-ttu-id="f92e0-105">Aby uzyskać więcej informacji na temat pisania metody rozszerzenia, zobacz [How to: Write a Extension Method](./how-to-write-an-extension-method.md).</span><span class="sxs-lookup"><span data-stu-id="f92e0-105">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span></span>

 <span data-ttu-id="f92e0-106">Poniższe instrukcje odnoszą się do metody rozszerzającej `PrintAndPunctuate` , która wyświetla wystąpienie ciągu, które wywołuje ten element, a następnie dowolną wartość jest wysyłana w dla drugiego parametru, `punc` .</span><span class="sxs-lookup"><span data-stu-id="f92e0-106">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

<span data-ttu-id="f92e0-107">Metoda musi znajdować się w zakresie, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="f92e0-107">The method must be in scope when it is called.</span></span>

### <a name="to-call-an-extension-method"></a><span data-ttu-id="f92e0-108">Aby wywołać metodę rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="f92e0-108">To call an extension method</span></span>

1. <span data-ttu-id="f92e0-109">Zadeklaruj zmienną, która ma typ danych pierwszego parametru metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="f92e0-109">Declare a variable that has the data type of the first parameter of the extension method.</span></span> <span data-ttu-id="f92e0-110">Dla `PrintAndPunctuate` , potrzebna jest <xref:System.String> zmienna:</span><span class="sxs-lookup"><span data-stu-id="f92e0-110">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span></span>

    ```vb
    Dim example = "Ready"
    ```

2. <span data-ttu-id="f92e0-111">Ta zmienna wywoła metodę rozszerzającą, a jej wartość jest powiązana z pierwszym parametrem `aString` .</span><span class="sxs-lookup"><span data-stu-id="f92e0-111">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span></span> <span data-ttu-id="f92e0-112">Zostanie wyświetlona następująca instrukcja wywołująca `Ready?` .</span><span class="sxs-lookup"><span data-stu-id="f92e0-112">The following calling statement will display `Ready?`.</span></span>

    ```vb
    example.PrintAndPunctuate("?")
    ```

     <span data-ttu-id="f92e0-113">Zwróć uwagę, że wywołanie tej metody rozszerzenia wygląda tak samo jak wywołanie jednej z <xref:System.String> metod instancji, które wymagają jednego parametru:</span><span class="sxs-lookup"><span data-stu-id="f92e0-113">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span></span>

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. <span data-ttu-id="f92e0-114">Zadeklaruj inną zmienną ciągu i Wywołaj metodę ponownie, aby zobaczyć, że działa z dowolnym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="f92e0-114">Declare another string variable and call the method again to see that it works with any string.</span></span>

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     <span data-ttu-id="f92e0-115">Wynik tego czasu: `or not!!!` .</span><span class="sxs-lookup"><span data-stu-id="f92e0-115">The result this time is: `or not!!!`.</span></span>

## <a name="example"></a><span data-ttu-id="f92e0-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="f92e0-116">Example</span></span>
 <span data-ttu-id="f92e0-117">Poniższy kod stanowi kompletny przykład tworzenia i używania prostej metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="f92e0-117">The following code is a complete example of the creation and use of a simple extension method.</span></span>

```vb
Imports System.Runtime.CompilerServices
Imports ConsoleApplication1.StringExtensions

Module Module1

    Sub Main()

        Dim example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")

        Dim example2 = "Goodbye"
        example2.PrintAndPunctuate("?")
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module

' Output:
' Hello.
' Hello!!!!
' Goodbye?
```

## <a name="see-also"></a><span data-ttu-id="f92e0-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f92e0-118">See also</span></span>

- [<span data-ttu-id="f92e0-119">Porady: zapisywanie metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="f92e0-119">How to: Write an Extension Method</span></span>](./how-to-write-an-extension-method.md)
- [<span data-ttu-id="f92e0-120">Metody rozszerzające</span><span class="sxs-lookup"><span data-stu-id="f92e0-120">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="f92e0-121">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f92e0-121">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
