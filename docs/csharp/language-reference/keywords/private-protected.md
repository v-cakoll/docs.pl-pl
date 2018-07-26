---
title: prywatny chroniony (odwołanie w C#)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 0d511f55f44511590fbe92a98cef118e0cb482e2
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961135"
---
# <a name="private-protected-c-reference"></a>prywatny chroniony (odwołanie w C#)
`private protected` Kombinacja słów kluczowych jest modyfikator dostępu składowej. Prywatny chroniony element członkowski jest dostępna przez typy pochodne z zawierającego klasy, ale tylko w ramach własnego zestawu zawierającego. Porównanie `private protected` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md). 

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
 Ten przykład zawiera dwa pliki `Assembly1.cs` i `Assembly2.cs`. Pierwszy plik zawiera klasę bazową publicznych `BaseClass`oraz typu pochodnego w `DerivedClass1`. `BaseClass` jest właścicielem prywatnego elementu członkowskiego chronionego `myValue`, który `DerivedClass1` próbuje uzyskać dostęp na dwa sposoby. Pierwsza próba dostępu do `myValue` za pośrednictwem wystąpienia `BaseClass` powoduje wygenerowanie błędu. Jednak można go użyć jako dziedziczonego członka w `DerivedClass1` zakończy się powodzeniem.
W drugim pliku, próba uzyskania dostępu do `myValue` jako dziedziczonego członka `DerivedClass2` generuje błąd, ponieważ nie jest tylko dostępny przez typy pochodne w Assembly1. 

 Składowe struktury nie mogą być `private protected` ponieważ struktura nie może być dziedziczona.  
  
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
