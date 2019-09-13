---
title: 'Instrukcje: Implementowanie klasy lekkiej z zaimplementowanymi właściwościami Przewodnik C# programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
ms.openlocfilehash: 626a44fbaa65f48e0d9fe66d83c44abb07eba379
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926757"
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="33765-102">Instrukcje: Implementowanie klasy lekkiej z zaimplementowanymi właściwościami (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="33765-102">How to: Implement a Lightweight Class with Auto-Implemented Properties (C# Programming Guide)</span></span>

<span data-ttu-id="33765-103">Ten przykład przedstawia sposób tworzenia niezmiennej klasy lekkiej, która służy tylko do hermetyzacji zestawu właściwości, które są implementowane.</span><span class="sxs-lookup"><span data-stu-id="33765-103">This example shows how to create an immutable lightweight class that serves only to encapsulate a set of auto-implemented properties.</span></span> <span data-ttu-id="33765-104">Użyj tego rodzaju konstrukcji zamiast struktury, gdy musisz użyć semantyki typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="33765-104">Use this kind of construct instead of a struct when you must use reference type semantics.</span></span>

<span data-ttu-id="33765-105">Można wprowadzić niemodyfikowalną właściwość na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="33765-105">You can make an immutable property in two ways:</span></span>

- <span data-ttu-id="33765-106">Można zadeklarować metodę dostępu [Set](../../language-reference/keywords/set.md) jako [prywatną](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="33765-106">You can declare the [set](../../language-reference/keywords/set.md) accessor to be [private](../../language-reference/keywords/private.md).</span></span>  <span data-ttu-id="33765-107">Właściwość jest tylko settable w obrębie typu, ale jest niezmienna dla odbiorców.</span><span class="sxs-lookup"><span data-stu-id="33765-107">The property is only settable within the type, but it is immutable to consumers.</span></span>

  <span data-ttu-id="33765-108">W przypadku deklarowania prywatnej `set` metody dostępu nie można użyć inicjatora obiektów do zainicjowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="33765-108">When you declare a private `set` accessor, you cannot use an object initializer to initialize the property.</span></span> <span data-ttu-id="33765-109">Musisz użyć konstruktora lub metody fabryki.</span><span class="sxs-lookup"><span data-stu-id="33765-109">You must use a constructor or a factory method.</span></span>
- <span data-ttu-id="33765-110">Można zadeklarować tylko metodę dostępu [Get](../../language-reference/keywords/get.md) , która sprawia, że właściwość jest niezmienna wszędzie z wyjątkiem konstruktora typu.</span><span class="sxs-lookup"><span data-stu-id="33765-110">You can declare only the [get](../../language-reference/keywords/get.md) accessor, which makes the property immutable everywhere except in the type’s constructor.</span></span>

## <a name="example"></a><span data-ttu-id="33765-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="33765-111">Example</span></span>

<span data-ttu-id="33765-112">Poniższy przykład przedstawia dwa sposoby implementacji niezmiennej klasy, która ma właściwości, które są implementowane.</span><span class="sxs-lookup"><span data-stu-id="33765-112">The following example shows two ways to implement an immutable class that has auto-implemented properties.</span></span> <span data-ttu-id="33765-113">Każdy ze sposobów deklaruje jedną z właściwości z prywatną `set` i jedną z właściwości `get` tylko z.</span><span class="sxs-lookup"><span data-stu-id="33765-113">Each way declares one of the properties with a private `set` and one of the properties with a `get` only.</span></span>  <span data-ttu-id="33765-114">Pierwsza klasa używa konstruktora tylko w celu zainicjowania właściwości, a druga Klasa używa metody fabryki statycznej, która wywołuje konstruktora.</span><span class="sxs-lookup"><span data-stu-id="33765-114">The first class uses a constructor only to initialize the properties, and the second class uses a static factory method that calls a constructor.</span></span>

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

<span data-ttu-id="33765-115">Kompilator tworzy pola kopii zapasowej dla każdej automatycznie zaimplementowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="33765-115">The compiler creates backing fields for each auto-implemented property.</span></span> <span data-ttu-id="33765-116">Pola są niedostępne bezpośrednio z kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="33765-116">The fields are not accessible directly from source code.</span></span>

## <a name="see-also"></a><span data-ttu-id="33765-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33765-117">See also</span></span>

- [<span data-ttu-id="33765-118">Właściwości</span><span class="sxs-lookup"><span data-stu-id="33765-118">Properties</span></span>](./properties.md)
- [<span data-ttu-id="33765-119">struct</span><span class="sxs-lookup"><span data-stu-id="33765-119">struct</span></span>](../../language-reference/keywords/struct.md)
- [<span data-ttu-id="33765-120">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="33765-120">Object and Collection Initializers</span></span>](./object-and-collection-initializers.md)
