---
title: '&lt;Uwagi&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 6e4e280760b9238fdc403ac5fe586743334e4c69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598202"
---
# <a name="ltremarksgt-visual-basic"></a>&lt;Uwagi&gt; (Visual Basic)
Określa elementu członkowskiego w sekcji uwag.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a>Parametry  
 `description`  
 Opis elementu członkowskiego.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<remarks>` znacznik w celu dodania informacji o typie, uzupełniające podanych informacji o [ \<podsumowania >](../../../visual-basic/language-reference/xmldoc/summary.md).  
  
 Informacje te pojawiają się w przeglądarce obiektów. Informacje o przeglądarce obiektów, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<remarks>` tag, aby wyjaśnić, co `UpdateRecord` metoda wykonuje.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
