---
title: Za mało miejsca na stosie
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 9ae604a9727413f2705d42a4b68f5a50b7dd3feb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349183"
---
# <a name="out-of-stack-space-visual-basic"></a>Za mało miejsca na stosie (Visual Basic)
Stos jest obszarem roboczym pamięci, który powiększa się i zmniejsza dynamicznie z wymaganiami wykonywanymi przez program. Przekroczono limity.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Sprawdź, czy procedury nie są zbyt głęboko zagnieżdżone.  
  
2. Upewnij się, że procedury cykliczne kończą się prawidłowo.  
  
3. Jeśli zmienne lokalne wymagają więcej przestrzeni zmiennych lokalnych niż jest dostępna, spróbuj Zadeklaruj pewne zmienne na poziomie modułu. Można również zadeklarować wszystkie zmienne w procedurze statycznej, poprzedzając słowo kluczowe `Property`, `Sub`lub `Function` z `Static`. Można też użyć instrukcji `Static`, aby zadeklarować poszczególne zmienne statyczne w ramach procedur.  
  
4. Przedefiniuj niektóre ciągi o stałej długości jako ciągi o zmiennej długości, ponieważ ciągi o stałej długości używają większej ilości miejsca na stosie niż ciągi o zmiennej długości. Możesz również zdefiniować ciąg na poziomie modułu, gdzie nie wymaga miejsca na stosie.  
  
5. Sprawdź liczbę zagnieżdżonych wywołań funkcji `DoEvents` przy użyciu okna dialogowego `Calls`, aby zobaczyć, które procedury są aktywne na stosie.  
  
6. Upewnij się, że "zdarzenie kaskadowe" nie zostało wywołane przez wyzwolenie zdarzenia, które wywołuje procedurę zdarzenia już na stosie. Zdarzenie kaskadowe jest podobne do niekończącego wywołania procedury cyklicznej, ale jest mniej oczywiste, ponieważ wywołanie jest wykonywane przez Visual Basic, a nie jawne wywołanie w kodzie. Za pomocą okna dialogowego `Calls` można zobaczyć, które procedury są aktywne na stosie.  
  
## <a name="see-also"></a>Zobacz także

- [Okna pamięci](/visualstudio/debugger/memory-windows)
