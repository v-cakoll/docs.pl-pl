---
title: Modyfikator „Custom” jest nieprawidłowy w zdarzeniach deklarowanych bez jawnych typów delegowanych
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 0c5a4188fedf9685afdd1cde4c1de93a0b43b919
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409789"
---
# <a name="custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>Modyfikator „Custom” jest nieprawidłowy w zdarzeniach deklarowanych bez jawnych typów delegowanych
W przeciwieństwie do zdarzenia nieniestandardowego, `Custom Event` Deklaracja wymaga `As` klauzuli następującej po nazwie zdarzenia, która jawnie określa typ delegata dla zdarzenia.  
  
 Zdarzenia nieniestandardowe można definiować z `As` klauzulą i jawnym typem delegata lub z listą parametrów bezpośrednio po nazwie zdarzenia.  
  
 **Identyfikator błędu:** BC31122  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Zdefiniuj delegata z tą samą listą parametrów co zdarzenie niestandardowe.  
  
     Na przykład, jeśli `Custom Event` zostało zdefiniowane przez `Custom Event Test(ByVal sender As Object, ByVal i As Integer)` , odpowiadający mu delegat byłby następujący.  
  
     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]  
  
2. Zastąp listę parametrów zdarzenia niestandardowego `As` klauzulą określającą typ delegata.  
  
     Kontynuując z przykładem, `Custom Event` Deklaracja zostanie zmieniona w następujący sposób.  
  
     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]  
  
## <a name="example"></a>Przykład  
 Ten przykład deklaruje `Custom Event` i określa `As` klauzulę wymaganą z typem delegata.  
  
 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- [Event — Instrukcja](../statements/event-statement.md)
- [Delegate — Instrukcja](../statements/delegate-statement.md)
- [Zdarzenia](../../programming-guide/language-features/events/index.md)
