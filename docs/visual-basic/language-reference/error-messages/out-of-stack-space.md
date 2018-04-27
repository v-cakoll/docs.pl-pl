---
title: Za mało miejsca na stosie (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ec839d1f0ad1931ed4229e898a900c3210d813ed
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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
