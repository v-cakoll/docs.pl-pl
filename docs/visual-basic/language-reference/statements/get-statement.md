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
ms.openlocfilehash: 31936fb2c8f658203a43702a2b5fa4ee2481beb5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404605"
---
# <a name="get-statement"></a>Get — Instrukcja
Deklaruje `Get` procedurę właściwości używaną do pobrania wartości właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`attributelist`|Opcjonalny. Zobacz [listę atrybutów](attribute-list.md).|  
|`accessmodifier`|Opcjonalne dla co najwyżej jednej `Get` instrukcji i `Set` w tej właściwości. Może być jedną z następujących czynności:<br /><br /> -   [Chronione](../modifiers/protected.md)<br />-   [Osoby](../modifiers/friend.md)<br />-   [Użytek](../modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).|  
|`statements`|Opcjonalny. Jedna lub więcej instrukcji, które są uruchamiane, gdy `Get` wywoływana jest procedura właściwości.|  
|`End Get`|Wymagany. Kończy definicję `Get` procedury właściwości.|  
  
## <a name="remarks"></a>Uwagi  
 Każda właściwość musi mieć `Get` procedurę właściwości, chyba że właściwość jest oznaczona `WriteOnly` . `Get`Procedura służy do zwracania bieżącej wartości właściwości.  
  
 Visual Basic automatycznie wywołuje procedurę właściwości, `Get` gdy wyrażenie żąda wartości właściwości.  
  
 Treść deklaracji właściwości może zawierać tylko właściwości `Get` i `Set` procedury między [instrukcją właściwości](property-statement.md) a `End Property` instrukcją. Nie może on przechowywać żadnych elementów innych niż te procedury. W szczególności nie można zapisać bieżącej wartości właściwości. Ta wartość musi być przechowywana poza właściwością, ponieważ w przypadku przechowywania jej w ramach jednej z procedur dotyczących właściwości inna procedura właściwości nie będzie mogła uzyskać do niej dostępu. Typowym podejściem jest przechowywanie wartości w zmiennej [prywatnej](../modifiers/private.md) zadeklarowanej na tym samym poziomie co właściwość. Należy zdefiniować `Get` procedurę wewnątrz właściwości, do której ma zastosowanie.  
  
 `Get`Procedura jest domyślnie ustawiona na poziom dostępu właściwości zawierającej, chyba że zostanie użyta `accessmodifier` `Get` instrukcja w instrukcji.  
  
## <a name="rules"></a>Reguły  
  
- **Mieszane poziomy dostępu.** W przypadku definiowania właściwości do odczytu i zapisu można opcjonalnie określić inny poziom dostępu dla `Get` lub `Set` procedury, ale nie oba. W takim przypadku poziom dostępu do procedury musi być bardziej restrykcyjny niż poziom dostępu do właściwości. Na przykład, jeśli właściwość jest zadeklarowana `Friend` , można zadeklarować `Get` procedurę `Private` , ale nie `Public` .  
  
     W przypadku definiowania `ReadOnly` właściwości `Get` procedura reprezentuje całą właściwość. Nie można zadeklarować innego poziomu dostępu dla `Get` , ponieważ spowodowałoby to ustawienie dwóch poziomów dostępu dla właściwości.  
  
- **Typ zwracany.** [Instrukcja Property](property-statement.md) może deklarować typ danych zwracanej wartości. `Get`Procedura automatycznie zwraca ten typ danych. Można określić dowolny typ danych lub nazwę wyliczenia, struktury, klasy lub interfejsu.  
  
     Jeśli instrukcja nie zostanie `Property` określona `returntype` , procedura zwraca wartość `Object` .  
  
## <a name="behavior"></a>Zachowanie  
  
- **Powrót z procedury.** Gdy `Get` procedura zwraca kod wywołujący, wykonywanie jest kontynuowane w instrukcji, która zażądała wartości właściwości.  
  
     `Get`procedury właściwości mogą zwracać wartość przy użyciu [instrukcji return](return-statement.md) lub przez przypisanie wartości zwracanej do nazwy właściwości. Aby uzyskać więcej informacji, zobacz "wartość zwracana" w [instrukcji funkcji](function-statement.md).  
  
     `Exit Property`Instrukcje i `Return` powodują natychmiastowe wyjście z procedury właściwości. Dowolna liczba `Exit Property` `Return` instrukcji i może występować w dowolnym miejscu procedury i można mieszać i wypełniać `Exit Property` `Return` instrukcje.  
  
- **Wartość zwracana.** Aby zwrócić wartość z `Get` procedury, można przypisać wartość do nazwy właściwości lub dołączyć ją do [instrukcji return](return-statement.md). `Return`Instrukcja równocześnie przypisuje `Get` wartość zwracaną przez procedurę i kończy procedurę.  
  
     Jeśli używasz `Exit Property` bez przypisywania wartości do nazwy właściwości, `Get` procedura zwraca wartość domyślną dla typu danych właściwości. Aby uzyskać więcej informacji, zobacz "wartość zwracana" w [instrukcji funkcji](function-statement.md).  
  
     Poniższy przykład ilustruje dwa sposoby, gdy właściwość tylko do odczytu `quoteForTheDay` może zwracać wartość przechowywaną w zmiennej prywatnej `quoteValue` .  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji, `Get` Aby zwrócić wartość właściwości.  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>Zobacz też

- [Set — Instrukcja](set-statement.md)
- [Property — Instrukcja](property-statement.md)
- [Exit, instrukcja](exit-statement.md)
- [Obiekty i klasy](../../programming-guide/language-features/objects-and-classes/index.md)
- [Wskazówki: definiowanie klas](../../programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
