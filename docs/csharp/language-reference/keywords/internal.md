---
title: "internal (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a3b115022ed2b38dfcfbbfad3c5fc00e0203b255
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="internal-c-reference"></a>internal (odwołanie w C#)
`internal` — Słowo kluczowe jest [modyfikator dostępu](../../../csharp/language-reference/keywords/access-modifiers.md) typy i elementy członkowskie typu. 
  
 > Ta strona zawiera `internal` dostępu. `internal` — Słowo kluczowe jest również częścią [ `protected internal` ](./protected-internal.md) modyfikator dostępu.
  
Wewnętrzne typy i elementy członkowskie są dostępne tylko w plikach w tym samym zestawie, jak w poniższym przykładzie:  
  
```  
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
  
```  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```  
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
  
```  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```  
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
 [publiczny](../../../csharp/language-reference/keywords/public.md)  
 [prywatne](../../../csharp/language-reference/keywords/private.md)  
 [chronione](../../../csharp/language-reference/keywords/protected.md)
