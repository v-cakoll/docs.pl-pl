---
title: '&lt;przykład&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 2de91d828fd9706b66f4c810486e54e2d3062de0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43384234"
---
# <a name="ltexamplegt-visual-basic"></a>&lt;przykład&gt; (Visual Basic)
Określa przykład dla elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<example>description</example>  
```  
  
#### <a name="parameters"></a>Parametry  
 `description`  
 Opis przykładowego kodu.  
  
## <a name="remarks"></a>Uwagi  
 `<example>` Należy określić przykładem przedstawiającym sposób użycia metody lub innego członka biblioteki. Często wiąże się to przy użyciu [ \<kodu >](../../../visual-basic/language-reference/xmldoc/code.md) tagu.  
  
 Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<example>` tag, aby uwzględnić przykład za pomocą `ID` pola.  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/example_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
