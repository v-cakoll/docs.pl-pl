---
title: IsTrue, operator
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: bc129d3a3aec76285d5ea8fb727fc72c3064c9cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370651"
---
# <a name="istrue-operator-visual-basic"></a>IsTrue — Operator (Visual Basic)
Określa, czy wyrażenie jest `True` .  
  
 Nie można `IsTrue` jawnie wywołać w kodzie, ale kompilator Visual Basic może użyć go do wygenerowania kodu z `OrElse` klauzul. W przypadku zdefiniowania klasy lub struktury, a następnie użycia zmiennej tego typu w `OrElse` klauzuli, należy zdefiniować `IsTrue` dla tej klasy lub struktury.  
  
 Kompilator traktuje `IsTrue` Operatory i `IsFalse` jako *pasującą parę*. Oznacza to, że w przypadku zdefiniowania jednego z nich należy również zdefiniować drugi.  
  
## <a name="compiler-use-of-istrue"></a>Użycie kompilatora IsTrue  
 Po zdefiniowaniu klasy lub struktury można użyć zmiennej tego typu w `For` `If` instrukcji,, `Else If` , lub `While` w `When` klauzuli. W takim przypadku kompilator wymaga operatora, który konwertuje typ na `Boolean` wartość, aby umożliwić przetestowanie warunku. Wyszukuje odpowiedni operator w następującej kolejności:  
  
1. Rozszerzający Operator konwersji z klasy lub struktury do `Boolean` .  
  
2. Rozszerzający Operator konwersji z klasy lub struktury do `Boolean?` .  
  
3. `IsTrue`Operator klasy lub struktury.  
  
4. Zawężanie konwersji na `Boolean?` , która nie obejmuje konwersji z `Boolean` do `Boolean?` .  
  
5. Wąski Operator konwersji z klasy lub struktury do `Boolean` .  
  
 Jeśli nie zdefiniowano żadnej konwersji do `Boolean` `IsTrue` operatora OR, kompilator sygnalizuje błąd.  
  
> [!NOTE]
> `IsTrue`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może zmienić jego zachowanie, gdy jego operand ma typ tej klasy lub struktury. Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu definiuje kontur struktury, która zawiera definicje `IsFalse` `IsTrue` operatorów i.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Zobacz też

- [IsFalse, operator](isfalse-operator.md)
- [Instrukcje: definiowanie operatora](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [OrElse, operator](orelse-operator.md)
