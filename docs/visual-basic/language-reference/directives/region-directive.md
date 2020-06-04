---
title: '##Region, dyrektywa'
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
ms.openlocfilehash: cd53a6079c1564a8c73a0a1a6273fc166d18d3e6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409946"
---
# <a name="region-directive"></a>#Region — dyrektywa

Zwija i ukrywa sekcje kodu w plikach Visual Basic.  
  
## <a name="syntax"></a>Składnia  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`identifier_string`|Wymagany. Ciąg, który działa jako tytuł regionu, gdy jest zwinięty. Regiony są domyślnie zwinięte.|  
|`#End Region`|Kończy `#Region` blok.|  
  
## <a name="remarks"></a>Uwagi  

 Użyj `#Region` dyrektywy, aby określić blok kodu do rozwinięcia lub zwinięcia przy użyciu funkcji tworzenia konspektu edytora Visual Studio Code. Możesz umieszczać lub *zagnieżdżać*regiony w innych regionach, aby grupować podobne regiony jednocześnie.  
  
## <a name="example"></a>Przykład  

 Ten przykład używa `#Region` dyrektywy.  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>Zobacz też

- [#If... Then... #Else — dyrektywy](if-then-else-directives.md)
- [Tworzenie konspektu](/visualstudio/ide/outlining)
- [Instrukcje: Zwijanie i ukrywanie fragmentów kodu](../../programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
