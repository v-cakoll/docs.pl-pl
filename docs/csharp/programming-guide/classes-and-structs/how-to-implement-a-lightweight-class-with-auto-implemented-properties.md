---
title: Jak zaimplementować klasę lekkości z właściwościami implementowanymi automatycznie - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
ms.openlocfilehash: 6d121f6be768d41d22ea01d871662913b2daae2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170276"
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a>Jak zaimplementować klasę lekkości z właściwościami implementowanymi automatycznie (Przewodnik programowania C#)

W tym przykładzie pokazano, jak utworzyć niezmienne klasy lekki, który służy tylko do hermetyzacji zestaw właściwości auto implementowane. Użyj tego rodzaju konstrukcji zamiast struktury, gdy należy użyć semantyki typu odwołania.

Właściwość niezmienną można wykonać na dwa sposoby:

- Można zadeklarować [set](../../language-reference/keywords/set.md) akcesor być [prywatny](../../language-reference/keywords/private.md).  Właściwość jest tylko settable w ramach typu, ale jest niezmienne dla konsumentów.

  Podczas deklarowania `set` akcesor prywatny, nie można użyć inicjatora obiektu do zainicjowania właściwości. Należy użyć konstruktora lub metody fabrycznej.
- Można zadeklarować tylko [get](../../language-reference/keywords/get.md) akcesor, co sprawia, że właściwość niezmienne wszędzie z wyjątkiem konstruktora typu.

W poniższym przykładzie pokazano, jak właściwość z tylko get akcesor różni się niż jeden z get i zestaw prywatny.

```csharp
class Contact
{
    public string Name { get; }
    public string Address { get; private set; }

    public Contact(string contactName, string contactAddress)
    {
        // Both properties are accessible in the constructor.
        Name = contactName;
        Address = contactAddress;
    }

    // Name isn't assignable here. This will generate a compile error.
    //public void ChangeName(string newName) => Name = newName;

    // Address is assignable here.
    public void ChangeAddress(string newAddress) => Address = newAddress
}
```

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono dwa sposoby implementowania niezmiennej klasy, która ma właściwości implementowane automatycznie. Każdy sposób deklaruje jedną z właściwości `set` z prywatną i jedną `get` z właściwości tylko.  Pierwsza klasa używa konstruktora tylko do inicjowania właściwości, a druga klasa używa statycznej metody fabrycznej, która wywołuje konstruktora.

```csharp
// This class is immutable. After an object is created,
// it cannot be modified from outside the class. It uses a
// constructor to initialize its properties.
class Contact
{
    // Read-only property.
    public string Name { get; }

    // Read-write property with a private set accessor.
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
    // Read-write property with a private set accessor.
    public string Name { get; private set; }

    // Read-only property.
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

Kompilator tworzy pola zapasowe dla każdej właściwości implementowane automatycznie. Pola nie są dostępne bezpośrednio z kodu źródłowego.

## <a name="see-also"></a>Zobacz też

- [Właściwości](./properties.md)
- [Struct](../../language-reference/builtin-types/struct.md)
- [Inicjatory obiektów i kolekcji](./object-and-collection-initializers.md)
