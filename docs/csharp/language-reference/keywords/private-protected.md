---
title: prywatny chroniony (odwołanie w C#)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 4a4ee999fe932674e854b1428ab33b33bc71d2ad
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419537"
---
# <a name="private-protected-c-reference"></a>prywatny chroniony (odwołanie w C#)

`private protected` Kombinacja słów kluczowych jest modyfikator dostępu składowej. Prywatny chroniony element członkowski jest dostępna przez typy pochodne z zawierającego klasy, ale tylko w ramach własnego zestawu zawierającego. Porównanie `private protected` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](accessibility-levels.md).

> [!NOTE]
> `private protected` Modyfikator dostępu jest nieprawidłowy w języku C# w wersji 7.2 lub nowszy.

## <a name="example"></a>Przykład

Prywatne chronione elementy członkowskie klasy bazowej jest dostępna z typów pochodnych w jego zawierające zestaw, tylko wtedy, gdy typ klasy pochodnej zmiennej typu statycznego. Na przykład rozważmy następujący segment kodu:  

```csharp
// Assembly1.cs  
// Compile with: /target:library  
public class BaseClass
{
    private protected int myValue = 0;
}

public class DerivedClass1 : BaseClass
{
    void Access()
    {
        BaseClass baseObject = new BaseClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 5;  

        // OK, accessed through the current derived class instance
        myValue = 5;
    }
}
```

```csharp
// Assembly2.cs  
// Compile with: /reference:Assembly1.dll  
class DerivedClass2 : BaseClass
{
    void Access()
    {
        // Error CS0122, because myValue can only be
        // accessed by types in Assembly1
        // myValue = 10;
    }
}
```

Ten przykład zawiera dwa pliki `Assembly1.cs` i `Assembly2.cs`.
Pierwszy plik zawiera klasę bazową publicznych `BaseClass`oraz typu pochodnego w `DerivedClass1`. `BaseClass` jest właścicielem prywatnego elementu członkowskiego chronionego `myValue`, który `DerivedClass1` próbuje uzyskać dostęp na dwa sposoby. Pierwsza próba dostępu do `myValue` za pośrednictwem wystąpienia `BaseClass` powoduje wygenerowanie błędu. Jednak można go użyć jako dziedziczonego członka w `DerivedClass1` zakończy się powodzeniem.
W drugim pliku, próba uzyskania dostępu do `myValue` jako dziedziczonego członka `DerivedClass2` generuje błąd, ponieważ nie jest tylko dostępny przez typy pochodne w Assembly1.

Składowe struktury nie mogą być `private protected` ponieważ struktura nie może być dziedziczona.  

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
- [Kwestie bezpieczeństwa wewnętrznych wirtualnych słów kluczowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))