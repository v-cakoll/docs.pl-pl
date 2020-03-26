---
title: private protected - C# Reference
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 01a8b716ce87a63a50a92a25b2842f7bb12d4c9f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134365"
---
# <a name="private-protected-c-reference"></a>private protected (c# Reference)

Kombinacja `private protected` słów kluczowych jest modyfikatorem dostępu do członków. Prywatny chroniony element członkowski jest dostępny dla typów pochodzących z klasy zawierającej, ale tylko w ramach jego zestawu zawierającego. Aby zapoznać `private protected` się z innymi modyfikatorami dostępu, zobacz [Poziomy ułatwień dostępu](accessibility-levels.md).

> [!NOTE]
> Modyfikator `private protected` dostępu jest prawidłowy w języku C# w wersji 7.2 i nowszych.

## <a name="example"></a>Przykład

Prywatny chroniony element członkowski klasy podstawowej jest dostępny z typów pochodnych w zestawie zawierającym tylko wtedy, gdy typ statyczny zmiennej jest typem klasy pochodnej. Rozważmy na przykład następujący segment kodu:  

```csharp
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

W tym przykładzie `Assembly1.cs` `Assembly2.cs`znajdują się dwa pliki i .
Pierwszy plik zawiera publiczną `BaseClass`klasę podstawową i typ `DerivedClass1`pochodną. `BaseClass`jest właścicielem prywatnego chronionego `myValue` `DerivedClass1` członka, który próbuje uzyskać dostęp na dwa sposoby. Pierwsza próba uzyskania `myValue` dostępu za `BaseClass` pośrednictwem wystąpienia spowoduje błąd. Jednak próba użycia go jako dziedziczonego `DerivedClass1` elementu członkowskiego w zakończy się pomyślnie.
W drugim pliku próba dostępu `myValue` jako dziedziczony `DerivedClass2` element członkowski spowoduje błąd, ponieważ jest dostępny tylko dla typów pochodnych w Assembly1.

Struct elementów `private protected` członkowskich nie może być, ponieważ struktura nie może być dziedziczona.  

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [C# Przewodnik programowania](../../programming-guide/index.md)
- [C# Słowa kluczowe](index.md)
- [Modyfikatory dostępu](access-modifiers.md)
- [Poziomy ułatwień dostępu](accessibility-levels.md)
- [Modyfikatory](index.md)
- [Publicznego](public.md)
- [Prywatny](private.md)
- [Wewnętrznego](internal.md)
- [Kwestie bezpieczeństwa wewnętrznych wirtualnych słów kluczowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
