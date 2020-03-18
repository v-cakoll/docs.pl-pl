---
title: chronione prywatne — odwołanie do języka C#
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: a73d61712075cf24d2b94c505104df1fade629e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713212"
---
# <a name="private-protected-c-reference"></a>chronione prywatne (odwołanie do języka C#)

Kombinacja `private protected` słów kluczowych jest modyfikatorem dostępu do elementów członkowskich. Prywatny chroniony element członkowski jest dostępny przez typy pochodzące z klasy zawierającej, ale tylko w jego zestawie zawierającym. Aby porównać `private protected` inne modyfikatory dostępu, zobacz [Poziomy ułatwień dostępu](accessibility-levels.md).

> [!NOTE]
> Modyfikator `private protected` dostępu jest prawidłowy w wersji C# 7.2 i nowszych.

## <a name="example"></a>Przykład

Prywatny chroniony element członkowski klasy podstawowej jest dostępny z typów pochodnych w jego zestawie zawierającym tylko wtedy, gdy typ statyczny zmiennej jest typem klasy pochodnej. Rozważmy na przykład następujący segment kodu:  

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

W tym przykładzie `Assembly1.cs` znajdują `Assembly2.cs`się dwa pliki i .
Pierwszy plik zawiera publiczną `BaseClass`klasę podstawową i typ `DerivedClass1`pochodzący z niej. `BaseClass`jest właścicielem prywatnego `myValue`chronionego `DerivedClass1` elementu członkowskiego, który próbuje uzyskać dostęp na dwa sposoby. Pierwsza próba dostępu `myValue` za pośrednictwem wystąpienia `BaseClass` spowoduje błąd. Jednak próba użycia go jako dziedziczonego `DerivedClass1` elementu członkowskiego w zakończy się pomyślnie.
W drugim pliku próba dostępu `myValue` jako dziedziczony element członkowski `DerivedClass2` spowoduje błąd, ponieważ jest dostępny tylko przez typy pochodne w Assembly1.

Elementy członkowskie struktury `private protected` nie mogą być, ponieważ struktura nie może być dziedziczona.  

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
