---
title: chronionych wewnętrznych (odwołanie w C#)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 5ba2c811a1a4f095bcee65ed6678a7dc50fe94db
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244861"
---
# <a name="protected-internal-c-reference"></a>chronionych wewnętrznych (odwołanie w C#)
`protected internal` Kombinacja słów kluczowych jest modyfikator dostępu składowej. Chronionych wewnętrznych składowych jest możliwy z bieżącego zestawu lub typy pochodzące z klasy zawierającej. Porównanie `protected internal` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md). 
   
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
 Ten przykład zawiera dwa pliki `Assembly1.cs` i `Assembly2.cs`. Pierwszy plik zawiera klasę bazową publicznych `BaseClass`oraz inną klasę `TestAccess`. `BaseClass` jest właścicielem wewnętrzny elementu członkowskiego chronionego `myValue`, który jest dostępny po `TestAccess` typu. W drugim pliku, próba uzyskania dostępu do `myValue` za pośrednictwem wystąpienia `BaseClass` wystąpi błąd, podczas dostępu do tego elementu członkowskiego przez wystąpienie klasy pochodnej, `DerivedClass` zakończy się powodzeniem. 

 Składowe struktury nie mogą być `protected internal` ponieważ struktura nie może być dziedziczona.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)   
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)   
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)   
 [Modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)   
 [Publiczne](../../../csharp/language-reference/keywords/public.md)   
 [Prywatne](../../../csharp/language-reference/keywords/private.md)   
 [Wewnętrzne](../../../csharp/language-reference/keywords/internal.md)   
 [Kwestie bezpieczeństwa wewnętrznych wirtualnych słów kluczowych](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))
