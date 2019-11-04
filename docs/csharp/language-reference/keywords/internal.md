---
title: C# odwołanie wewnętrzne
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: f72866cafbf291310d88fc6f18a5a15dc77c621d
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422729"
---
# <a name="internal-c-reference"></a>internal (odwołanie w C#)
Słowo kluczowe `internal` jest [modyfikatorem dostępu](./access-modifiers.md) dla typów i elementów członkowskich typu. 
  
 > Ta strona obejmuje `internal` dostępu. Słowo kluczowe `internal` jest również częścią modyfikatora dostępu [`protected internal`](./protected-internal.md) .
  
Typy wewnętrzne lub składowe są dostępne tylko w plikach w tym samym zestawie, jak w poniższym przykładzie:  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 Aby uzyskać porównanie `internal` z innymi modyfikatorami dostępu, zobacz [poziomy ułatwień](./accessibility-levels.md) dostępu i [Modyfikatory dostęp](../../programming-guide/classes-and-structs/access-modifiers.md).  
  
 Aby uzyskać więcej informacji o zestawach, zobacz [zestawy w programie .NET](../../../standard/assembly/index.md).  
  
 Typowym zastosowaniem dostępu wewnętrznego jest w programowaniu opartym na składnikach, ponieważ umożliwia ono grupom współdziałanie w sposób prywatny bez ujawniania pozostałej części kodu aplikacji. Na przykład struktura do tworzenia graficznych interfejsów użytkownika może zapewnić `Control` i `Form` klas, które współpracują z użytkownikami z dostępem wewnętrznym. Ponieważ te składowe są wewnętrzne, nie są one widoczne dla kodu, który używa struktury.  
  
 Wystąpił błąd podczas odwoływania się do typu lub elementu członkowskiego z dostępem wewnętrznym poza zestawem, w ramach którego został zdefiniowany.  
  
## <a name="example"></a>Przykład  
 Ten przykład zawiera dwa pliki, `Assembly1.cs` i `Assembly1_a.cs`. Pierwszy plik zawiera wewnętrzną klasę bazową `BaseClass`. W drugim pliku próba wystąpienia `BaseClass` spowoduje wystąpienie błędu.  
  
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
      var myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie należy użyć tych samych plików, które zostały użyte w przykładzie 1, i zmienić poziom dostępności `BaseClass` na `public`. Zmień również poziom dostępności `intM` Członkowskich, aby `internal`. W takim przypadku można utworzyć wystąpienie klasy, ale nie można uzyskać dostępu do wewnętrznego elementu członkowskiego.  
  
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
      var myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [zadeklarowane ułatwienia dostępu](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz także

- [C#Odwoła](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Modyfikatory dostępu](./access-modifiers.md)
- [Poziomy ułatwień dostępu](./accessibility-levels.md)
- [Modyfikatory](index.md)
- [public](./public.md)
- [private](./private.md)
- [protected](./protected.md)
