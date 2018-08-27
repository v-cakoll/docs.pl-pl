---
title: '&lt;param&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 4cb3de06d574f8b9abb3e3e11641a6ada750b56a
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935761"
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
  
## <a name="see-also"></a>Zobacz też  
 [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
