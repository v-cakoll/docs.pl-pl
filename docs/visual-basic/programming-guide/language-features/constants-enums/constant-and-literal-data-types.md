---
title: Stała i typy literałów (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 58fa1e8c6c659c80cd7998a88d07849ea223750f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="constant-and-literal-data-types-visual-basic"></a>Stała i typy literałów (Visual Basic)
Literał jest wartość, która jest wyrażona jako samej siebie, a nie wartość zmiennej lub wynik wyrażenia, takich jak numer 3 lub ciąg "Hello". Stała jest znaczącą nazwę, która ma miejsce literału i zachowuje tej samej wartości w programie, w przeciwieństwie do zmiennej, którego wartość może zmienić.  
  
 Gdy [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) jest `Off` i [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) jest `On`, musisz jawnie zadeklarować wszystkich stałych o typie danych. W poniższym przykładzie typu danych `MyByte` jawnie jest zadeklarowany jako typ danych `Byte`:  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 Gdy `Option Infer` jest `On` lub `Option Strict` jest `Off`, mogą zadeklarować stałą bez określania typu danych z `As` klauzuli. Kompilator Określa typ stałej z typem wyrażenia. Literał całkowity liczbowych jest rzutowane domyślnie `Integer` — typ danych. Domyślny typ danych liczb zmiennoprzecinkowych jest `Double`i słowa kluczowe `True` i `False` określ `Boolean` stałej.  
  
## <a name="literals-and-type-coercion"></a>Literały i koercja typu  
 W niektórych przypadkach można wymusić literału do określonego typu danych; na przykład podczas przypisywania szczególnie dużej wartości całkowitych wartość literału do zmiennej typu `Decimal`. Poniższy przykład powoduje błąd:  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 Błąd wynika z reprezentację literału. `Decimal` — Typ danych można, przytrzymaj wartość będzie rozmiarze, ale literał niejawnie jest reprezentowany jako `Long`, które nie.  
  
 Można wymusić literału do określonego typu danych na dwa sposoby: przez dodanie do niej znak typu lub umieszczając je w ramach otaczającej znaków. Znak typu lub Załączanie znaków musi bezpośrednio poprzedzać i/lub wykonaj literału, bez interwencji miejsca lub znaków dowolnego rodzaju.  
  
 Aby w poprzednim przykładzie działa, możesz dołączyć `D` wpisz znak literal, co powoduje, że jej może być reprezentowana jako `Decimal`:  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 W poniższym przykładzie pokazano poprawne użycie znaków typu lub otaczającego znaków:  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 Poniższej tabeli otaczającego znaków i znaki typu są dostępne w języku Visual Basic.  
  
|Typ danych|Znak otaczającego|Znak typu dołączany|  
|---|---|---|  
|`Boolean`|(Brak)|(Brak)|  
|`Byte`|(Brak)|(Brak)|  
|`Char`|"|C|  
|`Date`|#|(Brak)|  
|`Decimal`|(Brak)|D lub @|  
|`Double`|(Brak)|R lub #|  
|`Integer`|(Brak)|Lub %|  
|`Long`|(Brak)|L lub &|  
|`Short`|(Brak)|S|  
|`Single`|(Brak)|F lub!|  
|`String`|"|(Brak)|  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe zdefiniowane przez użytkownika](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)  
 [Instrukcje: deklarowanie stałej](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)  
 [Stałe — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Option Explicit, instrukcja](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Wyliczenia — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [Porady: deklarowanie wyliczeń](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)
