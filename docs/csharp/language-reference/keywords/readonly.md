---
title: readonly (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: d2f8a2f192dc319ad806aeef4bfbaeecc44b07a3
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172636"
---
# <a name="readonly-c-reference"></a>readonly (odwołanie w C#)
`readonly` — Słowo kluczowe jest modyfikator, pomocne w polach. Jeżeli zawiera deklarację pola `readonly` , modyfikator przypisania do pól wprowadzone przez deklaracja może występować tylko w ramach deklaracji lub w Konstruktorze w tej samej klasy.  
  
## <a name="readonly-field-example"></a>Przykład pola tylko do odczytu  
 W tym przykładzie wartość pola `year` nie można zmienić w metodzie `ChangeYear`, nawet jeśli jest przypisywana wartość w konstruktorze klasy:  
  
 [!code-csharp[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]  
  
 Można przypisać wartości do `readonly` tylko w następujących sytuacjach:  
  
-   Jeśli zmienna jest ustawiana w deklaracji, na przykład:  
  
    ```csharp  
    public readonly int y = 5;  
    ```  
  
-   Dla pola wystąpienia w konstruktorach wystąpień klasy zawiera deklarację pola lub statycznego pola statycznego konstruktora klasy zawiera deklarację pola. Te są również tylko kontekstów, w których jest nieprawidłowy do przekazania `readonly` pole jako [limit](../../../csharp/language-reference/keywords/out-parameter-modifier.md) lub [ref](../../../csharp/language-reference/keywords/ref.md) parametru.  
  
> [!NOTE]
>  `readonly` — Słowo kluczowe różni się od [const](../../../csharp/language-reference/keywords/const.md) — słowo kluczowe. A `const` pól mogą być inicjowane tylko w deklaracji pola. A `readonly` pól mogą być inicjowane w deklaracji lub w konstruktorze. W związku z tym `readonly` pola mogą mieć różne wartości w zależności od Konstruktor używany. Ponadto podczas `const` pole jest stałą czasu kompilacji `readonly` pole może być używane dla środowiska uruchomieniowego stałe, jak w poniższym przykładzie:  
  
```csharp  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## <a name="comparing-readonly-and-non-readonly-instance-fields"></a>Porównanie pola wystąpienia tylko do odczytu i nie tylko do odczytu  
 [!code-csharp[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]  
  
 W poprzednim przykładzie, jeśli używana jest instrukcja następująco:  
  
 `p2.y = 66;        // Error`  
  
 otrzymasz komunikat o błędzie kompilatora:  
  
 `The left-hand side of an assignment must be an l-value`  
  
 która jest ten sam błąd, które pojawia się podczas próby przypisać wartość stałą.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
 [const](../../../csharp/language-reference/keywords/const.md)  
 [Pola](../../../csharp/programming-guide/classes-and-structs/fields.md)
