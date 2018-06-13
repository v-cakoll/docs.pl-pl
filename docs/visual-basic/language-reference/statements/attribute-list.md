---
title: Lista atrybutów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: 35d031722a5eddd6adce5e32df62b86c500d305b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604077"
---
# <a name="attribute-list-visual-basic"></a>Lista atrybutów (Visual Basic)
Określa atrybuty, które ma zostać zastosowany do zadeklarowany element. Wiele atrybutów są rozdzielane przecinkami. Poniżej przedstawiono składnię jeden atrybut.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>Części  
 `attributemodifier`  
 Wymagany dla atrybutów zastosowanych na początku pliku źródłowego. Może być [zestawu](../../../visual-basic/language-reference/modifiers/assembly.md) lub [modułu](../../../visual-basic/language-reference/modifiers/module-keyword.md).  
  
 `attributename`  
 Wymagana. Nazwa atrybutu.  
  
 `attributearguments`  
 Opcjonalna. Lista argumentów pozycyjnych dla tego atrybutu. Używanie wielu argumentów są oddzielone przecinkami.  
  
 `attributeinitializer`  
 Opcjonalna. Listy inicjatorów zmienna lub właściwość dla tego atrybutu. Wiele inicjatory są oddzielone przecinkami.  
  
## <a name="remarks"></a>Uwagi  
 Co najmniej jeden atrybut można stosować do niemal dowolnego elementu programistycznego (typy, procedur, właściwości i tak dalej). Atrybuty są wyświetlane w metadanych zestawu i mogą pomóc adnotacji kodu lub określić sposób użycia konkretnego elementu programistycznego. Można zastosować atrybutów zdefiniowanych przez Visual Basic i .NET Framework, a można definiować własne atrybuty.  

 Aby uzyskać więcej informacji o tym, kiedy należy używać atrybutów, zobacz [Omówienie atrybutów](../../../visual-basic/programming-guide/concepts/attributes/index.md). Aby uzyskać informacje o nazwach atrybutów, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Reguły  
  
-   **Umieszczanie.** Atrybuty można zastosować do najbardziej zadeklarowanych elementów programistycznych. Aby zastosować jeden lub więcej atrybutów, umieść *bloku attribute* na początku deklaracji elementu. Każdy wpis na liście atrybutów Określa atrybut, który chcesz zastosować i modyfikator i argumenty używanego dla tego wywołania atrybutu.  
  
-   **Nawiasy.** Jeśli podasz lista atrybutów, należy ująć go w nawiasy ("`<`"i"`>`").  
  
-   **Część deklaracji.** Atrybut musi być w deklaracji elementu oddzielną instrukcję. Można użyć sekwencji kontynuacji wiersza (" `_`") do rozszerzenia instrukcji deklaracji na wiele wierszy kodu źródłowego.  
  
-   **Modyfikatory.** Modyfikator atrybutu (`Assembly` lub `Module`) jest wymagany na każdy atrybut zastosowany do elementu programistycznego na początku pliku źródłowego. Atrybut modyfikatorów nie są dozwolone na atrybuty stosowane do elementów, które nie są na początku pliku źródłowego.  
  
-   **Argumenty.** Wszystkie argumenty pozycyjne atrybutu musi poprzedzać wszystkie inicjatory zmienna lub właściwość.  
  
## <a name="example"></a>Przykład  
 Następujący przykład dotyczy <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu szkielet definicji `Function` procedury.  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> Wskazuje, że procedura oparte na atrybutach reprezentuje punkt wejścia w niezarządzanych biblioteki dołączanej (dynamicznie DLL). Ten atrybut zawiera nazwy biblioteki DLL jako argument pozycyjny oraz inne informacje jako inicjatory zmiennej.  
  
## <a name="see-also"></a>Zobacz też  
 [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)  
 [Moduł \<— słowo kluczowe >](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [Atrybuty — omówienie](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [Instrukcje: przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
