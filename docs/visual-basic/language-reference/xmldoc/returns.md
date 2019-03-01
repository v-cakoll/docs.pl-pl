---
title: <returns> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 96b9754332b7b9c6c7823aecab6a93b0aa7ffd21
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975462"
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
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także
- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
