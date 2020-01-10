---
title: chronione C# odwołanie wewnętrzne
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 877df74b51fb859043171619f5687ecddb8409d1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713199"
---
# <a name="protected-internal-c-reference"></a>chroniona wewnętrznieC# (odwołanie)

Kombinacja słowa kluczowego `protected internal` jest modyfikatorem dostępu składowej. Chroniony wewnętrzny element członkowski jest dostępny z bieżącego zestawu lub z typów, które pochodzą od klasy zawierającej. Aby uzyskać porównanie `protected internal` z innymi modyfikatorami dostępu, zobacz [poziomy dostępności](accessibility-levels.md).

## <a name="example"></a>Przykład

Chroniona wewnętrzna składowa klasy bazowej jest dostępna z dowolnego typu w obrębie zawierającego go zestawu. Jest ona również dostępna w klasie pochodnej znajdującej się w innym zestawie tylko wtedy, gdy dostęp odbywa się za pomocą zmiennej typu klasy pochodnej. Rozważmy na przykład następujący segment kodu:

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

Ten przykład zawiera dwa pliki, `Assembly1.cs` i `Assembly2.cs`.
Pierwszy plik zawiera publiczną klasę bazową, `BaseClass`i inną klasę, `TestAccess`. `BaseClass` jest właścicielem chronionego wewnętrznego elementu członkowskiego, `myValue`, do którego jest uzyskiwany dostęp za pomocą typu `TestAccess`.
W drugim pliku próba uzyskania dostępu do `myValue` za pomocą wystąpienia `BaseClass` spowoduje wystąpienie błędu, podczas gdy dostęp do tego elementu członkowskiego odbywa się za pomocą wystąpienia klasy pochodnej, `DerivedClass` powiedzie się.

Elementy członkowskie struktury nie mogą być `protected internal`, ponieważ struktura nie może być dziedziczona.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory dostępu](access-modifiers.md)
- [Poziomy ułatwień dostępu](accessibility-levels.md)
- [Modyfikatory](index.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [Zagadnienia dotyczące zabezpieczeń wewnętrznych wirtualnych słów kluczowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
