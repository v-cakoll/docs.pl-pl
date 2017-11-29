---
title: "Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a4397200b5a2aa5f337dd3479b5405c1a9f245a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a><span data-ttu-id="10f2d-102">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10f2d-102">Accessing Attributes by Using Reflection (Visual Basic)</span></span>
<span data-ttu-id="10f2d-103">Fakt, że można zdefiniować atrybutów niestandardowych i umieść je w kodzie źródłowym byłoby o niewielkiej wartości bez sposób pobierania tych informacji i działające na nim.</span><span class="sxs-lookup"><span data-stu-id="10f2d-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="10f2d-104">Przy użyciu odbicia, można pobierać informacje, która została zdefiniowana z atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="10f2d-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="10f2d-105">Metoda klucza jest `GetCustomAttributes`, która zwraca tablicę obiektów, które są odpowiedniki środowiska wykonawczego atrybutów kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="10f2d-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="10f2d-106">Ta metoda ma kilka wersji przeciążona.</span><span class="sxs-lookup"><span data-stu-id="10f2d-106">This method has several overloaded versions.</span></span> <span data-ttu-id="10f2d-107">Aby uzyskać więcej informacji, zobacz <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="10f2d-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="10f2d-108">Specyfikacja atrybutu, takich jak:</span><span class="sxs-lookup"><span data-stu-id="10f2d-108">An attribute specification such as:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="10f2d-109">odpowiada koncepcyjnie to:</span><span class="sxs-lookup"><span data-stu-id="10f2d-109">is conceptually equivalent to this:</span></span>  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 <span data-ttu-id="10f2d-110">Jednak kod nie jest wykonywany do momentu `SampleClass` zostanie zapytany o atrybuty.</span><span class="sxs-lookup"><span data-stu-id="10f2d-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="10f2d-111">Wywoływanie `GetCustomAttributes` na `SampleClass` powoduje, że `Author` obiektu utworzone i zainicjowane zgodnie z powyższym.</span><span class="sxs-lookup"><span data-stu-id="10f2d-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="10f2d-112">Jeśli klasa ma inne atrybuty, inne obiekty atrybutu są zbudowane analogicznie.</span><span class="sxs-lookup"><span data-stu-id="10f2d-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="10f2d-113">`GetCustomAttributes`Zwraca `Author` obiektu i innych obiektów atrybutu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="10f2d-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="10f2d-114">Można następnie iteracja tej tablicy, określić atrybuty zostały zastosowane w zależności od typu każdy element tablicy i wyodrębnienia informacji z obiektów atrybutu.</span><span class="sxs-lookup"><span data-stu-id="10f2d-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10f2d-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="10f2d-115">Example</span></span>  
 <span data-ttu-id="10f2d-116">W tym miejscu jest pełny przykład.</span><span class="sxs-lookup"><span data-stu-id="10f2d-116">Here is a complete example.</span></span> <span data-ttu-id="10f2d-117">Atrybut niestandardowy jest zdefiniowany, stosowane do kilku jednostek i pobrać za pomocą odbicia.</span><span class="sxs-lookup"><span data-stu-id="10f2d-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="10f2d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10f2d-118">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="10f2d-119">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10f2d-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="10f2d-120">Pobieranie informacji przechowywanych w atrybutach</span><span class="sxs-lookup"><span data-stu-id="10f2d-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
 [<span data-ttu-id="10f2d-121">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10f2d-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="10f2d-122">Atrybuty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10f2d-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)  
 [<span data-ttu-id="10f2d-123">Tworzenie atrybutów niestandardowych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10f2d-123">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
