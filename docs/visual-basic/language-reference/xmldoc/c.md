---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 857ea1ccca4d74daf65bba03845004561afefd55
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348509"
---
# <a name="c-visual-basic"></a>> \<c (Visual Basic)
Wskazuje, że tekst w opisie ma kod.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---|---|  
|`text`|Tekst, który ma być wskazywany jako kod.|  
  
## <a name="remarks"></a>Uwagi  
 Tag `<c>` umożliwia wskazanie, że tekst w opisie powinien być oznaczony jako kod. Użyj [\<kodu >](../../../visual-basic/language-reference/xmldoc/code.md) , aby wskazać wiele wierszy jako kod.  
  
 Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano tag `<c>` w sekcji Podsumowanie, aby wskazać, że `Counter` jest kodem.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
