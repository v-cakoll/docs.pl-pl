---
title: Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)
ms.date: 07/20/2015
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
ms.openlocfilehash: f7c7b89be13022471f4e17bcb6ed9a90bcbc1c54
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660414"
---
# <a name="accessing-attributes-by-using-reflection-c"></a>Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)
Korzyści bez jakiś sposób pobierania tych informacji i działających na nim mogą być fakt, że można zdefiniować atrybutów niestandardowych i umieść je w kodzie źródłowym. Przy użyciu odbicia, możesz pobrać informacje, które zostało zdefiniowane przy użyciu atrybutów niestandardowych. Metoda klucza jest `GetCustomAttributes`, która zwraca tablicę obiektów, które są odpowiedników środowiska wykonawczego atrybuty kodu źródłowego. Ta metoda ma kilka przeciążone wersje. Aby uzyskać więcej informacji, zobacz <xref:System.Attribute>.  
  
 Specyfikacja atrybutu, takie jak:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 jest równoważny to:  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 Jednakże, kod nie jest wykonywany do momentu `SampleClass` jest wysyłane zapytanie dla atrybutów. Wywoływanie `GetCustomAttributes` na `SampleClass` powoduje, że `Author` obiekt skonstruowany i zainicjowany, tak jak powyżej. Jeśli klasa ma inne atrybuty, innych atrybutów obiektów są konstruowane podobnie. `GetCustomAttributes` następnie zwraca `Author` obiektów i innych atrybutów obiektów w tablicy. Następnie można wykonać iterację za pośrednictwem tej tablicy, określić, jakie atrybuty zostały zastosowane w oparciu o typ każdego elementu tablicy i wyodrębnianie informacji z obiektów atrybutu.  
  
## <a name="example"></a>Przykład  
 Oto kompletny przykład. Atrybut niestandardowy jest zdefiniowane, stosowania do kilku jednostek i pobierane za pomocą odbicia.  
  
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
- [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)
- [Pobieranie informacji przechowywanych w atrybutach](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [Odbicie (C#)](../../../../csharp/programming-guide/concepts/reflection.md)
- [Atrybuty (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)
- [Tworzenie atrybutów niestandardowych (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)
