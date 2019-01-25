---
title: 'Instrukcje: Wywoływanie metody rozszerzenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 4e9391a4c4a159cd5e198689bf7af7cd64c3a872
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620451"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a><span data-ttu-id="b0f48-102">Instrukcje: Wywoływanie metody rozszerzenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0f48-102">How to: Call an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="b0f48-103">Metody rozszerzające umożliwiają dodawanie metod do istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="b0f48-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="b0f48-104">Po metody rozszerzenia są deklarowane i dostosowane do zakresu, można też wywołać, takich jak metoda wystąpienia typu, który stanowi rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="b0f48-104">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span></span> <span data-ttu-id="b0f48-105">Aby uzyskać więcej informacji na temat pisania metodę rozszerzenia, zobacz [jak: Zapisywanie metody rozszerzenia](./how-to-write-an-extension-method.md).</span><span class="sxs-lookup"><span data-stu-id="b0f48-105">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span></span>  
  
 <span data-ttu-id="b0f48-106">Poniższe instrukcje dotyczą — metoda rozszerzenia `PrintAndPunctuate`, co spowoduje wyświetlenie wystąpieniu ciągu, który wywołuje on następuje niezależnie od wartości wysyłane jako drugi parametr `punc`.</span><span class="sxs-lookup"><span data-stu-id="b0f48-106">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span></span>  
  
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
  
 <span data-ttu-id="b0f48-107">Metoda musi być w zakresie, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="b0f48-107">The method must be in scope when it is called.</span></span>  
  
### <a name="to-call-an-extension-method"></a><span data-ttu-id="b0f48-108">Aby wywołać metodę rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="b0f48-108">To call an extension method</span></span>  
  
1.  <span data-ttu-id="b0f48-109">Zadeklaruj zmienną, która ma typ danych pierwszy parametr metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="b0f48-109">Declare a variable that has the data type of the first parameter of the extension method.</span></span> <span data-ttu-id="b0f48-110">Aby uzyskać `PrintAndPunctuate`, potrzebujesz <xref:System.String> zmiennej:</span><span class="sxs-lookup"><span data-stu-id="b0f48-110">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span></span>  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  <span data-ttu-id="b0f48-111">Czy zmienna spowoduje wywołanie metody rozszerzenia, a jego wartość jest związana z pierwszego parametru `aString`.</span><span class="sxs-lookup"><span data-stu-id="b0f48-111">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span></span> <span data-ttu-id="b0f48-112">Zostanie wyświetlona następująca instrukcja wywoływania `Ready?`.</span><span class="sxs-lookup"><span data-stu-id="b0f48-112">The following calling statement will display `Ready?`.</span></span>  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     <span data-ttu-id="b0f48-113">Należy zauważyć, że wywołanie tej metody rozszerzenia wygląda po prostu, takie jak wywołanie jednej z <xref:System.String> wystąpienia metody, które wymagają jednego parametru:</span><span class="sxs-lookup"><span data-stu-id="b0f48-113">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span></span>  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  <span data-ttu-id="b0f48-114">Zadeklaruj innej zmiennej ciągu i wywołanie metody ponownie, aby zobaczyć, czy działa z dowolnym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="b0f48-114">Declare another string variable and call the method again to see that it works with any string.</span></span>  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     <span data-ttu-id="b0f48-115">Wynik jest w tej chwili: `or not!!!`.</span><span class="sxs-lookup"><span data-stu-id="b0f48-115">The result this time is: `or not!!!`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0f48-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0f48-116">Example</span></span>  
 <span data-ttu-id="b0f48-117">Poniższy kod jest kompletny przykład tworzenia i używania metody proste rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="b0f48-117">The following code is a complete example of the creation and use of a simple extension method.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b0f48-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0f48-118">See also</span></span>
- [<span data-ttu-id="b0f48-119">Instrukcje: Zapisywanie metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="b0f48-119">How to: Write an Extension Method</span></span>](./how-to-write-an-extension-method.md)
- [<span data-ttu-id="b0f48-120">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="b0f48-120">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="b0f48-121">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b0f48-121">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
