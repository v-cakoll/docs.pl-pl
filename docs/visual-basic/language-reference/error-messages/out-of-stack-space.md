---
title: Za mało miejsca na stosie (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 29dbdf74808fc98bb856483c3fd8e3a09a72113b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925583"
---
# <a name="out-of-stack-space-visual-basic"></a>Za mało miejsca na stosie (Visual Basic)
Stos jest pracy obszaru pamięci, która zwiększania lub zmniejszania dynamicznie z zapotrzebowaniem na zasoby wykonywania programu. Przekroczono limit.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Sprawdź, czy procedury nie są zagnieżdżone zbyt głęboko.  
  
2. Upewnij się, że procedury rekurencyjne kończą się poprawnie.  
  
3. Jeśli zmienne lokalne wymagają lokalnej zmiennej miejsca niż dostępna, spróbuj deklarowanie niektóre zmienne na poziomie modułu. Można również zadeklarować wszystkie zmienne w procedurze statyczne poprzedzając `Property`, `Sub`, lub `Function` — słowo kluczowe z `Static`. Możesz też `Static` instrukcję, aby zadeklarować poszczególnych zmiennych statycznych w ramach procedur.  
  
4. Niektóre z Twoimi ciągami o stałej długości, jako ciągi o zmiennej długości przedefiniować jako ciągi o stałej długości Użyj więcej miejsca na stosie niż ciągi o zmiennej długości. Można również zdefiniować ciąg na poziomie modułu wymagającym nie obszar stosu.  
  
5. Sprawdź liczbę zagnieżdżonych `DoEvents` funkcję wywołania, przy użyciu `Calls` okno dialogowe do widoku, które procedury są aktywne na stosie.  
  
6. Upewnij się, że nie był przyczyną "cascade zdarzeń", wyzwalając zdarzenie, które wywołuje procedury zdarzenia już na stosie. Kaskadowe zdarzeń jest podobny do niezakończony cykliczne wywołanie procedury, ale jest mniej oczywistych, ponieważ jest nawiązywane połączenie, zamiast jawnego wywołania w kodzie języka Visual Basic. Użyj `Calls` okno dialogowe do widoku, które procedury są aktywne na stosie.  
  
## <a name="see-also"></a>Zobacz także

- [Okna pamięci](/visualstudio/debugger/memory-windows)
