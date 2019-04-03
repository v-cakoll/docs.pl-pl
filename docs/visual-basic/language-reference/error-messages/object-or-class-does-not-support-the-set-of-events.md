---
title: Obiekt lub klasa nie obsługuje zbioru zdarzeń
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: 2e00bdd624b54e19f19b6dabf6681bbf89709e60
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822586"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>Obiekt lub klasa nie obsługuje zbioru zdarzeń
Próbowano użyć `WithEvents` zmiennej za pomocą składnika, który nie może działać jako źródło zdarzeń dla określonego zestawu zdarzeń. Na przykład chcesz przechwytywać zdarzenia obiektu, a następnie utworzyć inny obiekt, który `Implements` pierwszy obiekt. Mimo że myślisz, że można przechwytywać zdarzenia z zaimplementowaną obiektu, nie zawsze jest to wymagane. `Implements` tylko implementuje interfejs dla metod i właściwości. `WithEvents` nie jest obsługiwana dla prywatnych `UserControls`, ponieważ wymagane informacje dotyczące typu podnieść `ObjectEvent` nie jest dostępna w czasie wykonywania.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Nie można wychwytywanie zdarzeń interfejsu składnika, który nie źródeł zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
- [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md)
