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
Określa atrybuty, które mają zostać zastosowane do zadeklarowanego elementu. Wiele atrybutów rozdziela się przecinkami. Poniżej przedstawiono składnię z jednym atrybutem.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>Części  
|||
|---|---|
|`attributemodifier`|Wymagane dla atrybutów zastosowanych na początku pliku źródłowego. Może to być [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) lub [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md).|
|`attributename`|Wymagane. Nazwa atrybutu.|
|`attributearguments`|Opcjonalne. Lista argumentów pozycyjnych dla tego atrybutu. Wiele argumentów oddzielamy przecinkami.|
|`attributeinitializer`|Opcjonalne. Lista zmiennych lub inicjatorów właściwości dla tego atrybutu. Wiele inicjatorów oddzielamy przecinkami.|
|||
  
## <a name="remarks"></a>Uwagi  
 Można zastosować jeden lub więcej atrybutów do niemal dowolnego elementu programistycznego (typów, procedur, właściwości i tak dalej). Atrybuty są wyświetlane w metadanych zestawu i mogą pomóc w adnotacji kodu lub określeniu sposobu użycia konkretnego elementu programistycznego. Można zastosować atrybuty zdefiniowane przez Visual Basic i .NET Framework, oraz można definiować własne atrybuty.  

 Aby uzyskać więcej informacji o tym, kiedy należy używać atrybutów, zobacz [Omówienie atrybutów](../../../visual-basic/programming-guide/concepts/attributes/index.md). Aby uzyskać informacje o nazwach atrybutów, zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Reguły  
  
-   **Umieszczanie.** Atrybuty można zastosować do najbardziej zadeklarowanych elementów programistycznych. Aby zastosować jeden lub więcej atrybutów, umieść *blok atrybutu* na początku deklaracji elementu. Każdy wpis na liście atrybutów określa atrybut, który chcesz zastosować oraz modyfikator i argumenty używane dla tego wywołania atrybutu.  
  
-   **Nawiasy.** Jeśli podajesz listę atrybutów, musisz ująć ją w nawiasy (`<` i `>`).  
  
-   **Część deklaracji.** Atrybut musi być częścią deklaracji elementu, a nie oddzielną instrukcją. Można użyć kontynuacji sekwencji wiersza (`_`) do rozszerzenia instrukcji deklaracji na wiele wierszy kodu źródłowego.  
  
-   **Modyfikatory.** Modyfikator atrybutu (`Assembly` lub `Module`) jest wymagany dla każdego atrybut zastosowanego do elementu programistycznego na początku pliku źródłowego. Modyfikatory atrybutu nie są dozwolone dla atrybutów stosowanych do elementów, które nie są na początku pliku źródłowego.  
  
-   **Argumenty.** Wszystkie argumenty pozycyjne atrybutu muszą poprzedzać wszystkie inicjatory zmiennej lub właściwości.  
  
## <a name="example"></a>Przykład  
 Następujący przykład stosuje atrybut <xref:System.Runtime.InteropServices.DllImportAttribute> w definicji szkieletu procedury `Function`.  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> wskazuje, że procedura z atrybutami reprezentuje punkt wejścia w niezarządzanej bibliotece dołączanej dynamicznie (DLL). Atrybut ten zawiera nazwę biblioteki DLL jako argument pozycyjny oraz inne informacje jako inicjatory zmiennych.  
  
## <a name="see-also"></a>Zobacz też  
 [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)  
 [Module \<słowo kluczowe>](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [Atrybuty — omówienie](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [Instrukcje: przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
