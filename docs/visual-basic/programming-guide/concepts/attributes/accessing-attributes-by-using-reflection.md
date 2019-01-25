---
title: Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: caf48372f165f3689503d47472a5fa28d2299193
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625118"
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a><span data-ttu-id="8702c-102">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8702c-102">Accessing Attributes by Using Reflection (Visual Basic)</span></span>
<span data-ttu-id="8702c-103">Korzyści bez jakiś sposób pobierania tych informacji i działających na nim mogą być fakt, że można zdefiniować atrybutów niestandardowych i umieść je w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="8702c-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="8702c-104">Przy użyciu odbicia, możesz pobrać informacje, które zostało zdefiniowane przy użyciu atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="8702c-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="8702c-105">Metoda klucza jest `GetCustomAttributes`, która zwraca tablicę obiektów, które są odpowiedników środowiska wykonawczego atrybuty kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="8702c-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="8702c-106">Ta metoda ma kilka przeciążone wersje.</span><span class="sxs-lookup"><span data-stu-id="8702c-106">This method has several overloaded versions.</span></span> <span data-ttu-id="8702c-107">Aby uzyskać więcej informacji, zobacz <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="8702c-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="8702c-108">Specyfikacja atrybutu, takie jak:</span><span class="sxs-lookup"><span data-stu-id="8702c-108">An attribute specification such as:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="8702c-109">jest równoważny to:</span><span class="sxs-lookup"><span data-stu-id="8702c-109">is conceptually equivalent to this:</span></span>  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 <span data-ttu-id="8702c-110">Jednakże, kod nie jest wykonywany do momentu `SampleClass` jest wysyłane zapytanie dla atrybutów.</span><span class="sxs-lookup"><span data-stu-id="8702c-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="8702c-111">Wywoływanie `GetCustomAttributes` na `SampleClass` powoduje, że `Author` obiekt skonstruowany i zainicjowany, tak jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="8702c-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="8702c-112">Jeśli klasa ma inne atrybuty, innych atrybutów obiektów są konstruowane podobnie.</span><span class="sxs-lookup"><span data-stu-id="8702c-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="8702c-113">`GetCustomAttributes` następnie zwraca `Author` obiektów i innych atrybutów obiektów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="8702c-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="8702c-114">Następnie można wykonać iterację za pośrednictwem tej tablicy, określić, jakie atrybuty zostały zastosowane w oparciu o typ każdego elementu tablicy i wyodrębnianie informacji z obiektów atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8702c-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8702c-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="8702c-115">Example</span></span>  
 <span data-ttu-id="8702c-116">Oto kompletny przykład.</span><span class="sxs-lookup"><span data-stu-id="8702c-116">Here is a complete example.</span></span> <span data-ttu-id="8702c-117">Atrybut niestandardowy jest zdefiniowane, stosowania do kilku jednostek i pobierane za pomocą odbicia.</span><span class="sxs-lookup"><span data-stu-id="8702c-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
```vb  
' Multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
  
        ' Default value  
        version = 1.0  
    End Sub  
  
    Function GetName() As String  
        Return name  
    End Function          
End Class  
  
' Class with the Author attribute  
<Author("P. Ackerman")>   
Public Class FirstClass  
End Class  
  
' Class without the Author attribute  
Public Class SecondClass  
End Class  
  
' Class with multiple Author attributes.  
<Author("P. Ackerman"), Author("R. Koch", Version:=2.0)>   
Public Class ThirdClass  
End Class  
  
Class TestAuthorAttribute  
    Sub Main()  
        PrintAuthorInfo(GetType(FirstClass))  
        PrintAuthorInfo(GetType(SecondClass))  
        PrintAuthorInfo(GetType(ThirdClass))  
    End Sub  
  
    Private Shared Sub PrintAuthorInfo(ByVal t As System.Type)  
        System.Console.WriteLine("Author information for {0}", t)  
  
        ' Using reflection  
        Dim attrs() As System.Attribute = System.Attribute.GetCustomAttributes(t)  
  
        ' Displaying output  
        For Each attr In attrs  
            Dim a As Author = CType(attr, Author)  
            System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version)  
        Next              
    End Sub  
  
    ' Output:  
    '   Author information for FirstClass  
    '     P. Ackerman, version 1.00  
    ' Author information for SecondClass  
    ' Author information for ThirdClass  
    '  R. Koch, version 2.00  
    '  P. Ackerman, version 1.00  
  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="8702c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8702c-118">See also</span></span>
- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="8702c-119">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8702c-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="8702c-120">Pobieranie informacji przechowywanych w atrybutach</span><span class="sxs-lookup"><span data-stu-id="8702c-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="8702c-121">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8702c-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="8702c-122">Atrybuty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8702c-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="8702c-123">Tworzenie atrybutów niestandardowych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8702c-123">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
