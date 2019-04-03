---
title: 'Instrukcje: Zapisywanie metody rozszerzenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: d6f8b85945bd400d1f4b54a50260d72c750add8b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819120"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="83570-102">Instrukcje: Zapisywanie metody rozszerzenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83570-102">How to: Write an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="83570-103">Metody rozszerzające umożliwiają dodawanie metod do istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="83570-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="83570-104">Metoda rozszerzenia może być wywoływana, jakby była wystąpieniem tej klasy.</span><span class="sxs-lookup"><span data-stu-id="83570-104">The extension method can be called as if it were an instance of that class.</span></span>  
  
### <a name="to-define-an-extension-method"></a><span data-ttu-id="83570-105">Aby zdefiniować metodę rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="83570-105">To define an extension method</span></span>  
  
1.  <span data-ttu-id="83570-106">Otwieranie nowej lub istniejącej aplikacji języka Visual Basic w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="83570-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="83570-107">W górnej części pliku, w której chcesz zdefiniować metodę rozszerzenia obejmują następującą instrukcję import:</span><span class="sxs-lookup"><span data-stu-id="83570-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  <span data-ttu-id="83570-108">W module w nowej lub istniejącej aplikacji Rozpocznij definicję metody z atrybutem rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="83570-108">Within a module in your new or existing application, begin the method definition with the extension attribute:</span></span>  
  
    ```  
    <Extension()>  
    ```  
  
4.  <span data-ttu-id="83570-109">Zadeklaruj metodę w zwykły sposób, z tą różnicą, że typ pierwszego parametru musi być typu danych, które chcesz rozszerzyć.</span><span class="sxs-lookup"><span data-stu-id="83570-109">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a><span data-ttu-id="83570-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="83570-110">Example</span></span>  
 <span data-ttu-id="83570-111">Poniższy przykład deklaruje metodę rozszerzenia w module `StringExtensions`.</span><span class="sxs-lookup"><span data-stu-id="83570-111">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="83570-112">Drugi moduł `Module1`, importuje `StringExtensions` i wywołuje metodę.</span><span class="sxs-lookup"><span data-stu-id="83570-112">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="83570-113">Metoda rozszerzenia musi być w zakresie, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="83570-113">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="83570-114">Metoda rozszerzenia `PrintAndPunctuate` rozszerza <xref:System.String> klasę z metodą, która wyświetla wystąpienia ciągu następuje ciąg symbole znaków interpunkcyjnych wysyłane jako parametr.</span><span class="sxs-lookup"><span data-stu-id="83570-114">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>  
  
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
  
 <span data-ttu-id="83570-115">Należy zauważyć, że metoda jest zdefiniowana za pomocą dwóch parametrów i wywoływana tylko z jednym.</span><span class="sxs-lookup"><span data-stu-id="83570-115">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="83570-116">Pierwszy parametr `aString`, w metodzie definicji jest powiązany z `example`, wystąpienie `String` , wywołuje metodę.</span><span class="sxs-lookup"><span data-stu-id="83570-116">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="83570-117">Dane wyjściowe z przykładu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="83570-117">The output of the example is as follows:</span></span>  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a><span data-ttu-id="83570-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83570-118">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="83570-119">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="83570-119">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="83570-120">Instrukcja Module</span><span class="sxs-lookup"><span data-stu-id="83570-120">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="83570-121">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="83570-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="83570-122">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="83570-122">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
