---
title: 'Porady: zapisywanie metody rozszerzenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: e220a025c39757b492be033caeb8924523515804
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="9de5b-102">Porady: zapisywanie metody rozszerzenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9de5b-102">How to: Write an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="9de5b-103">Metody rozszerzenia umożliwiają dodawanie metody do istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="9de5b-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="9de5b-104">Tak, jakby była wystąpienia tej klasy można wywołać metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="9de5b-104">The extension method can be called as if it were an instance of that class.</span></span>  
  
### <a name="to-define-an-extension-method"></a><span data-ttu-id="9de5b-105">Aby zdefiniować — metoda rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="9de5b-105">To define an extension method</span></span>  
  
1.  <span data-ttu-id="9de5b-106">Otwieranie nowej lub istniejącej aplikacji Visual Basic w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9de5b-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="9de5b-107">W górnej części pliku, w którym chcesz zdefiniować metodę rozszerzenia należy uwzględnić następującą instrukcję import:</span><span class="sxs-lookup"><span data-stu-id="9de5b-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  <span data-ttu-id="9de5b-108">W module w nowej lub istniejącej aplikacji Rozpocznij definicja metody z atrybutem rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="9de5b-108">Within a module in your new or existing application, begin the method definition with the extension attribute:</span></span>  
  
    ```  
    <Extension()>  
    ```  
  
4.  <span data-ttu-id="9de5b-109">Zadeklaruj metodę w zwykły sposób, z tą różnicą, że typ pierwszego parametru musi być typu danych, który ma zostać rozszerzony.</span><span class="sxs-lookup"><span data-stu-id="9de5b-109">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a><span data-ttu-id="9de5b-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="9de5b-110">Example</span></span>  
 <span data-ttu-id="9de5b-111">Poniższy przykład deklaruje metody rozszerzenia w module `StringExtensions`.</span><span class="sxs-lookup"><span data-stu-id="9de5b-111">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="9de5b-112">Drugi moduł `Module1`, importuje `StringExtensions` i wywołuje metodę.</span><span class="sxs-lookup"><span data-stu-id="9de5b-112">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="9de5b-113">Metoda rozszerzenia musi być w zakresie, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="9de5b-113">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="9de5b-114">Metody rozszerzenia `PrintAndPunctuate` rozszerza <xref:System.String> klasy za pomocą metody, która wyświetla wystąpienia ciągu następuje ciąg znaków specjalnych wysyłane w jako parametr.</span><span class="sxs-lookup"><span data-stu-id="9de5b-114">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>  
  
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
  
 <span data-ttu-id="9de5b-115">Zwróć uwagę, że metoda jest zdefiniowana z dwoma parametrami i wywołać tylko z jednym.</span><span class="sxs-lookup"><span data-stu-id="9de5b-115">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="9de5b-116">Pierwszy parametr `aString`, w metodzie definicji jest powiązany z `example`, wystąpienie `String` która wywołuje metodę.</span><span class="sxs-lookup"><span data-stu-id="9de5b-116">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="9de5b-117">Dane wyjściowe przykładzie ma następującą składnię:</span><span class="sxs-lookup"><span data-stu-id="9de5b-117">The output of the example is as follows:</span></span>  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a><span data-ttu-id="9de5b-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9de5b-118">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>  
 [<span data-ttu-id="9de5b-119">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="9de5b-119">Extension Methods</span></span>](./extension-methods.md)  
 [<span data-ttu-id="9de5b-120">Module, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9de5b-120">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [<span data-ttu-id="9de5b-121">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="9de5b-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="9de5b-122">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9de5b-122">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
