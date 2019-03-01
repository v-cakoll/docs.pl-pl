---
title: <summary> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 531cac9bfec24577c22cb52962b2ac1eb740c5c8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975501"
---
# <a name="summary-visual-basic"></a>\<Podsumowanie > (Visual Basic)
Określa podsumowanie elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a>Parametry  
 `description`  
 Podsumowanie obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<summary>` znaczników do opisu typu lub składowej typu. Użyj [ \<Uwagi >](../../../visual-basic/language-reference/xmldoc/remarks.md) można dodać dodatkowe informacje do opisu typu.  
  
 Tekst dla `<summary>` tagu to jedyne źródło informacji o typie w technologii IntelliSense i jest wyświetlany w przeglądarce obiektów. Aby uzyskać informacje o przeglądarce obiektów, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<summary>` tag do opisania `ResetCounter` metody i `Counter` właściwości.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także
- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
