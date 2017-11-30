---
title: "Niejawna konwersja z &#39; &lt;typename1&gt;&#39; do &#39;&lt; typename2&gt;&#39; podczas kopiowania wartości &#39; ByRef &#39; Parametr &#39; &lt;parametername&gt;&#39; z powrotem do pasującego argumentu."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords: BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e858b475a816a35d18822643de5a273abe28562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a>Niejawna konwersja z &#39; &lt;typename1&gt;&#39; do &#39;&lt; typename2&gt;&#39; podczas kopiowania wartości &#39; ByRef &#39; Parametr &#39; &lt;parametername&gt;&#39; z powrotem do pasującego argumentu.
Procedura jest wywoływana z [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argumentu typu innego niż jego odpowiadającego mu parametru.  
  
 Jeśli zostanie przekazany argument `ByRef`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] czasami kopiuje wartość argumentu do zmiennej lokalnej w procedurze, a przekazywaniem odwołań do. W takim przypadku po powrocie z procedurą [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] musi skopiować wartości zmiennej lokalnej powrót do argumentu w wywoływanym kodzie.  
  
 Jeśli `ByRef` wartość argumentu jest kopiowany do procedury i argumentów i parametrów są tego samego typu, niezbędne jest brak konwersji. Ale jeśli typy są różne, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] należy przekonwertować w obu kierunkach. Ponieważ nie można użyć `CType` lub wszelkie inne słowa kluczowe konwersji na argumentu procedury lub parametrów, takich konwersji zawsze jest niejawnie.  
  
 Domyślnie ten komunikat jest ostrzeżenie. Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC41999  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli to możliwe, więc użyć wywoływania argumentów tego samego typu jako parametru procedury [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] konieczne wszelkiej konwersji.  
  
-   Jeśli musisz wywołać procedurę z argumentem Typ inny niż typ parametru, ale nie muszą zwracać wartość do wywołującego argumentu, zdefiniuj dany parametr jako [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) zamiast `ByRef`.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Parametry i argumenty procedur](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [Przekazywanie argumentów według wartości i według odwołania](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
