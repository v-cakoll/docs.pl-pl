---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 1cbac2162bd39cdc8af9a55dfd6e2f90bc40b08a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354323"
---
# <a name="code-visual-basic"></a>> kodu \<(Visual Basic)
Wskazuje, że tekst jest wieloma wierszami kodu.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a>Parametry  
 `content`  
 Tekst, który ma zostać oznaczony jako kod.  
  
## <a name="remarks"></a>Uwagi  
 Użyj znacznika `<code>`, aby wskazać wiele wierszy jako kod. Użyj [\<c >](../../../visual-basic/language-reference/xmldoc/c.md) , aby wskazać, że tekst w opisie powinien być oznaczony jako kod.  
  
 Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto tagu \<Code >, aby dołączyć przykładowy kod do użycia pola `ID`.  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
