---
title: '&lt;Kod&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: e66aebe35dd8f6443fefe3b07842b37270159e6e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858642"
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
  
## <a name="see-also"></a>Zobacz też  
 [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
