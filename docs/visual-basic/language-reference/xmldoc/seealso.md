---
title: '&lt;SeeAlso&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 1d45c0c5fa95de9cfa345c0bdbf496aa227b9af5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604682"
---
# <a name="ltseealsogt-visual-basic"></a>&lt;SeeAlso&gt; (Visual Basic)
Określa łącze, które pojawia się w sekcji Zobacz też.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 `member`  
 Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywoływania z bieżącym środowisku kompilacji. Kompilator sprawdza, czy element podanego kodu istnieje i przekazuje `member` do nazwy elementu w danych wyjściowych XML. `member` musi występować w podwójny cudzysłów ("").  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<seealso>` tag, aby określić tekst, który ma być wyświetlany w sekcji Zobacz też. Użyj [ \<zobacz >](../../../visual-basic/language-reference/xmldoc/see.md) można określić łącze od w tekście.  
  
 Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<seealso>` tagów w `DoesRecordExist` uwagi sekcji, aby odwołać się do `UpdateRecord` metody.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/seealso_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
