---
title: chronione wewnętrzne - C# Odwołanie
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 877df74b51fb859043171619f5687ecddb8409d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713199"
---
# <a name="protected-internal-c-reference"></a>chroniony wewnętrzny (odwołanie do Języka C#)

Kombinacja `protected internal` słów kluczowych jest modyfikatorem dostępu do elementów członkowskich. Chroniony wewnętrzny element członkowski jest dostępny z bieżącego zestawu lub z typów, które są uzyskiwane z klasy zawierającej. Aby porównać `protected internal` inne modyfikatory dostępu, zobacz [Poziomy ułatwień dostępu](accessibility-levels.md).

## <a name="example"></a>Przykład

Chroniony wewnętrzny element członkowski klasy podstawowej jest dostępny z dowolnego typu w jego zestawie zawierającym. Jest również dostępny w klasie pochodnej znajduje się w innym zestawie tylko wtedy, gdy dostęp występuje za pośrednictwem zmiennej typu klasy pochodnej. Rozważmy na przykład następujący segment kodu:

```csharp
// Assembly1.cs
// Compile with: /target:library
public class BaseClass
{
   protected internal int myValue = 0;
}

class TestAccess
{
    void Access()
    {
        var baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass : BaseClass
{
    static void Main()
    {
        var baseObject = new BaseClass();
        var derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```

W tym przykładzie `Assembly1.cs` znajdują `Assembly2.cs`się dwa pliki i .
Pierwszy plik zawiera publiczną `BaseClass`klasę podstawową, `TestAccess`a inna klasa . `BaseClass`jest właścicielem chronionego `myValue`elementu wewnętrznego, `TestAccess` który jest dostępny przez typ.
W drugim pliku próba dostępu `myValue` za pośrednictwem wystąpienia `BaseClass` spowoduje błąd, podczas gdy dostęp do tego elementu `DerivedClass` członkowskiego za pośrednictwem wystąpienia klasy pochodnej, zakończy się pomyślnie.

Elementy członkowskie struktury `protected internal` nie mogą być, ponieważ struktura nie może być dziedziczona.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory dostępu](access-modifiers.md)
- [Poziomy ułatwień dostępu](accessibility-levels.md)
- [Modyfikatory](index.md)
- [Publicznego](public.md)
- [Prywatny](private.md)
- [Wewnętrznego](internal.md)
- [Obawy dotyczące zabezpieczeń wewnętrznych wirtualnych słów kluczowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
