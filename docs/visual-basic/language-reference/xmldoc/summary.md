---
title: '&lt;Podsumowanie&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: cf320b61a2ca1c54b22e3c3d31ae51d003366efd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602655"
---
# <a name="ltsummarygt-visual-basic"></a>&lt;Podsumowanie&gt; (Visual Basic)
Określa podsumowanie elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a>Parametry  
 `description`  
 Podsumowanie obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<summary>` tag do opisu typu lub członka typu. Użyj [ \<Uwagi >](../../../visual-basic/language-reference/xmldoc/remarks.md) można dodać dodatkowe informacje do opisu typu.  
  
 Tekst dla `<summary>` tag jest jedynym źródłem informacji o typie w IntelliSense i jest wyświetlany w przeglądarce obiektów. Informacje o przeglądarce obiektów, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<summary>` tag do opisywania `ResetCounter` — metoda i `Counter` właściwości.  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
