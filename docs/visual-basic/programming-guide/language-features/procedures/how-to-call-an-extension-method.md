---
title: 'Porady: wywoływanie metody rozszerzenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 32691183bcd1632a82b1e9a2668790abbf8f80fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-call-an-extension-method-visual-basic"></a><span data-ttu-id="1e881-102">Porady: wywoływanie metody rozszerzenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e881-102">How to: Call an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="1e881-103">Metody rozszerzenia umożliwiają dodawanie metody do istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="1e881-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="1e881-104">Po — metoda rozszerzenia został zadeklarowany i dostosowane do zakresu, można wywołać go jak metodą wystąpienia typu, który rozszerza.</span><span class="sxs-lookup"><span data-stu-id="1e881-104">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span></span> <span data-ttu-id="1e881-105">Aby uzyskać więcej informacji na temat pisania metodę rozszerzenia, zobacz [porady: zapisywanie metody rozszerzenia](./how-to-write-an-extension-method.md).</span><span class="sxs-lookup"><span data-stu-id="1e881-105">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span></span>  
  
 <span data-ttu-id="1e881-106">Poniższe instrukcje dotyczą — metoda rozszerzenia `PrintAndPunctuate`, które zostaną wyświetlone wystąpienia ciągu, który wywołuje ona następuje niezależnie od wartości są wysyłane drugi parametr `punc`.</span><span class="sxs-lookup"><span data-stu-id="1e881-106">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span></span>  
  
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
  
 <span data-ttu-id="1e881-107">Metoda musi być w zakresie, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="1e881-107">The method must be in scope when it is called.</span></span>  
  
### <a name="to-call-an-extension-method"></a><span data-ttu-id="1e881-108">Wywoływanie metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="1e881-108">To call an extension method</span></span>  
  
1.  <span data-ttu-id="1e881-109">Deklarowanie zmiennej, która ma typ danych pierwszego parametru metody rozszerzającej.</span><span class="sxs-lookup"><span data-stu-id="1e881-109">Declare a variable that has the data type of the first parameter of the extension method.</span></span> <span data-ttu-id="1e881-110">Aby uzyskać `PrintAndPunctuate`, należy <xref:System.String> zmienną:</span><span class="sxs-lookup"><span data-stu-id="1e881-110">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span></span>  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  <span data-ttu-id="1e881-111">Zmienna wywoła metodę rozszerzenia, czy wartość jest powiązany z pierwszym parametrem `aString`.</span><span class="sxs-lookup"><span data-stu-id="1e881-111">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span></span> <span data-ttu-id="1e881-112">Zostanie wyświetlona następująca instrukcja wywoływania `Ready?`.</span><span class="sxs-lookup"><span data-stu-id="1e881-112">The following calling statement will display `Ready?`.</span></span>  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     <span data-ttu-id="1e881-113">Zwróć uwagę, że wywołanie tej metody rozszerzenia wygląda podobnie jak wywołania do jednego z <xref:System.String> wystąpienia metody, które wymagają jeden parametr:</span><span class="sxs-lookup"><span data-stu-id="1e881-113">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span></span>  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  <span data-ttu-id="1e881-114">Deklarowanie innej zmiennej ciągu i wywołać metodę ponownie, aby sprawdzić, czy działa z dowolnym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="1e881-114">Declare another string variable and call the method again to see that it works with any string.</span></span>  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     <span data-ttu-id="1e881-115">Wynik jest teraz: `or not!!!`.</span><span class="sxs-lookup"><span data-stu-id="1e881-115">The result this time is: `or not!!!`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e881-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="1e881-116">Example</span></span>  
 <span data-ttu-id="1e881-117">Następujący kod jest kompletnym przykładem tworzenia i stosowania metody rozszerzenia proste.</span><span class="sxs-lookup"><span data-stu-id="1e881-117">The following code is a complete example of the creation and use of a simple extension method.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1e881-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1e881-118">See Also</span></span>  
 [<span data-ttu-id="1e881-119">Instrukcje: zapisywanie metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="1e881-119">How to: Write an Extension Method</span></span>](./how-to-write-an-extension-method.md)  
 [<span data-ttu-id="1e881-120">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="1e881-120">Extension Methods</span></span>](./extension-methods.md)  
 [<span data-ttu-id="1e881-121">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1e881-121">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
