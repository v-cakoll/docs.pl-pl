---
title: <example> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 75e6f966f8baac2fd3c863c7caea939d80bfc41b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255527"
---
# <a name="example-visual-basic"></a>\<przykład > (Visual Basic)
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
  
## <a name="see-also"></a>Zobacz także
- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
