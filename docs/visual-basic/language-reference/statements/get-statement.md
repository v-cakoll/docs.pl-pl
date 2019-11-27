---
title: Get — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
ms.openlocfilehash: 9560faf90d531c32f104dbd053a7c1f5584cfb1b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351171"
---
# <a name="get-statement"></a>Get — Instrukcja
Deklaruje procedurę właściwości `Get` użytą do pobrania wartości właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`attributelist`|Opcjonalna. Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcjonalne dla co najwyżej jednej instrukcji `Get` i `Set` w tej właściwości. Może to być jeden z następujących modyfikatorów dostępu:<br /><br /> -   [chronione](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [znajomy](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [prywatny](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`statements`|Opcjonalna. Jedna lub więcej instrukcji, które są uruchamiane po wywołaniu procedury `Get` właściwości.|  
|`End Get`|Wymagana. Kończy definicję procedury `Get` właściwości.|  
  
## <a name="remarks"></a>Uwagi  
 Każda właściwość musi mieć procedurę właściwości `Get`, chyba że właściwość jest oznaczona `WriteOnly`. Procedura `Get` służy do zwracania bieżącej wartości właściwości.  
  
 Visual Basic automatycznie wywołuje procedurę `Get` właściwości, gdy wyrażenie żąda wartości właściwości.  
  
 Treść deklaracji właściwości może zawierać tylko `Get` i `Set` procedur między [instrukcją właściwości](../../../visual-basic/language-reference/statements/property-statement.md) i instrukcją `End Property`. Nie może on przechowywać żadnych elementów innych niż te procedury. W szczególności nie można zapisać bieżącej wartości właściwości. Ta wartość musi być przechowywana poza właściwością, ponieważ w przypadku przechowywania jej w ramach jednej z procedur dotyczących właściwości inna procedura właściwości nie będzie mogła uzyskać do niej dostępu. Typowym podejściem jest przechowywanie wartości w zmiennej [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) zadeklarowanej na tym samym poziomie co właściwość. Należy zdefiniować `Get` procedury wewnątrz właściwości, do której ma zastosowanie.  
  
 Procedura `Get` domyślnie jest poziomem dostępu właściwości zawierającego, chyba że w instrukcji `Get` użyto `accessmodifier`.  
  
## <a name="rules"></a>Reguły  
  
- **Mieszane poziomy dostępu.** W przypadku definiowania właściwości do odczytu i zapisu można opcjonalnie określić inny poziom dostępu dla `Get` lub procedury `Set`, ale nie dla obu tych opcji. W takim przypadku poziom dostępu do procedury musi być bardziej restrykcyjny niż poziom dostępu do właściwości. Na przykład, jeśli właściwość jest zadeklarowana `Friend`, można zadeklarować procedurę `Get` `Private`, ale nie `Public`.  
  
     Jeśli definiujesz Właściwość `ReadOnly`, procedura `Get` reprezentuje całą właściwość. Nie można zadeklarować innego poziomu dostępu dla `Get`, ponieważ spowodowałoby to ustawienie dwóch poziomów dostępu dla właściwości.  
  
- **Typ zwracany.** [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md) może deklarować typ danych zwracanej wartości. Procedura `Get` automatycznie zwraca ten typ danych. Można określić dowolny typ danych lub nazwę wyliczenia, struktury, klasy lub interfejsu.  
  
     Jeśli instrukcja `Property` nie określa `returntype`, procedura zwróci `Object`.  
  
## <a name="behavior"></a>Zachowanie  
  
- **Powrót z procedury.** Gdy procedura `Get` zwraca kod wywołujący, wykonywanie jest kontynuowane w instrukcji, która zażądała wartości właściwości.  
  
     procedury właściwości `Get` mogą zwracać wartość przy użyciu [instrukcji return](../../../visual-basic/language-reference/statements/return-statement.md) lub przez przypisanie wartości zwracanej do nazwy właściwości. Aby uzyskać więcej informacji, zobacz "wartość zwracana" w [instrukcji funkcji](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     Instrukcje `Exit Property` i `Return` powodują natychmiastowe wyjście z procedury właściwości. Dowolna liczba instrukcji `Exit Property` i `Return` może występować w dowolnym miejscu procedury i można mieszać instrukcje `Exit Property` i `Return`.  
  
- **Wartość zwracana.** Aby zwrócić wartość z procedury `Get`, można przypisać wartość do nazwy właściwości lub dołączyć ją do [instrukcji return](../../../visual-basic/language-reference/statements/return-statement.md). Instrukcja `Return` równocześnie przypisuje wartość zwrotną procedury `Get` i kończy procedurę.  
  
     Jeśli używasz `Exit Property` bez przypisywania wartości do nazwy właściwości, procedura `Get` zwróci wartość domyślną dla typu danych właściwości. Aby uzyskać więcej informacji, zobacz "wartość zwracana" w [instrukcji funkcji](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     Poniższy przykład ilustruje dwa sposoby, `quoteForTheDay` właściwość tylko do odczytu może zwrócić wartość przechowywaną w zmiennej prywatnej `quoteValue`.  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji `Get`, aby zwrócić wartość właściwości.  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>Zobacz także

- [Set, instrukcja](../../../visual-basic/language-reference/statements/set-statement.md)
- [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)
- [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Przewodnik: definiowanie klas](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
