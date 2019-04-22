---
title: Niejawna konwersja z „<typename1>” na „<typename2>” podczas kopiowania wartości parametru „ByRef” „<parametername>” z powrotem do pasującego argumentu.
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: 7b02659d96b08c592b25ddf3ef1f99114c3ee269
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58831764"
---
# <a name="implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a>Niejawna konwersja z "\<typename1 >" do "\<typename2 >" podczas kopiowania wartości parametru "ByRef" "\<parametername >" powrotem do pasującego argumentu.
Procedura jest wywoływana z [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argumentu typu innego niż jego odpowiadającego mu parametru.  
  
 W przypadku przekazania argument `ByRef`, Visual Basic czasami kopiuje wartość argumentu do zmiennej lokalnej w procedurze, zamiast przekazywać odwołania. W takim przypadku po powrocie z procedury języka Visual Basic należy skopiować do argumentu w wywoływanym kodzie następnie wartości zmiennej lokalnej.  
  
 Jeśli `ByRef` wartość argumentu jest kopiowana do procedury i parametry i argument są tego samego typu, konwersja nie jest konieczne. Jednak w przypadku różnych typów języka Visual Basic należy przekonwertować w obu kierunkach. Ponieważ nie można użyć `CType` lub dowolne inne słowa kluczowe konwersji argumentu procedury lub parametr, taka konwersja jest zawsze niejawne.  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC41999  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli to możliwe należy użyć wywoływania argumentów tego samego typu jako parametr procedury, Visual Basic nie trzeba wykonać żadnych konwersji.  
  
-   Jeśli musisz wywołać procedurę z nieprawidłowym argumentem typu różni się od typu parametru, ale nie muszą zwracać wartość do wywołującego argumentu, zdefiniuj parametr jako [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) zamiast `ByRef`.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Parametry i argumenty procedur](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Przekazywanie argumentów według wartości i według odwołania](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
