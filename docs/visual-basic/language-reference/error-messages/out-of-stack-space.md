---
title: Za mało miejsca na stosie (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: e39be5913fe877cf7b3396e4f13f4440288cb8f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593288"
---
# <a name="out-of-stack-space-visual-basic"></a>Za mało miejsca na stosie (Visual Basic)
Stos jest obszar roboczy pamięci, który powiększa się i zmniejsza dynamicznie z wymaganiami wykonywania programu. Przekroczono limit.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź, czy procedury nie są zagnieżdżone zbyt głęboko.  
  
2.  Upewnij się, że procedury rekurencyjne kończą się poprawnie.  
  
3.  Jeśli zmienne lokalne wymagają lokalnej zmiennej miejsca niż jest dostępne, spróbuj deklarowanie niektóre zmienne na poziomie modułu. Można również zadeklarować wszystkie zmienne w procedurze statycznych poprzedzając `Property`, `Sub`, lub `Function` — słowo kluczowe z `Static`. Możesz też użyć `Static` instrukcji, aby zadeklarować poszczególnych zmiennych statycznych w ramach procedur.  
  
4.  Niektóre z ciągi o stałej długości jako ciągi o zmiennej długości przedefiniować jako ciągi o stałej długości Użyj więcej miejsca na stosie niż ciągi o zmiennej długości. Można również zdefiniować ciąg na poziomie modułu, których wymaga miejsca na stosie.  
  
5.  Sprawdź liczbę zagnieżdżonych `DoEvents` funkcji wywołań, za pomocą `Calls` okno dialogowe do widoku, które procedury są aktywne na stosie.  
  
6.  Upewnij się, że nie spowodowało "cascade zdarzeń" wyzwalając zdarzenie, które wywołuje procedurę zdarzenia już na stosie. Cascade zdarzeń jest podobny do niezakończony procedur rekursja, ale jest mniej oczywista, ponieważ połączenie jest nawiązywane przez zamiast jawnego wywołania w kodzie języka Visual Basic. Użyj `Calls` okno dialogowe do widoku, które procedury są aktywne na stosie.  
  
## <a name="see-also"></a>Zobacz też  
 [Okno pamięci](/visualstudio/debugger/memory-windows)
