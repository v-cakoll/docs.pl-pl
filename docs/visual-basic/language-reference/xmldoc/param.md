---
title: '&lt;param&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: cc9ceccef8123d49d6267276e9dcb7be84f78a01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670683"
---
# <a name="ltparamgt-visual-basic"></a>&lt;param&gt; (Visual Basic)
Określa nazwę parametru i opis.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Nazwa parametru metody. Nazwę należy ująć w znaki podwójnego cudzysłowu ("").  
  
 `description`  
 Opis parametru.  
  
## <a name="remarks"></a>Uwagi  
 `<param>` Używany tag w komentarzu do deklaracji metody do opisania jeden z parametrów dla metody.  
  
 Tekst dla `<param>` tag pojawi się w następujących lokalizacjach:  
  
-   Informacje o parametrach IntelliSense. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](/visualstudio/ide/using-intellisense).  
  
-   Przeglądarka obiektów. Aby uzyskać więcej informacji, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<param>` tag do opisania `id` parametru.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
