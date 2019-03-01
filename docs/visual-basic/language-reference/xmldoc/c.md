---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 5f07b9cc084c73a7dcaf8c4d5f631519e550781e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979498"
---
# <a name="c-visual-basic"></a>\<c > (Visual Basic)
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
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także
- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
