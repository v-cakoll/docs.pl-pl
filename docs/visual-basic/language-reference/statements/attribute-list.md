---
title: Lista atrybutów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: 35d031722a5eddd6adce5e32df62b86c500d305b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604077"
---
# <a name="attribute-list-visual-basic"></a>Lista atrybutów (Visual Basic)
Określa atrybuty, które mają zostać zastosowane do zadeklarowanego elementu programowania. Wiele atrybutów rozdziela się przecinkami. Poniżej przedstawiono składnię z jednym atrybutem.  
  
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
 Atrybuty (jeden lub więcej) można zastosować do niemal dowolnego elementu programistycznego (typu, procedury, właściwości itd.). Atrybuty są wyświetlane w metadanych zestawu i mogą pomóc w opisaniu kodu lub określeniu sposobu użycia konkretnego elementu programistycznego. Zastosować można atrybuty zdefiniowane przez Visual Basic i .NET Framework. Zdefiniować można także własne atrybuty.  

 Aby uzyskać więcej informacji o stosowaniu atrybutów, zobacz artykuł [Omówienie atrybutów](../../../visual-basic/programming-guide/concepts/attributes/index.md). Aby uzyskać informacje o nazwach atrybutów, zobacz artykuł [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Reguły  
  
-   **Umieszczanie.** Atrybuty można zastosować do większości zadeklarowanych elementów programistycznych. Aby zastosować jeden lub więcej atrybutów, umieść *blok atrybutu* na początku deklaracji elementu. Każdy wpis na liście atrybutów określa atrybut, który chcesz zastosować, oraz modyfikator i argumenty używane dla tego wywołania atrybutu.  
  
-   **Nawiasy.** Podając listę atrybutów, musisz ująć ją w nawiasy (`<` i `>`).  
  
-   **Część deklaracji.** Atrybut musi być częścią deklaracji elementu, a nie oddzielną instrukcją. Można użyć sekwencji kontynuacji wiersza (`_`) do rozszerzenia instrukcji deklaracji na wiele wierszy kodu źródłowego.  
  
-   **Modyfikatory.** Modyfikator atrybutu (`Assembly` lub `Module`) jest wymagany dla każdego atrybutu zastosowanego do elementu programistycznego na początku pliku źródłowego. Modyfikatory atrybutu nie są dozwolone w przypadku atrybutów stosowanych do elementów, które nie znajdują się na początku pliku źródłowego.  
  
-   **Argumenty.** Wszystkie argumenty pozycyjne atrybutu muszą poprzedzać wszystkie inicjatory zmiennej lub właściwości.  
  
## <a name="example"></a>Przykład  
 W przykładzie poniżej atrybut <xref:System.Runtime.InteropServices.DllImportAttribute> został zastosowany dla definicji szkieletu procedury `Function`.  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> wskazuje, że procedura z atrybutami reprezentuje punkt wejścia w niezarządzanej bibliotece dołączanej dynamicznie (DLL). Atrybut zawiera nazwę biblioteki DLL jako argument pozycyjny oraz inne informacje jako inicjatory zmiennych.  
  
## <a name="see-also"></a>Zobacz też  
 [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)  
 [Module \<słowo kluczowe>](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [Atrybuty — omówienie](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [Instrukcje: przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
