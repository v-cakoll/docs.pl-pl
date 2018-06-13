---
title: '&lt;przykład&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8c09ab934ee7457fdff39a63c58f2546cda4d643
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598553"
---
# <a name="ltexamplegt-visual-basic"></a>&lt;przykład&gt; (Visual Basic)
Określa przykład elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<example>description</example>  
```  
  
#### <a name="parameters"></a>Parametry  
 `description`  
 Opis przykładowego kodu.  
  
## <a name="remarks"></a>Uwagi  
 `<example>` Należy określić przykładem przedstawiającym sposób użycia metody lub innego członka biblioteki. Obejmuje to zwykle, za pomocą [ \<kod >](../../../visual-basic/language-reference/xmldoc/code.md) tagu.  
  
 Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<example>` tag do uwzględnienia na przykład za pomocą `ID` pola.  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/example_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
