---
title: "Obiekt lub klasa nie obsługuje zbioru zdarzeń"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be4b9140222ef969bfb836fd74f45b8f662360b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>Obiekt lub klasa nie obsługuje zbioru zdarzeń
Próbowano użyć `WithEvents` zmiennej ze składnikiem, który nie może działać jako źródła zdarzeń dla określonego zestawu zdarzeń. Na przykład chcesz przechwytywać zdarzenia obiektu, a następnie utworzyć inny obiekt, który `Implements` pierwszy obiekt. Mimo że może uważasz, że można obiekt sink zdarzenia z zaimplementowanym obiektu, to nie zawsze jest wielkość liter. `Implements`tylko implementuje interfejs dla metody i właściwości. `WithEvents`nie jest obsługiwana w prywatnej `UserControls`, ponieważ informacje o typach wymagane do podnieść `ObjectEvent` nie jest dostępny w czasie wykonywania.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Nie można przechwytywać zdarzenia składnika, który nie źródła zdarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [Implements — instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md)
