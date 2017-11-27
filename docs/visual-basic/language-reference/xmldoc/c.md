---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e57cae8fd4b93fee59992d717135ad7d3d78be5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltcgt-visual-basic"></a>&lt;c&gt; (Visual Basic)
Wskazuje, że tekst opisu jest kod.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---|---|  
|`text`|Tekst, który chcesz wskazać jako kod.|  
  
## <a name="remarks"></a>Uwagi  
 `<c>` Tag zapewnia sposób, aby wskazać, że tekst opisu powinien być oznaczony jako kod. Użyj [ \<kod >](../../../visual-basic/language-reference/xmldoc/code.md) wskazująca wiele wierszy, jak kod.  
  
 Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<c>` tagu w sekcji podsumowania, aby wskazać, że `Counter` jest kod.  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
