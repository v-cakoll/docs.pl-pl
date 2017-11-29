---
title: "chronionych wewnętrznych (odwołanie w C#)"
ms.date: 11/15/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
author: sputier
ms.author: wiwagn
ms.openlocfilehash: f9004a5e8d65179c9ff2e30688e63c14c95ab431
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="protected-internal-c-reference"></a>chronionych wewnętrznych (odwołanie w C#)
`protected internal` Kombinacja słów kluczowych jest modyfikator dostępu elementu członkowskiego. Chroniony element członkowski wewnętrznego jest dostępny, z bieżącego zestawu lub typów pochodzących od klasy zawierającego. Porównanie `protected internal` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md). 
   
## <a name="example"></a>Przykład  
 Wewnętrzny chroniony element członkowski klasy podstawowej jest dostępna z dowolnego typu, w ramach zawierający go zestaw. Jest również dostępna w klasie pochodnej, która znajduje się w innym zestawie tylko wtedy, gdy występuje dostęp za pośrednictwem zmiennej typu klasy pochodnej. Rozważmy na przykład następujący segment kodu:  

```
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
  
```  
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
 Ten przykład zawiera dwa pliki `Assembly1.cs` i `Assembly2.cs`. Pierwszy plik zawiera klasę podstawową publicznego `BaseClass`, a inna klasa `TestAccess`. `BaseClass`właścicielem członka chronionego wewnętrzny `myValue`, który jest dostępny po `TestAccess` typu. W drugim pliku, próba uzyskania dostępu do `myValue` za pośrednictwem wystąpienia `BaseClass` utworzy wystąpił błąd podczas dostępu do tego elementu członkowskiego przez wystąpienie klasy pochodnej, `DerivedClass` powiedzie się. 

 Członkowie struktury nie mogą być `protected internal` ponieważ struktury nie może być dziedziczona.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)   
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)   
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)   
 [Modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)   
 [publiczny](../../../csharp/language-reference/keywords/public.md)   
 [prywatne](../../../csharp/language-reference/keywords/private.md)   
 [wewnętrzny](../../../csharp/language-reference/keywords/internal.md)   
 [Problemy z zabezpieczeniami dla wewnętrznego wirtualnego słowa kluczowe](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))
