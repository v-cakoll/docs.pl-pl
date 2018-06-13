---
title: '&lt;obejmują&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 65bc0439696612cd8331a9c0718efcfee83af574
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602739"
---
# <a name="ltincludegt-visual-basic"></a>&lt;obejmują&gt; (Visual Basic)
Odwołuje się do innego pliku, który opisuje typy i składniki w kodzie źródłowym.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Wymagana. Nazwa pliku zawierającego w dokumentacji. Nazwa pliku może być kwalifikowany za pomocą ścieżki. Umieść `filename` w podwójny cudzysłów ("").  
  
 `tagpath`  
 Wymagana. Ścieżka tagów w `filename` prowadzi to do tagu `name`. Ścieżka do ujmij ją w podwójny cudzysłów ("").  
  
 `name`  
 Wymagana. Określenie nazwy w tagu poprzedzający komentarze. `Name` będzie mieć `id`.  
  
 `id`  
 Wymagana. Identyfikator znacznika poprzedzający komentarze. Umieść identyfikator w pojedynczym cudzysłowie ("").  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<include>` tag do odwoływania się do komentarzy w innym pliku, które opisują typy i elementy członkowskie w kodzie źródłowym. Jest to alternatywa do wprowadzania komentarzy do dokumentacji bezpośrednio w pliku kodu źródłowego.  
  
 `<include>` Tag używa zalecenie W3C XML Path Language (XPath) w wersji 1.0. Więcej informacji o sposobach dostosowywania Twojej `<include>` użycia znajduje się w temacie http://www.w3.org/TR/xpath.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<include>` tag importowanego elementu członkowskiego komentarzy do dokumentacji w pliku o nazwie `commentFile.xml`.  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 Format `commentFile.xml` ma następującą składnię.  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
