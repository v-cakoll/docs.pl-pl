---
title: <returns> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 0463d1b489fdad5e6af2d8eb20a1e68c77f57b4d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254967"
---
# <a name="returns-visual-basic"></a>\<Zwraca > (Visual Basic)
Określa wartość zwracaną właściwości lub funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a>Parametry  
 `description`  
 Opis wartość zwracaną.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<returns>` tagu w komentarzu do deklaracji metody opisać wartość zwracaną.  
  
 Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<returns>` tag, aby wyjaśnić, co `DoesRecordExist` funkcja zwraca.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
