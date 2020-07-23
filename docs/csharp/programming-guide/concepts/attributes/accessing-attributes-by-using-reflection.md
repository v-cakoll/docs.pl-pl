---
title: Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)
description: Użyj odbicia, aby uzyskać informacje zdefiniowane przy użyciu atrybutów niestandardowych w języku C# przy użyciu metody GetCustomAttributes —.
ms.date: 07/20/2015
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
ms.openlocfilehash: 9425141d64fd061d0c1f628228693cce02f7bfa0
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925101"
---
# <a name="accessing-attributes-by-using-reflection-c"></a>Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)
Fakt, że można zdefiniować atrybuty niestandardowe i umieścić je w kodzie źródłowym, będzie miał małą wartość bez konieczności pobierania tych informacji i działania na nich. Za pomocą odbicia można pobrać informacje, które zostały zdefiniowane przy użyciu atrybutów niestandardowych. Kluczową metodą jest `GetCustomAttributes` , która zwraca tablicę obiektów, które są odpowiednikami w czasie wykonywania dla atrybutów kodu źródłowego. Ta metoda ma kilka przeciążonych wersji. Aby uzyskać więcej informacji, zobacz <xref:System.Attribute>.  
  
 Specyfikacja atrybutu, taka jak:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 jest koncepcyjnie równoważne:  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 Jednak kod nie jest wykonywany do momentu `SampleClass` zapytania o atrybuty. Wywołanie metody powoduje, że `GetCustomAttributes` `SampleClass` `Author` obiekt ma być skonstruowany i zainicjowany jak powyżej. Jeśli klasa ma inne atrybuty, inne obiekty atrybutów są konstruowane podobnie. `GetCustomAttributes`następnie zwraca `Author` obiekt i wszystkie inne obiekty atrybutu w tablicy. Następnie można wykonać iterację tej tablicy, określić, jakie atrybuty zostały zastosowane na podstawie typu każdego elementu tablicy, i wyodrębnić informacje z obiektów atrybutów.  
  
## <a name="example"></a>Przykład  
 Oto kompletny przykład. Atrybut niestandardowy jest zdefiniowany, stosowany do kilku jednostek i pobierany za pośrednictwem odbicia.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Przewodnik programowania w języku C#](../../index.md)
- [Pobieranie informacji przechowywanych w atrybutach](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [Odbicie (C#)](../reflection.md)
- [Atrybuty (C#)](./index.md)
- [Tworzenie atrybutów niestandardowych (C#)](./creating-custom-attributes.md)
