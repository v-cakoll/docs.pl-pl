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
ms.openlocfilehash: 7d97b7b05645b02a31af848c97758c7a1f6423b9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602083"
---
# <a name="internal-c-reference"></a>internal (odwołanie w C#)
Słowo kluczowe jest modyfikatorem dostępu dla typów i elementów członkowskich typu. [](./access-modifiers.md) `internal` 
  
 > Ta strona dotyczy `internal` dostępu. Słowo kluczowe jest również częścią [`protected internal`](./protected-internal.md) modyfikatora dostępu. `internal`
  
Typy wewnętrzne lub składowe są dostępne tylko w plikach w tym samym zestawie, jak w poniższym przykładzie:  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 Aby uzyskać porównanie `internal` z innymi modyfikatorami dostępu, zobacz [poziomy dostępności](./accessibility-levels.md) i Modyfikatory [dostępu](../../programming-guide/classes-and-structs/access-modifiers.md).  
  
 Aby uzyskać więcej informacji o zestawach, zobacz [zestawy w programie .NET](../../../standard/assembly/index.md).  
  
 Typowym zastosowaniem dostępu wewnętrznego jest w programowaniu opartym na składnikach, ponieważ umożliwia ono grupom współdziałanie w sposób prywatny bez ujawniania pozostałej części kodu aplikacji. Na przykład struktura do tworzenia graficznych interfejsów użytkownika mogłaby udostępniać `Control` klasy i `Form` współdziałać z użytkownikami z dostępem wewnętrznym. Ponieważ te składowe są wewnętrzne, nie są one widoczne dla kodu, który używa struktury.  
  
 Wystąpił błąd podczas odwoływania się do typu lub elementu członkowskiego z dostępem wewnętrznym poza zestawem, w ramach którego został zdefiniowany.  
  
## <a name="example"></a>Przykład  
 Ten przykład zawiera dwa pliki `Assembly1.cs` i. `Assembly1_a.cs` Pierwszy plik zawiera wewnętrzną klasę `BaseClass`bazową. W drugim pliku próba wystąpienia `BaseClass` spowoduje wystąpienie błędu.  
  
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
 W tym przykładzie należy użyć tych samych plików, które zostały użyte w przykładzie 1, i zmienić poziom `BaseClass` dostępności na. `public` Zmień również poziom dostępności elementu członkowskiego `intM` na. `internal` W takim przypadku można utworzyć wystąpienie klasy, ale nie można uzyskać dostępu do wewnętrznego elementu członkowskiego.  
  
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

Aby uzyskać więcej informacji, zobacz [zadeklarowane ułatwienia dostępu](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Modyfikatory dostępu](./access-modifiers.md)
- [Poziomy ułatwień dostępu](./accessibility-levels.md)
- [Modyfikatory](./modifiers.md)
- [public](./public.md)
- [private](./private.md)
- [protected](./protected.md)
