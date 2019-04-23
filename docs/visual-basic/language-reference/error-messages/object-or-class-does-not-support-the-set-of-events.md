---
title: Obiekt lub klasa nie obsługuje zbioru zdarzeń
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: ad9176b5332a75f03968e742501c3fce541055de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342885"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>Obiekt lub klasa nie obsługuje zbioru zdarzeń
Próbowano użyć `WithEvents` zmiennej za pomocą składnika, który nie może działać jako źródło zdarzeń dla określonego zestawu zdarzeń. Na przykład chcesz przechwytywać zdarzenia obiektu, a następnie utworzyć inny obiekt, który `Implements` pierwszy obiekt. Mimo że myślisz, że można przechwytywać zdarzenia z zaimplementowaną obiektu, nie zawsze jest to wymagane. `Implements` tylko implementuje interfejs dla metod i właściwości. `WithEvents` nie jest obsługiwana dla prywatnych `UserControls`, ponieważ wymagane informacje dotyczące typu podnieść `ObjectEvent` nie jest dostępna w czasie wykonywania.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Nie można wychwytywanie zdarzeń interfejsu składnika, który nie źródeł zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
- [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md)
