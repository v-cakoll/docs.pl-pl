---
title: "private (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords: private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9cc8f86166888b47a758e200182d319c68ca6d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="private-c-reference"></a>private (odwołanie w C#)
`private` — Słowo kluczowe jest modyfikator dostępu elementu członkowskiego. 
   
 > Ta strona zawiera `private` dostępu. `private` — Słowo kluczowe jest również częścią [ `private protected` ](./private-protected.md) modyfikator dostępu.
  
Prywatny dostęp jest najbardziej ograniczająca poziom dostępu. Prywatne elementy członkowskie są dostępne tylko w treści klasy lub struktury, w której zostały zgłoszone, jak w poniższym przykładzie:  
  
```  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  

 Zagnieżdżone typy w tym samym treści można także uzyskać dostęp do tych prywatne elementy członkowskie.  
  
 Jest to błąd kompilacji do odwołania prywatnego elementu członkowskiego spoza klasy lub struktury, w którym jest zadeklarowany.  
  
 Porównanie `private` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md) i [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `Employee` klasa zawiera dwa elementy członkowskie danych prywatnych, `name` i `salary`. Jako prywatne elementy członkowskie ich nie są dostępne z wyjątkiem metodami elementu członkowskiego. Metody publiczne o nazwie `GetName` i `Salary` są dodawane do dostęp do kontrolowanego prywatne elementy członkowskie. `name` Elementu członkowskiego jest dostępny na publiczną metodę i `salary` elementu członkowskiego jest dostępny i publicznej właściwości tylko do odczytu. (Zobacz [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md) Aby uzyskać więcej informacji.)  
  
 [!code-csharp[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
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
 [chronione](../../../csharp/language-reference/keywords/protected.md)  
 [wewnętrzny](../../../csharp/language-reference/keywords/internal.md)
