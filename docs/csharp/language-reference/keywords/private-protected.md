---
title: Private Protected C# — odwołanie
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: a73d61712075cf24d2b94c505104df1fade629e9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713212"
---
# <a name="private-protected-c-reference"></a>prywatna chroniona (C# odwołanie)

Kombinacja słowa kluczowego `private protected` jest modyfikatorem dostępu składowej. Prywatna chroniona składowa jest dostępna dla typów pochodzących od klasy zawierającej, ale tylko w obrębie zawartego zestawu. Aby uzyskać porównanie `private protected` z innymi modyfikatorami dostępu, zobacz [poziomy dostępności](accessibility-levels.md).

> [!NOTE]
> Modyfikator dostępu `private protected` jest prawidłowy w C# wersji 7,2 i nowszych.

## <a name="example"></a>Przykład

Prywatna chroniona składowa klasy bazowej jest dostępna z typów pochodnych w jego zestawie zawierającym tylko wtedy, gdy typ statyczny zmiennej jest typem klasy pochodnej. Rozważmy na przykład następujący segment kodu:  

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
        var baseObject = new BaseClass();

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

Ten przykład zawiera dwa pliki, `Assembly1.cs` i `Assembly2.cs`.
Pierwszy plik zawiera publiczną klasę bazową, `BaseClass`i typ pochodny, `DerivedClass1`. `BaseClass` jest właścicielem prywatnej chronionej składowej, `myValue`, która `DerivedClass1` próbuje uzyskać dostęp na dwa sposoby. Pierwsza próba dostępu do `myValue` za pomocą wystąpienia `BaseClass` spowoduje wystąpienie błędu. Jednak próba użycia jej jako dziedziczonego elementu członkowskiego w `DerivedClass1` powiedzie się.
W drugim pliku próba uzyskania dostępu do `myValue` jako dziedziczonego elementu członkowskiego `DerivedClass2` spowoduje wystąpienie błędu, ponieważ jest on dostępny tylko dla typów pochodnych w assembly1.

Elementy członkowskie struktury nie mogą być `private protected`, ponieważ struktura nie może być dziedziczona.  

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
