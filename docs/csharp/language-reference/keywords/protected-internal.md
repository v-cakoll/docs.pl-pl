---
title: chronionych wewnętrznych (odwołanie w C#)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 1a305cb84989f12350e2e7cc28dd18f9d0c7ae5e
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46529953"
---
# <a name="protected-internal-c-reference"></a>chronionych wewnętrznych (odwołanie w C#)

`protected internal` Kombinacja słów kluczowych jest modyfikator dostępu składowej. Chronionych wewnętrznych składowych jest możliwy z bieżącego zestawu lub typy pochodzące z klasy zawierającej. Porównanie `protected internal` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](accessibility-levels.md).

## <a name="example"></a>Przykład

Chronionych wewnętrznych elementu członkowskiego klasy bazowej jest dostępna z dowolnego typu w ramach własnego zestawu zawierającego. Jest również dostępna w klasie pochodnej znajduje się w innym zestawie, tylko wtedy, gdy dostęp odbywa się za pośrednictwem zmiennej o typie klasy pochodnej. Na przykład rozważmy następujący segment kodu:

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
        BaseClass baseObject = new BaseClass();
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
        BaseClass baseObject = new BaseClass();
        DerivedClass derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```
Ten przykład zawiera dwa pliki `Assembly1.cs` i `Assembly2.cs`.
Pierwszy plik zawiera klasę bazową publicznych `BaseClass`oraz inną klasę `TestAccess`. `BaseClass` jest właścicielem wewnętrzny elementu członkowskiego chronionego `myValue`, który jest dostępny po `TestAccess` typu.
W drugim pliku, próba uzyskania dostępu do `myValue` za pośrednictwem wystąpienia `BaseClass` wystąpi błąd, podczas dostępu do tego elementu członkowskiego przez wystąpienie klasy pochodnej, `DerivedClass` zakończy się powodzeniem.

Składowe struktury nie mogą być `protected internal` ponieważ struktura nie może być dziedziczona.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory dostępu](access-modifiers.md)
- [Poziomy ułatwień dostępu](accessibility-levels.md)
- [Modyfikatory](modifiers.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [Kwestie bezpieczeństwa wewnętrznych wirtualnych słów kluczowych](https://docs.microsoft.com/en-us/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))