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
# <a name="accessing-attributes-by-using-reflection-c"></a>Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)
Fakt, że można zdefiniować atrybuty niestandardowe i umieścić je w kodzie źródłowym będzie mało wartości bez jakiś sposób pobierania tych informacji i działania na nim. Za pomocą odbicia, można pobrać informacje, które zostały zdefiniowane z atrybutami niestandardowymi. Kluczową metodą `GetCustomAttributes`jest , który zwraca tablicy obiektów, które są odpowiedniki czasu wykonywania atrybutów kodu źródłowego. Ta metoda ma kilka wersji przeciążonych. Aby uzyskać więcej informacji, zobacz <xref:System.Attribute>.  
  
 Specyfikacja atrybutu, taka jak:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 jest koncepcyjnie równoważny z tym:  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 Jednak kod nie jest `SampleClass` wykonywany, dopóki nie jest wyszukiwany o atrybuty. `GetCustomAttributes` Wywoływanie `SampleClass` powoduje, `Author` że obiekt ma być skonstruowany i zainicjowany jak wyżej. Jeśli klasa ma inne atrybuty, inne obiekty atrybutu są konstruowane podobnie. `GetCustomAttributes`następnie zwraca `Author` obiekt i inne obiekty atrybutu w tablicy. Następnie można iterate przez tę tablicę, określić, jakie atrybuty zostały zastosowane na podstawie typu każdego elementu tablicy i wyodrębnić informacje z obiektów atrybutu.  
  
## <a name="example"></a>Przykład  
 Oto kompletny przykład. Atrybut niestandardowy jest zdefiniowany, zastosowany do kilku encji i pobrany za pomocą odbicia.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Przewodnik programowania języka C#](../../index.md)
- [Pobieranie informacji przechowywanych w atrybutach](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [Odbicie (C#)](../reflection.md)
- [Atrybuty (C#)](./index.md)
- [Tworzenie atrybutów niestandardowych (C#)](./creating-custom-attributes.md)
