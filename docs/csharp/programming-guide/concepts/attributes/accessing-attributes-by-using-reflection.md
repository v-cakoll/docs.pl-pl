---
title: Uzyskiwanie dostępu do atrybutów przyC#użyciu odbicia ()
ms.date: 07/20/2015
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
ms.openlocfilehash: 990b6487e50bfb2d123c3871e5f85da063711d9e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595506"
---
# <a name="accessing-attributes-by-using-reflection-c"></a><span data-ttu-id="c0098-102">Uzyskiwanie dostępu do atrybutów przyC#użyciu odbicia ()</span><span class="sxs-lookup"><span data-stu-id="c0098-102">Accessing Attributes by Using Reflection (C#)</span></span>
<span data-ttu-id="c0098-103">Fakt, że można zdefiniować atrybuty niestandardowe i umieścić je w kodzie źródłowym, będzie miał małą wartość bez konieczności pobierania tych informacji i działania na nich.</span><span class="sxs-lookup"><span data-stu-id="c0098-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="c0098-104">Za pomocą odbicia można pobrać informacje, które zostały zdefiniowane przy użyciu atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="c0098-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="c0098-105">Kluczową metodą jest `GetCustomAttributes`, która zwraca tablicę obiektów, które są odpowiednikami w czasie wykonywania dla atrybutów kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="c0098-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="c0098-106">Ta metoda ma kilka przeciążonych wersji.</span><span class="sxs-lookup"><span data-stu-id="c0098-106">This method has several overloaded versions.</span></span> <span data-ttu-id="c0098-107">Aby uzyskać więcej informacji, zobacz <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="c0098-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="c0098-108">Specyfikacja atrybutu, taka jak:</span><span class="sxs-lookup"><span data-stu-id="c0098-108">An attribute specification such as:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 <span data-ttu-id="c0098-109">jest koncepcyjnie równoważne:</span><span class="sxs-lookup"><span data-stu-id="c0098-109">is conceptually equivalent to this:</span></span>  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 <span data-ttu-id="c0098-110">Jednak kod nie jest wykonywany do momentu `SampleClass` zapytania o atrybuty.</span><span class="sxs-lookup"><span data-stu-id="c0098-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="c0098-111">Wywołanie metody `GetCustomAttributes` powoduje`Author`, że obiekt ma być skonstruowany i zainicjowany jak powyżej. `SampleClass`</span><span class="sxs-lookup"><span data-stu-id="c0098-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="c0098-112">Jeśli klasa ma inne atrybuty, inne obiekty atrybutów są konstruowane podobnie.</span><span class="sxs-lookup"><span data-stu-id="c0098-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="c0098-113">`GetCustomAttributes`następnie zwraca `Author` obiekt i wszystkie inne obiekty atrybutu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="c0098-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="c0098-114">Następnie można wykonać iterację tej tablicy, określić, jakie atrybuty zostały zastosowane na podstawie typu każdego elementu tablicy, i wyodrębnić informacje z obiektów atrybutów.</span><span class="sxs-lookup"><span data-stu-id="c0098-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0098-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="c0098-115">Example</span></span>  
 <span data-ttu-id="c0098-116">Oto kompletny przykład.</span><span class="sxs-lookup"><span data-stu-id="c0098-116">Here is a complete example.</span></span> <span data-ttu-id="c0098-117">Atrybut niestandardowy jest zdefiniowany, stosowany do kilku jednostek i pobierany za pośrednictwem odbicia.</span><span class="sxs-lookup"><span data-stu-id="c0098-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c0098-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0098-118">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="c0098-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c0098-119">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="c0098-120">Pobieranie informacji przechowywanych w atrybutach</span><span class="sxs-lookup"><span data-stu-id="c0098-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="c0098-121">OdbicieC#()</span><span class="sxs-lookup"><span data-stu-id="c0098-121">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="c0098-122">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="c0098-122">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="c0098-123">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="c0098-123">Creating Custom Attributes (C#)</span></span>](./creating-custom-attributes.md)
