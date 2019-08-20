---
title: 'Instrukcje: Implementowanie klasy lekkiej z zaimplementowanymi właściwościami Przewodnik C# programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
ms.openlocfilehash: 4cbed8145487325d8b06882bbab843321a49d0d3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596905"
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a>Instrukcje: Implementowanie klasy lekkiej z zaimplementowanymi właściwościami (C# Przewodnik programowania)

Ten przykład przedstawia sposób tworzenia niezmiennej klasy lekkiej, która służy tylko do hermetyzacji zestawu właściwości, które są implementowane. Użyj tego rodzaju konstrukcji zamiast struktury, gdy musisz użyć semantyki typu odwołania.

Można wprowadzić niemodyfikowalną właściwość na dwa sposoby:
- Można zadeklarować metodę dostępu [Set](../../language-reference/keywords/set.md) jako [prywatną](../../language-reference/keywords/private.md).  Właściwość jest tylko settable w obrębie typu, ale jest niezmienna dla odbiorców.

  W przypadku deklarowania prywatnej `set` metody dostępu nie można użyć inicjatora obiektów do zainicjowania właściwości. Musisz użyć konstruktora lub metody fabryki.
- Można zadeklarować tylko metodę dostępu [Get](../../language-reference/keywords/get.md) , która sprawia, że właściwość jest niezmienna wszędzie z wyjątkiem konstruktora typu.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia dwa sposoby implementacji niezmiennej klasy, która ma właściwości, które są implementowane. Każdy ze sposobów deklaruje jedną z właściwości z prywatną `set` i jedną z właściwości `get` tylko z.  Pierwsza klasa używa konstruktora tylko w celu zainicjowania właściwości, a druga Klasa używa metody fabryki statycznej, która wywołuje konstruktora.

```csharp
// This class is immutable. After an object is created,
// it cannot be modified from outside the class. It uses a
// constructor to initialize its properties.
class Contact
{
    // Read-only properties.
    public string Name { get; }
    public string Address { get; private set; }

    // Public constructor.
    public Contact(string contactName, string contactAddress)
    {
        Name = contactName;
        Address = contactAddress;
    }
}

// This class is immutable. After an object is created,
// it cannot be modified from outside the class. It uses a
// static method and private constructor to initialize its properties.
public class Contact2
{
    // Read-only properties.
    public string Name { get; private set; }
    public string Address { get; }

    // Private constructor.
    private Contact2(string contactName, string contactAddress)
    {
        Name = contactName;
        Address = contactAddress;
    }

    // Public factory method.
    public static Contact2 CreateContact(string name, string address)
    {
        return new Contact2(name, address);
    }
}

public class Program
{
    static void Main()
    {
        // Some simple data sources.
        string[] names = {"Terry Adams","Fadi Fakhouri", "Hanying Feng",
                            "Cesar Garcia", "Debra Garcia"};
        string[] addresses = {"123 Main St.", "345 Cypress Ave.", "678 1st Ave",
                                "12 108th St.", "89 E. 42nd St."};

        // Simple query to demonstrate object creation in select clause.
        // Create Contact objects by using a constructor.
        var query1 = from i in Enumerable.Range(0, 5)
                    select new Contact(names[i], addresses[i]);

        // List elements cannot be modified by client code.
        var list = query1.ToList();
        foreach (var contact in list)
        {
            Console.WriteLine("{0}, {1}", contact.Name, contact.Address);
        }

        // Create Contact2 objects by using a static factory method.
        var query2 = from i in Enumerable.Range(0, 5)
                        select Contact2.CreateContact(names[i], addresses[i]);

        // Console output is identical to query1.
        var list2 = query2.ToList();

        // List elements cannot be modified by client code.
        // CS0272:
        // list2[0].Name = "Eugene Zabokritski";

        // Keep the console open in debug mode.
        Console.WriteLine("Press any key to exit.");
        Console.ReadKey();
    }
}

/* Output:
    Terry Adams, 123 Main St.
    Fadi Fakhouri, 345 Cypress Ave.
    Hanying Feng, 678 1st Ave
    Cesar Garcia, 12 108th St.
    Debra Garcia, 89 E. 42nd St.
*/
```

Kompilator tworzy pola kopii zapasowej dla każdej automatycznie zaimplementowanej właściwości. Pola są niedostępne bezpośrednio z kodu źródłowego.

## <a name="see-also"></a>Zobacz także

- [Właściwości](./properties.md)
- [struct](../../language-reference/keywords/struct.md)
- [Inicjatory obiektów i kolekcji](./object-and-collection-initializers.md)
