---
title: Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)
ms.date: 07/20/2015
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
ms.openlocfilehash: 990b6487e50bfb2d123c3871e5f85da063711d9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595506"
---
# <a name="accessing-attributes-by-using-reflection-c"></a><span data-ttu-id="bb232-102">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="bb232-102">Accessing Attributes by Using Reflection (C#)</span></span>
<span data-ttu-id="bb232-103">Fakt, że można zdefiniować atrybuty niestandardowe i umieścić je w kodzie źródłowym będzie mało wartości bez jakiś sposób pobierania tych informacji i działania na nim.</span><span class="sxs-lookup"><span data-stu-id="bb232-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="bb232-104">Za pomocą odbicia, można pobrać informacje, które zostały zdefiniowane z atrybutami niestandardowymi.</span><span class="sxs-lookup"><span data-stu-id="bb232-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="bb232-105">Kluczową metodą `GetCustomAttributes`jest , który zwraca tablicy obiektów, które są odpowiedniki czasu wykonywania atrybutów kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="bb232-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="bb232-106">Ta metoda ma kilka wersji przeciążonych.</span><span class="sxs-lookup"><span data-stu-id="bb232-106">This method has several overloaded versions.</span></span> <span data-ttu-id="bb232-107">Aby uzyskać więcej informacji, zobacz <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="bb232-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="bb232-108">Specyfikacja atrybutu, taka jak:</span><span class="sxs-lookup"><span data-stu-id="bb232-108">An attribute specification such as:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 <span data-ttu-id="bb232-109">jest koncepcyjnie równoważny z tym:</span><span class="sxs-lookup"><span data-stu-id="bb232-109">is conceptually equivalent to this:</span></span>  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 <span data-ttu-id="bb232-110">Jednak kod nie jest `SampleClass` wykonywany, dopóki nie jest wyszukiwany o atrybuty.</span><span class="sxs-lookup"><span data-stu-id="bb232-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="bb232-111">`GetCustomAttributes` Wywoływanie `SampleClass` powoduje, `Author` że obiekt ma być skonstruowany i zainicjowany jak wyżej.</span><span class="sxs-lookup"><span data-stu-id="bb232-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="bb232-112">Jeśli klasa ma inne atrybuty, inne obiekty atrybutu są konstruowane podobnie.</span><span class="sxs-lookup"><span data-stu-id="bb232-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="bb232-113">`GetCustomAttributes`następnie zwraca `Author` obiekt i inne obiekty atrybutu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="bb232-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="bb232-114">Następnie można iterate przez tę tablicę, określić, jakie atrybuty zostały zastosowane na podstawie typu każdego elementu tablicy i wyodrębnić informacje z obiektów atrybutu.</span><span class="sxs-lookup"><span data-stu-id="bb232-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb232-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb232-115">Example</span></span>  
 <span data-ttu-id="bb232-116">Oto kompletny przykład.</span><span class="sxs-lookup"><span data-stu-id="bb232-116">Here is a complete example.</span></span> <span data-ttu-id="bb232-117">Atrybut niestandardowy jest zdefiniowany, zastosowany do kilku encji i pobrany za pomocą odbicia.</span><span class="sxs-lookup"><span data-stu-id="bb232-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
```csharp  
// Multiuse attribute.  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // Multiuse attribute.  
]  
public class Author : System.Attribute  
{  
    string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
  
        // Default value.  
        version = 1.0;  
    }  
  
    public string GetName()  
    {  
        return name;  
    }  
}  
  
// Class with the Author attribute.  
[Author("P. Ackerman")]  
public class FirstClass  
{  
    // ...  
}  
  
// Class without the Author attribute.  
public class SecondClass  
{  
    // ...  
}  
  
// Class with multiple Author attributes.  
[Author("P. Ackerman"), Author("R. Koch", version = 2.0)]  
public class ThirdClass  
{  
    // ...  
}  
  
class TestAuthorAttribute  
{  
    static void Test()  
    {  
        PrintAuthorInfo(typeof(FirstClass));  
        PrintAuthorInfo(typeof(SecondClass));  
        PrintAuthorInfo(typeof(ThirdClass));  
    }  
  
    private static void PrintAuthorInfo(System.Type t)  
    {  
        System.Console.WriteLine("Author information for {0}", t);  
  
        // Using reflection.  
        System.Attribute[] attrs = System.Attribute.GetCustomAttributes(t);  // Reflection.  
  
        // Displaying output.  
        foreach (System.Attribute attr in attrs)  
        {  
            if (attr is Author)  
            {  
                Author a = (Author)attr;  
                System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version);  
            }  
        }  
    }  
}  
/* Output:  
    Author information for FirstClass  
       P. Ackerman, version 1.00  
    Author information for SecondClass  
    Author information for ThirdClass  
       R. Koch, version 2.00  
       P. Ackerman, version 1.00  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb232-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb232-118">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="bb232-119">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="bb232-119">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="bb232-120">Pobieranie informacji przechowywanych w atrybutach</span><span class="sxs-lookup"><span data-stu-id="bb232-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="bb232-121">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="bb232-121">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="bb232-122">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="bb232-122">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="bb232-123">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="bb232-123">Creating Custom Attributes (C#)</span></span>](./creating-custom-attributes.md)
