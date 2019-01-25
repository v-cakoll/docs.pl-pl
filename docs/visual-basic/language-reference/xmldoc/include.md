---
title: '&lt;obejmują&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 1cd992ae12e21b3d7fe29aff5a15b280c663d13b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693071"
---
# <a name="ltincludegt-visual-basic"></a>&lt;obejmują&gt; (Visual Basic)
Odnosi się do innego pliku, który opisuje typy i elementy członkowskie w kodzie źródłowym.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Wymagana. Nazwa pliku zawierającego dokumentację. Nazwa pliku może być kwalifikowana przy użyciu ścieżki. Ujmij `filename` w podwójnym cudzysłowie ("").  
  
 `tagpath`  
 Wymagana. Ścieżka znaczniki `filename` prowadzi to do tagu `name`. Zamknij ścieżkę w znaki podwójnego cudzysłowu ("").  
  
 `name`  
 Wymagana. Określenie nazwy w tagu, który poprzedza komentarze. `Name` będzie miał `id`.  
  
 `id`  
 Wymagana. Identyfikator tagu, który poprzedza komentarze. Umieść identyfikator w znaki pojedynczego cudzysłowu ("").  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<include>` tag do odwoływania się do komentarzy w innym pliku, które opisują typy i elementy członkowskie w kodzie źródłowym. Jest to alternatywa do wprowadzania komentarzy dokumentacji bezpośrednio w pliku kodu źródłowego.  
  
 `<include>` Tag używa zalecenie w wersji 1.0 W3C XML Path Language (XPath). Aby uzyskać więcej informacji na temat sposobów dostosowania Twojego `<include>` , zobacz <https://www.w3.org/TR/xpath>.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<include>` tag, aby zaimportować komentarzy dokumentacji elementu członkowskiego z pliku o nazwie `commentFile.xml`.  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 Format `commentFile.xml` jest następujący.  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
