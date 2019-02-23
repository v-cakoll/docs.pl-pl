---
title: wewnętrzne — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: aefb806b452452d4837b29b6ab11ce158ea412bc
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745424"
---
# <a name="internal-c-reference"></a>internal (odwołanie w C#)
`internal` Słowo kluczowe jest [modyfikator dostępu](../../../csharp/language-reference/keywords/access-modifiers.md) dla typów i elementów członkowskich typu. 
  
 > Ta strona obejmuje `internal` dostępu. `internal` — Słowo kluczowe jest również częścią [ `protected internal` ](./protected-internal.md) modyfikator dostępu.
  
Typy wewnętrzne lub elementy członkowskie są dostępne tylko z poziomu plików w tym samym zestawie, jak w poniższym przykładzie:  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  

 Porównanie `internal` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md) i [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Aby uzyskać więcej informacji na temat zestawów, zobacz [zestawy na platformie .NET](../../../standard/assembly/index.md).  
  
 Typowym zastosowaniem dostępu wewnętrznego jest opracowywany oparty na komponentach, ponieważ umożliwia grupy składników do współpracy w sposób prywatne bez ujawniania w pozostałej części kodu aplikacji. Na przykład można dostarczyć umożliwiająca tworzenie graficznych interfejsów użytkownika `Control` i `Form` klas, które współpracują przy użyciu elementów członkowskich z dostępem do wewnętrznych. Ponieważ te elementy członkowskie są wewnętrzne, nie są one widoczne do kodu, który używa programu framework.  
  
 Jest to błąd, aby odwoływać się do typu lub elementu członkowskiego z wewnętrznego dostępem spoza zestawu, w którym został zdefiniowany.  
  
## <a name="example"></a>Przykład  
 Ten przykład zawiera dwa pliki `Assembly1.cs` i `Assembly1_a.cs`. Pierwszy plik zawiera wewnętrzny klasy bazowej `BaseClass`. W drugim pliku, próba utworzenia wystąpienia `BaseClass` powoduje wygenerowanie błędu.  
  
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
 W tym przykładzie należy użyć tych samych plików, które są używane w przykładzie 1 i zmienić poziom dostępności `BaseClass` do `public`. Również zmienić poziom dostępności elementu członkowskiego `IntM` do `internal`. W takim przypadku można utworzyć wystąpienia klasy, ale nie masz dostępu do wewnętrznego elementu członkowskiego.  
  
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
// Compile with: /reference:Assembly2.dll  
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

Aby uzyskać więcej informacji, zobacz [zadeklarowana dostępność](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
- [Modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md)
- [Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md)
- [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)
- [public](../../../csharp/language-reference/keywords/public.md)
- [private](../../../csharp/language-reference/keywords/private.md)
- [protected](../../../csharp/language-reference/keywords/protected.md)
