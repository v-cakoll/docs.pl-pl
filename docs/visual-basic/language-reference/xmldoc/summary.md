---
title: '&lt;Podsumowanie&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2a3008d1393c44aa0ec2398a2bd6afa079013e7e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
