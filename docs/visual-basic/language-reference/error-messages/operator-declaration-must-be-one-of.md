---
title: "Deklaracja operatora musi mieć jeden z: +,-, *,-, -, ^, &amp;, Like, Mod i, Or, Xor, nie &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;=, &gt; , &gt;=, CType, IsTrue, IsFalse"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 80c8358dd13105c18e73e94735a51b02d5bd22c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Operator — instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Porady: Definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Porady: Definiowanie operatora konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
