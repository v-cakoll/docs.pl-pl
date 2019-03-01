---
title: <paramref> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 3e889f97565f7961ce975f41e9ec4c85a4d0d2c6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965993"
---
# <a name="paramref-visual-basic"></a>\<paramref > (Visual Basic)
Formatuje wyrazem jako parametr.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Nazwa parametru do odwoływania się do. Nazwę należy ująć w znaki podwójnego cudzysłowu ("").  
  
## <a name="remarks"></a>Uwagi  
 `<paramref>` Tag zapewnia sposób, aby wskazać, że wyraz jest parametrem. Plik XML mogą być przetwarzane do formatowania tego parametru w jakiś sposób distinct.  
  
 Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<paramref>` tag do odwoływania się do `id` parametru.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także
- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
