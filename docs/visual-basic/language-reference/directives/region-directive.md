---
title: '#Dyrektywa regionalna (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
ms.openlocfilehash: 204b53751fce4f9a3e038ae7c44634522d54657c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45617224"
---
# <a name="region-directive"></a>#Region — dyrektywa
Zwija i ukrywa sekcje kodu w plikach języka Visual Basic.  
  
## <a name="syntax"></a>Składnia  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`identifier_string`|Wymagane. Ciąg, który funkcjonuje jako tytuł regionu, gdy jest zwinięty. Regiony są domyślnie zwinięte.|  
|`#End Region`|Kończy blok `#Region`.|  
  
## <a name="remarks"></a>Uwagi  
 Dyrektywa `#Region` służy do określania bloku kodu, który będzie rozwijany lub zwijany podczas korzystania z funkcji zwijania w edytorze kodu programu Visual Studio. Regiony można umieszczać lub *zagnieżdżać* w innych regionach w celu grupowania podobnych regionów.  
  
## <a name="example"></a>Przykład  
 Dyrektywa `#Region` została użyta w poniższym przykładzie.  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [#If...Then...#Else, dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Obramowanie](/visualstudio/ide/outlining)  
 [Instrukcje: zwijanie i ukrywanie fragmentów kodu](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
