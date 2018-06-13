---
title: internal (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: d2fcc19bb7bc6de373412e7728f3025647c0435d
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172675"
---
# <a name="internal-c-reference"></a>internal (odwołanie w C#)
`internal` — Słowo kluczowe jest [modyfikator dostępu](../../../csharp/language-reference/keywords/access-modifiers.md) typy i elementy członkowskie typu. 
  
 > Ta strona zawiera `internal` dostępu. `internal` — Słowo kluczowe jest również częścią [ `protected internal` ](./protected-internal.md) modyfikator dostępu.
  
Wewnętrzne typy i elementy członkowskie są dostępne tylko w plikach w tym samym zestawie, jak w poniższym przykładzie:  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  

 Porównanie `internal` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md) i [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Aby uzyskać więcej informacji na temat zestawów, zobacz [zestawy i Global Assembly Cache](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).  
  
 Zazwyczaj wewnętrznego dostępu jest używane w programowania opartego na składnik ponieważ dzięki grupy składników do współpracy w sposób prywatnej bez narażania z resztą kodu aplikacji. Na przykład można podać struktura umożliwiająca tworzenie graficznych interfejsów użytkownika `Control` i `Form` klasy, które współpracują przy użyciu elementów członkowskich z dostępem do wewnętrznego. Ponieważ te elementy członkowskie są wewnętrzne, ich nie są widoczne dla kodu, który używa programu framework.  
  
 Jest błąd, aby odwoływać się do typu lub elementu członkowskiego o wewnętrznej dostęp spoza zestawu, w którym został zdefiniowany.  
  
## <a name="example"></a>Przykład  
 Ten przykład zawiera dwa pliki `Assembly1.cs` i `Assembly1_a.cs`. Wewnętrzna klasa podstawowa zawiera pierwszy plik `BaseClass`. W drugim pliku, próba utworzenia wystąpienia `BaseClass` spowoduje błąd.  
  
```csharp  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```csharp  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie należy używać tych samych plików, które są używane w przykładzie 1 i zmienić poziom dostępności `BaseClass` do `public`. Również zmienić poziom dostępności elementu członkowskiego `IntM` do `internal`. W takim przypadku można utworzyć wystąpienia klasy, ale nie masz dostępu do wewnętrznego elementu członkowskiego.  
  
```csharp  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```csharp  
// Assembly2_a.cs  
// Compile with: /reference:Assembly1.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)
