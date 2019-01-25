---
title: <value> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 5aab2307a1967ea660282c7b324eaddfe798a155
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857895"
---
# <a name="value-visual-basic"></a>\<wartość > (Visual Basic)
Określa opis właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a>Parametry  
 `property-description`  
 Opis właściwości.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<value>` tag do opisywania właściwości. Należy pamiętać, że podczas dodawania właściwości, za pomocą Kreatora kodów w środowisku programowania Visual Studio, spowoduje to dodanie [ \<podsumowania >](../../../visual-basic/language-reference/xmldoc/summary.md) tag w przypadku nowej właściwości. Następnie należy ręcznie dodać `<value>` tag do opisania wartość, która reprezentuje właściwość.  
  
 Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<value>` tag do opisania wartość, jaką `Counter` przechowuje właściwości.  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
