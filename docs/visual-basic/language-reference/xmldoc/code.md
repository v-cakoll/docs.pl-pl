---
title: '&lt;Kod&gt; (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a7c1d8ab3db0c36c6a2935b9ffbef15e87df5ebc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltcodegt-visual-basic"></a>&lt;Kod&gt; (Visual Basic)
Wskazuje, czy tekst ma wiele wierszy kodu.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a>Parametry  
 `content`  
 Tekst, który chcesz oznaczyć jako kod.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<code>` tag, aby wskazać wiele wierszy, jak kod. Użyj [ \<c >](../../../visual-basic/language-reference/xmldoc/c.md) aby wskazać, że tekst opisu powinien być oznaczony jako kod.  
  
 Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto \<kod > tag, aby uwzględnić przykładowy kod służący do przy użyciu `ID` pola.  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
