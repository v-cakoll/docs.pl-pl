---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 06c6899895f278fdf652725a05ecc7229805f4d4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43455708"
---
# <a name="ltcgt-visual-basic"></a>&lt;c&gt; (Visual Basic)
Wskazuje, że tekst w ciągu opisu jest kod.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---|---|  
|`text`|Tekst, który chcesz wskazać jako kod.|  
  
## <a name="remarks"></a>Uwagi  
 `<c>` Tag zapewnia sposób, aby wskazać, że tekst w opis powinien być oznaczony jako kod. Użyj [ \<kodu >](../../../visual-basic/language-reference/xmldoc/code.md) aby wskazać wiele wierszy, jako kod.  
  
 Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<c>` tagu w sekcji podsumowania w celu wskazania, że `Counter` jest kod.  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
