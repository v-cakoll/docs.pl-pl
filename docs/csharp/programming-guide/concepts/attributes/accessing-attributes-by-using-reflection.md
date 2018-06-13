---
title: Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)
ms.date: 07/20/2015
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
ms.openlocfilehash: 05c051490dab5265309fd067dfb67f0ef7822541
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318493"
---
# <a name="accessing-attributes-by-using-reflection-c"></a>Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)
Fakt, że można zdefiniować atrybutów niestandardowych i umieść je w kodzie źródłowym byłoby o niewielkiej wartości bez sposób pobierania tych informacji i działające na nim. Przy użyciu odbicia, można pobierać informacje, która została zdefiniowana z atrybutów niestandardowych. Metoda klucza jest `GetCustomAttributes`, która zwraca tablicę obiektów, które są odpowiedniki środowiska wykonawczego atrybutów kodu źródłowego. Ta metoda ma kilka wersji przeciążona. Aby uzyskać więcej informacji, zobacz <xref:System.Attribute>.  
  
 Specyfikacja atrybutu, takich jak:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 odpowiada koncepcyjnie to:  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 Jednak kod nie jest wykonywany do momentu `SampleClass` zostanie zapytany o atrybuty. Wywoływanie `GetCustomAttributes` na `SampleClass` powoduje, że `Author` obiektu utworzone i zainicjowane zgodnie z powyższym. Jeśli klasa ma inne atrybuty, inne obiekty atrybutu są zbudowane analogicznie. `GetCustomAttributes` Zwraca `Author` obiektu i innych obiektów atrybutu w tablicy. Można następnie iteracja tej tablicy, określić atrybuty zostały zastosowane w zależności od typu każdy element tablicy i wyodrębnienia informacji z obiektów atrybutu.  
  
## <a name="example"></a>Przykład  
 W tym miejscu jest pełny przykład. Atrybut niestandardowy jest zdefiniowany, stosowane do kilku jednostek i pobrać za pomocą odbicia.  
  
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
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)  
 [Pobieranie informacji przechowywanych w atrybutach](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
 [Odbicie (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [Atrybuty (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [Tworzenie atrybutów niestandardowych (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)
