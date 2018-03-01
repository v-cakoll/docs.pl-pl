---
title: "With...End With — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.With
helpviewer_keywords:
- With keyword [Visual Basic]
- loop structures [Visual Basic], and With...End With statements
- execution [Visual Basic], on object
- instructions, repeating
- With...End With statements [Visual Basic]
- With statement [Visual Basic]
- With statement [Visual Basic], nesting
- objects [Visual Basic], accessing
- With block
- End keyword [Visual Basic], With...End With statements
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aa1f416e1bfdf6cdb51b098c0e2bd5e9912cb309
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="withend-with-statement-visual-basic"></a>With...End With — Instrukcja (Visual Basic)
Wykonuje szereg instrukcji, które wielokrotnie odwołują się do pojedynczego obiektu lub struktury, dzięki czemu instrukcje mogą używać uproszczonej składni podczas uzyskiwania dostępu do członków obiektu lub struktury.  Podczas używania struktury można odczytać wartości elementów członkowskich lub tylko wywołania metod i występuje błąd, Jeśli spróbujesz przypisać wartości do elementów członkowskich struktury używane w `With...End With` instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
With objectExpression  
    [ statements ]  
End With  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`objectExpression`|Wymagany. Wyrażenie, które zostaje oszacowane do obiektu. Wyrażenie może być dowolnie złożone i jest sprawdzane tylko raz. Wyrażenie może być dowolnego typu danych, w tym typów podstawowych.|  
|`statements`|Opcjonalny. Co najmniej jeden instrukcji między `With` i `End With` może odwołujące się do elementów członkowskich obiektu, który jest generowany przez ocenę `objectExpression`.|  
|`End With`|Wymagany. Kończy definicję `With` bloku.|  
  
## <a name="remarks"></a>Uwagi  
 Przy użyciu `With...End With`, można wykonać serię instrukcji na określony obiekt bez określania nazwy obiektu wiele razy. W ramach `With` blok instrukcji, można określić elementu członkowskiego obiektu, rozpoczynając od okresu, tak jakby `With` obiektu instrukcji poprzedzające go.  
  
 Na przykład, aby zmienić wiele właściwości w jednym obiekcie, umieść instrukcje przypisania właściwości wewnątrz `With...End With` bloku, odwołanie do obiektu tylko raz zamiast raz dla każdego przydziału właściwości.  
  
 Jeśli kod uzyskuje dostęp do tego samego obiektu wiele instrukcji, za pomocą zyskać następujące korzyści `With` instrukcji:  
  
-   Nie musisz szacować złożonego wyrażenia wiele razy ani przypisywać wyniku do zmiennej tymczasowej, aby odwołać się do jego członków wiele razy.  
  
-   Kod staje się bardziej czytelny dzięki eliminacji powtarzających się wyrażeń kwalifikujących.  
  
 Typ danych miary `objectExpression` może być dowolną klasę lub typ struktury lub nawet typu podstawowe języka Visual Basic takich jak `Integer`.  Jeśli `objectExpression` wyniki w innym niż obiekt można odczytać wartości jego elementów członkowskich lub tylko wywołania metod i występuje błąd, Jeśli spróbujesz przypisać wartości do elementów członkowskich struktury używane w `With...End With` instrukcji.  Jest to ten sam błąd, jeśli należy wywołać metodę zwrócił strukturę i od razu dostępne i przypisywać wartości do elementu członkowskiego wyniku funkcji, takich jak `GetAPoint().x = 1`.  Problem w obu przypadkach jest taki, że struktura istnieje tylko na stosie wywołań i nie ma żadnego sposobu, aby członek zmodyfikowanej struktury w takich sytuacjach mógł pisać do takich lokalizacji, żeby inny kod w programie mógł obserwować zmiany.  
  
 `objectExpression` Jest oceniane, po wejściu do bloku. Nie można przepisać `objectExpression` z poziomu `With` bloku.  
  
 W ramach `With` bloku, użytkownik ma dostęp do metod i właściwości określonego obiektu bez kwalifikujących się je. Możesz użyć metod i właściwości innych obiektów, ale musisz je zakwalifikować z ich nazwami obiektów.  
  
 Możesz umieścić jedną `With...End With` instrukcji w innym. Zagnieżdżone `With...End With` instrukcji może być mylące, jeśli obiekty, które są określone nie jest jasne z kontekstu. Należy podać pełną odwołanie do obiektu, który znajduje się w zewnętrznym `With` zablokować, jeśli obiekt jest wywoływany przez w wewnętrzny `With` bloku.  
  
 Nie można rozgałęzić do `With` blok instrukcji z poza blokiem.  
  
 Instrukcje są wykonywane tylko raz, chyba że blok zawiera pętlę. Możesz zagnieździć różne rodzaje struktur sterujących. Aby uzyskać więcej informacji, zobacz [zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
>  Można użyć `With` — słowo kluczowe w obiekt również inicjatory. Aby uzyskać dodatkowe informacje i przykłady, zobacz [inicjatory obiektów: typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) i [typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
>   
>  Jeśli używasz `With` bloku tylko zainicjować właściwości lub pola obiektu, który właśnie został uruchomiony, rozważ użycie zamiast tego inicjatora obiektu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie każdy `With` bloku uruchamia serię instrukcji na pojedynczy obiekt.  
  
 [!code-vb[VbVbalrWithStatement#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/with-end-with-statement_1.vb)]  
  
## <a name="example"></a>Przykład  
 Następujące zagnieżdża przykład `With…End With` instrukcje. W ramach zagnieżdżone `With` , składnia odwołuje się do obiektu wewnętrznego.  
  
 [!code-vb[VbVbalrWithStatement#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/with-end-with-statement_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic.List%601>  
 [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Inicjatory obiektów: Typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
