---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 240c2131179420834e6dade729ee631c0d7811a4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352172"
---
# <a name="value-visual-basic"></a>> wartości \<(Visual Basic)
Określa opis właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>Parametry  
 `property-description`  
 Opis właściwości.  
  
## <a name="remarks"></a>Uwagi  
 Użyj znacznika `<value>`, aby opisać właściwość. Należy pamiętać, że po dodaniu właściwości przy użyciu kreatora kodu w środowisku deweloperskim programu Visual Studio zostanie dodany tag [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md) dla nowej właściwości. Następnie należy ręcznie dodać tag `<value>`, aby opisać wartość, którą reprezentuje właściwość.  
  
 Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa znacznika `<value>` do opisania wartości właściwości `Counter`.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
