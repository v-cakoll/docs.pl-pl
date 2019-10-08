---
title: Lista atrybutów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: 771757afe214919649e13fda3990e1154be8e1e1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004526"
---
# <a name="attribute-list-visual-basic"></a>Lista atrybutów (Visual Basic)
Określa atrybuty, które mają zostać zastosowane do zadeklarowanego elementu programowania. Wiele atrybutów jest oddzielonych przecinkami. Poniżej znajduje się składnia jednego atrybutu.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>Części  
|||
|---|---|
|`attributemodifier`|Wymagane dla atrybutów zastosowanych na początku pliku źródłowego. Może to być [zestaw](../../../visual-basic/language-reference/modifiers/assembly.md) lub [moduł](../../../visual-basic/language-reference/modifiers/module-keyword.md).|
|`attributename`| Wymagany. Nazwa atrybutu.|
|`attributearguments`|Opcjonalny. Lista argumentów pozycyjnych dla tego atrybutu. Wiele argumentów jest oddzielonych przecinkami.|
|`attributeinitializer`|Opcjonalny. Lista inicjatorów zmiennych lub właściwości dla tego atrybutu. Wiele inicjatorów jest oddzielonych przecinkami.|
  
## <a name="remarks"></a>Uwagi  
 Można zastosować jeden lub więcej atrybutów do niemal każdego elementu programistycznego (typy, procedury, właściwości i tak dalej). Atrybuty są wyświetlane w metadanych zestawu i mogą ułatwić Dodawanie adnotacji do kodu lub określić sposób użycia określonego elementu programistycznego. Można stosować atrybuty zdefiniowane przez Visual Basic i .NET Framework, a także definiować własne atrybuty.  

 Aby uzyskać więcej informacji na temat sytuacji, w których należy używać atrybutów, zobacz [Omówienie atrybutów](../../../visual-basic/programming-guide/concepts/attributes/index.md). Aby uzyskać informacje na temat nazw atrybutów, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Przepisy  
  
- **Jęcia.** Atrybuty można stosować do najbardziej zadeklarowanych elementów programistycznych. Aby zastosować jeden lub więcej atrybutów, należy umieścić *blok atrybutu* na początku deklaracji elementu. Każdy wpis na liście atrybutów określa atrybut, który ma zostać zastosowany, oraz modyfikator i argumenty, które są używane dla tego wywołania atrybutu.  
  
- **Nawiasy ostre.** W przypadku podania listy atrybutów należy ująć ją w nawiasy ostre ("`<`" i "`>`").  
  
- **Część deklaracji.** Atrybut musi być częścią deklaracji elementu, a nie oddzielną instrukcją. Można użyć sekwencji kontynuacji wiersza ("`_`"), aby przedłużyć instrukcję deklaracji na wiele wierszy kodu źródłowego.  
  
- **Modyfikatory.** Modyfikator atrybutu (`Assembly` lub `Module`) jest wymagany dla każdego atrybutu zastosowanego do elementu programowania na początku pliku źródłowego. Modyfikatory atrybutów są niedozwolone w przypadku atrybutów zastosowanych do elementów, które nie znajdują się na początku pliku źródłowego.  
  
- **Argumentu.** Wszystkie argumenty pozycyjne dla atrybutu muszą poprzedzać wszelkie inicjatory zmiennych lub właściwości.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano atrybut <xref:System.Runtime.InteropServices.DllImportAttribute> do definicji szkieletowej procedury `Function`.  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> wskazuje, że procedura Attribute reprezentuje punkt wejścia w niezarządzanej bibliotece dołączanej dynamicznie (DLL). Atrybut dostarcza nazwę biblioteki DLL jako argument pozycyjny oraz inne informacje jako inicjatory zmiennych.  
  
## <a name="see-also"></a>Zobacz także

- [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)
- [Moduł @no__t — 1keyword >](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [Przegląd atrybutów](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Instrukcje: przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
