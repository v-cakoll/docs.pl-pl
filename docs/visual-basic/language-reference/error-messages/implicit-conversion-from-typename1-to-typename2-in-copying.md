---
title: Niejawna konwersja z &#39; &lt;typename1&gt; &#39; do &#39; &lt;typename2&gt; &#39; podczas kopiowania wartości &#39;ByRef&#39; parametru &#39; &lt; Nazwa parametru&gt; &#39; powrotem do pasującego argumentu.
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: 9f05a5fbcbef828b4ffa920d8cade475cedb64d5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537246"
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a>Niejawna konwersja z &#39; &lt;typename1&gt; &#39; do &#39; &lt;typename2&gt; &#39; podczas kopiowania wartości &#39;ByRef&#39; parametru &#39; &lt; Nazwa parametru&gt; &#39; powrotem do pasującego argumentu.
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
