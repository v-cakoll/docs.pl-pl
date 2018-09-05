---
title: Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)
ms.date: 07/20/2015
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
ms.openlocfilehash: aa8bf447fe0df81821a34b5a6d898980749921e1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536445"
---
# <a name="accessing-attributes-by-using-reflection-c"></a><span data-ttu-id="4148e-102">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="4148e-102">Accessing Attributes by Using Reflection (C#)</span></span>
<span data-ttu-id="4148e-103">Korzyści bez jakiś sposób pobierania tych informacji i działających na nim mogą być fakt, że można zdefiniować atrybutów niestandardowych i umieść je w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="4148e-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="4148e-104">Przy użyciu odbicia, możesz pobrać informacje, które zostało zdefiniowane przy użyciu atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="4148e-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="4148e-105">Metoda klucza jest `GetCustomAttributes`, która zwraca tablicę obiektów, które są odpowiedników środowiska wykonawczego atrybuty kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="4148e-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="4148e-106">Ta metoda ma kilka przeciążone wersje.</span><span class="sxs-lookup"><span data-stu-id="4148e-106">This method has several overloaded versions.</span></span> <span data-ttu-id="4148e-107">Aby uzyskać więcej informacji, zobacz <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="4148e-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="4148e-108">Specyfikacja atrybutu, takie jak:</span><span class="sxs-lookup"><span data-stu-id="4148e-108">An attribute specification such as:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 <span data-ttu-id="4148e-109">jest równoważny to:</span><span class="sxs-lookup"><span data-stu-id="4148e-109">is conceptually equivalent to this:</span></span>  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 <span data-ttu-id="4148e-110">Jednakże, kod nie jest wykonywany do momentu `SampleClass` jest wysyłane zapytanie dla atrybutów.</span><span class="sxs-lookup"><span data-stu-id="4148e-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="4148e-111">Wywoływanie `GetCustomAttributes` na `SampleClass` powoduje, że `Author` obiekt skonstruowany i zainicjowany, tak jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="4148e-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="4148e-112">Jeśli klasa ma inne atrybuty, innych atrybutów obiektów są konstruowane podobnie.</span><span class="sxs-lookup"><span data-stu-id="4148e-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="4148e-113">`GetCustomAttributes` następnie zwraca `Author` obiektów i innych atrybutów obiektów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="4148e-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="4148e-114">Następnie można wykonać iterację za pośrednictwem tej tablicy, określić, jakie atrybuty zostały zastosowane w oparciu o typ każdego elementu tablicy i wyodrębnianie informacji z obiektów atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4148e-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4148e-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="4148e-115">Example</span></span>  
 <span data-ttu-id="4148e-116">Oto kompletny przykład.</span><span class="sxs-lookup"><span data-stu-id="4148e-116">Here is a complete example.</span></span> <span data-ttu-id="4148e-117">Atrybut niestandardowy jest zdefiniowane, stosowania do kilku jednostek i pobierane za pomocą odbicia.</span><span class="sxs-lookup"><span data-stu-id="4148e-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4148e-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4148e-118">See Also</span></span>

- <xref:System.Reflection>  
- <xref:System.Attribute>  
- [<span data-ttu-id="4148e-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4148e-119">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="4148e-120">Pobieranie informacji przechowywanych w atrybutach</span><span class="sxs-lookup"><span data-stu-id="4148e-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
- [<span data-ttu-id="4148e-121">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="4148e-121">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
- [<span data-ttu-id="4148e-122">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="4148e-122">Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)  
- [<span data-ttu-id="4148e-123">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="4148e-123">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)
