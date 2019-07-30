---
title: 'Instrukcje: Napisz metodę rozszerzenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 7a7a9d16d9f69071e9d1dacb0558f7ca92e1d21e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631031"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="098b8-102">Instrukcje: Napisz metodę rozszerzenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="098b8-102">How to: Write an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="098b8-103">Metody rozszerzające umożliwiają dodawanie metod do istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="098b8-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="098b8-104">Metodę rozszerzenia można wywołać tak, jakby była wystąpieniem tej klasy.</span><span class="sxs-lookup"><span data-stu-id="098b8-104">The extension method can be called as if it were an instance of that class.</span></span>

### <a name="to-define-an-extension-method"></a><span data-ttu-id="098b8-105">Aby zdefiniować metodę rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="098b8-105">To define an extension method</span></span>

1. <span data-ttu-id="098b8-106">Otwórz nową lub istniejącą aplikację Visual Basic w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="098b8-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>

2. <span data-ttu-id="098b8-107">W górnej części pliku, w którym ma zostać zdefiniowana Metoda rozszerzenia, należy uwzględnić następujące instrukcje importu:</span><span class="sxs-lookup"><span data-stu-id="098b8-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. <span data-ttu-id="098b8-108">W module w nowej lub istniejącej aplikacji Rozpocznij Definiowanie metody z atrybutem rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="098b8-108">Within a module in your new or existing application, begin the method definition with the extension attribute:</span></span>

    ```vb
    <Extension()>
    ```

4. <span data-ttu-id="098b8-109">Zadeklaruj metodę w zwykły sposób, z tą różnicą, że typ pierwszego parametru musi być typem danych, który ma zostać rozszerzona.</span><span class="sxs-lookup"><span data-stu-id="098b8-109">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>

    ```vb
    <Extension()>
    Public Sub SubName (ByVal para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a><span data-ttu-id="098b8-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="098b8-110">Example</span></span>
 <span data-ttu-id="098b8-111">Poniższy przykład deklaruje metodę rozszerzenia w module `StringExtensions`.</span><span class="sxs-lookup"><span data-stu-id="098b8-111">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="098b8-112">Drugi moduł `Module1`,, importuje `StringExtensions` i wywołuje metodę.</span><span class="sxs-lookup"><span data-stu-id="098b8-112">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="098b8-113">Metoda rozszerzająca musi znajdować się w zakresie, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="098b8-113">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="098b8-114">Metoda `PrintAndPunctuate` rozszerzająca <xref:System.String> rozszerza klasę z metodą, która wyświetla wystąpienie ciągu, po którym następuje ciąg symboli interpunkcyjnych wysłanych jako parametr.</span><span class="sxs-lookup"><span data-stu-id="098b8-114">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>
  
```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
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
  
 <span data-ttu-id="098b8-115">Należy zauważyć, że metoda jest zdefiniowana z dwoma parametrami i wywoływana z tylko jedną.</span><span class="sxs-lookup"><span data-stu-id="098b8-115">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="098b8-116">Pierwszy parametr `aString`, w definicji metody jest powiązany z `example`, wystąpieniem `String` wywołującym metodę.</span><span class="sxs-lookup"><span data-stu-id="098b8-116">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="098b8-117">Dane wyjściowe przykładu są następujące:</span><span class="sxs-lookup"><span data-stu-id="098b8-117">The output of the example is as follows:</span></span>
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a><span data-ttu-id="098b8-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="098b8-118">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="098b8-119">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="098b8-119">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="098b8-120">Instrukcja Module</span><span class="sxs-lookup"><span data-stu-id="098b8-120">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="098b8-121">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="098b8-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="098b8-122">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="098b8-122">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
