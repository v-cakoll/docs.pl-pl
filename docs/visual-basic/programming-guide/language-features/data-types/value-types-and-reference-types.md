---
title: "Typy wartości i odwołań"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2b54945d27d186771e8b5353e753afd74c56d71b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="value-types-and-reference-types"></a>Typy wartości i odwołań
W języku Visual Basic typy danych są wdrażane na podstawie ich klasyfikacji. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Typy danych mogą być klasyfikowane w zależności od tego, czy zmienna określonego typu przechowuje własnych danych lub wskaźnikiem do danych. Jeśli przechowuje własnych danych jest *typu wartości*; jeśli posiada wskaźnik do danych w pamięci jest *zawierają odwołania do typu*.  
  
## <a name="value-types"></a>Typy wartości  
 Typ danych jest *typu wartości* Jeśli przechowuje dane w obrębie własnej alokacji pamięci. Typy wartości są następujące:  
  
-   Wszystkie typy danych numerycznych  
  
-   `Boolean`, `Char`, i`Date`  
  
-   Wszystkie struktury, nawet jeśli ich elementy członkowskie są typy odwołań  
  
-   Wyliczenia, ponieważ jego typ podstawowy jest zawsze `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, lub`ULong`  
  
 Co struktura jest typem wartości, nawet wtedy, gdy zawiera on elementy członkowskie typu odwołania. Z tego powodu wartość typy takich jak `Char` i `Integer` są implementowane przez struktury .NET Framework.  
  
 Można zadeklarować typu wartości za pomocą zastrzeżonym słowem kluczowym, na przykład `Decimal`. Można również użyć `New` — słowo kluczowe można zainicjować typu wartości. Jest to szczególnie przydatne, jeśli typ ma konstruktora, który przyjmuje parametry. Na przykład jest <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> konstruktora, który tworzy nową `Decimal` wartości z części dostarczony.  
  
## <a name="reference-types"></a>Typy odwołań  
 A *zawierają odwołania do typu* zawiera wskaźnik do innej lokalizacji pamięci, która przechowuje dane. Typy odwołań są następujące:  
  
-   `String`  
  
-   Wszystkie tablice, nawet jeśli ich elementy są typy wartości  
  
-   Typy klas, takich jak<xref:System.Windows.Forms.Form>  
  
-   Delegaty  
  
 Klasa jest *zawierają odwołania do typu*. Z tego powodu typy referencyjne takich jak `Object` i `String` są obsługiwane przez [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] klasy. Należy pamiętać, że każdy tablicy typu odwołania, nawet jeśli jego elementów członkowskich typów wartości.  
  
 Ponieważ każdy typ referencyjny reprezentuje klasy .NET Framework, należy użyć [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md) — słowo kluczowe podczas jego inicjowania. Poniższa instrukcja inicjuje tablicy.  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>Elementy, które nie są typami  
 Następujące elementy programowania nie kwalifikuje się jako typów, ponieważ nie można określić ich jako typ danych zadeklarowany element:  
  
-   Namespaces  
  
-   Moduły  
  
-   Zdarzenia  
  
-   Właściwości i procedury  
  
-   Pola, stałe i zmienne  
  
## <a name="working-with-the-object-data-type"></a>Praca z typem danych obiektu  
 Można przypisać typu odwołania lub typu wartości do zmiennej `Object` typu danych. `Object` Zmienna zawsze przechowuje wskaźnikiem do danych, a nie dane. Jednak jeśli przypisać do typu wartość `Object` zmiennej, działa tak, jakby posiada własnych danych. Aby uzyskać więcej informacji, zobacz [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Można sprawdzić, czy `Object` zmiennej działa jako typu odwołania lub typu wartościowego, przekazując go do <xref:Microsoft.VisualBasic.Information.IsReference%2A> metody w <xref:Microsoft.VisualBasic.Information> klasy <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw. <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType>Zwraca `True` Jeśli zawartość `Object` zmienna reprezentuje typ referencyjny.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy dopuszczające wartości zerowe wartości](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Structure — instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Skuteczne stosowanie typów danych](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
