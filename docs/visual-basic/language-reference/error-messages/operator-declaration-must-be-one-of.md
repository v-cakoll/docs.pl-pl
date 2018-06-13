---
title: 'Deklaracja operatora musi mieć jeden z: +,-, *,-, -, ^, &amp;, Like, Mod i, Or, Xor, nie &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;=, &gt; , &gt;=, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: eb1e7e8088ec8661be2469aff043c0f1a96e4d01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595023"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a>Deklaracja operatora musi mieć jeden z: +,-, *,\,/, ^, &amp;, Like, Mod i, Or, Xor, nie &lt; &lt;, &gt; &gt;...
Można zadeklarować tylko operatora, który jest uprawniona do przeciążenia. W poniższej tabeli wymieniono operatory, których można zadeklarować.  
  
|Typ|Operatory|  
|----------|---------------|  
|Jednoargumentowe|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|plików binarnych|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Konwersja (jednoargumentowy)|`CType`|  
  
 Należy pamiętać, że `=` operator porównania nie operator przypisania jest operator binarny listy.  
  
 **Identyfikator błędu:** BC33000  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Wybierz operator z zestawu operatory z możliwością przeciążenia.  
  
2.  Jeśli potrzebujesz funkcji przeciążenia operatora, który nie możesz przeciążyć bezpośrednio utworzyć `Function` procedury, która przyjmuje odpowiednie parametry i zwraca odpowiednią wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Instrukcje: definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Instrukcje: definiowanie operatora konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
