---
title: 'Deklaracja operatora musi mieć jeden z: +,-, *,-, -, ^, &amp;, Like, Mod i, Or, Xor, nie <<>>,, = <>, <, < =, >, > =, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: dac8613d79e3262e4d1fd6ad1599fd01182e329b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819375"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a>Deklaracja operatora musi mieć jeden z: +,-, *,\,/, ^, &amp;, Like, Mod i, Or, Xor, nie \< \<, >>...
Można zadeklarować tylko kwalifikuje się do przeciążania operatora. W poniższej tabeli wymieniono operatory, których można zadeklarować.  
  
|Typ|Operatory|  
|----------|---------------|  
|Jednoargumentowy|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|plików binarnych|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Konwersja (jednoargumentowy)|`CType`|  
  
 Należy pamiętać, że `=` operator binarny listy jest operator porównania nie operator przypisania.  
  
 **Identyfikator błędu:** BC33000  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Wybierz operatora z zestawu operatory z możliwością przeciążenia.  
  
2.  Przeciążanie operatora, który nie może zostać bezpośrednio przeciążenia funkcji, należy utworzyć `Function` procedury, która przyjmuje odpowiednie parametry i zwraca odpowiednią wartość.  
  
## <a name="see-also"></a>Zobacz także

- [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Instrukcje: Definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Instrukcje: Definiowanie operatora konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
