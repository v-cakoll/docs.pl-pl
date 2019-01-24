---
title: '&lt;Kod&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 8a4708a7b50b0e221c1ebe7f95d4f8ff80cd1ebe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566310"
---
# <a name="ltcodegt-visual-basic"></a>&lt;Kod&gt; (Visual Basic)
Wskazuje, że tekst jest wiele wierszy kodu.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a>Parametry  
 `content`  
 Tekst, aby oznaczyć jako kod.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<code>` tag, aby wskazać wiele wierszy, jako kod. Użyj [ \<c >](../../../visual-basic/language-reference/xmldoc/c.md) do wskazania, że tekst w opis powinien być oznaczony jako kod.  
  
 Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto \<kodu > tag obejmujący przykładowy kod dla przy użyciu `ID` pola.  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
