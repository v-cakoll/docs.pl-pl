---
title: wewnętrzny - C# Referencje
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: e5a5ca18828b689241abbb6d80c5adc51efb073c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173604"
---
# <a name="internal-c-reference"></a>internal (odwołanie w C#)
Słowo `internal` kluczowe jest [modyfikatorem dostępu](./access-modifiers.md) dla typów i elementów członkowskich typu.
  
 > Ta strona `internal` obejmuje dostęp. Słowo `internal` kluczowe jest również [`protected internal`](./protected-internal.md) częścią modyfikatora dostępu.
  
Typy wewnętrzne lub elementy członkowskie są dostępne tylko w plikach w tym samym zestawie, jak w tym przykładzie:  
  
```csharp  
public class BaseClass
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 Aby porównać `internal` z innymi modyfikatorami dostępu, zobacz [Poziomy ułatwień dostępu](./accessibility-levels.md) i [modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md).  
  
 Aby uzyskać więcej informacji na temat zestawów, zobacz [Zestawy w .NET](../../../standard/assembly/index.md).  
  
 Typowe użycie dostępu wewnętrznego jest w rozwoju opartym na składnikach, ponieważ umożliwia grupie składników współpracę w sposób prywatny bez narażenia na resztę kodu aplikacji. Na przykład struktura do tworzenia graficznych interfejsów użytkownika może zapewnić `Control` i `Form` klas, które współpracują przy użyciu elementów członkowskich z dostępem wewnętrznym. Ponieważ te elementy członkowskie są wewnętrzne, nie są one udostępniane do kodu, który używa struktury.  
  
 Jest to błąd, aby odwołać się do typu lub elementu członkowskiego z dostępem wewnętrznym poza zestawem, w którym został zdefiniowany.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `Assembly1.cs` znajdują `Assembly1_a.cs`się dwa pliki i . Pierwszy plik zawiera wewnętrzną `BaseClass`klasę podstawową. W drugim pliku próba wystąpienia spowoduje `BaseClass` wywołanie błędu.  
  
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
 W tym przykładzie użyj tych samych plików, które zostały `BaseClass` użyte `public`w przykładzie 1 i zmień poziom ułatwień dostępu na . Zmień również poziom dostępności `intM` elementu `internal`członkowskiego na . W takim przypadku można utworzyć wystąpienia klasy, ale nie można uzyskać dostępu do elementu członkowskiego wewnętrznego.  
  
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

Aby uzyskać więcej informacji, zobacz [Zadeklarowana dostępność](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Modyfikatory dostępu](./access-modifiers.md)
- [Poziomy ułatwień dostępu](./accessibility-levels.md)
- [Modyfikatory](index.md)
- [Publicznego](./public.md)
- [Prywatny](./private.md)
- [protected](./protected.md)
