---
title: '&lt;obejmują&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: da7a6c15c558fc56dbc6a874d4a28c4434f67668
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482707"
---
# <a name="ltincludegt-visual-basic"></a>&lt;obejmują&gt; (Visual Basic)
Odnosi się do innego pliku, który opisuje typy i elementy członkowskie w kodzie źródłowym.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Wymagane. Nazwa pliku zawierającego dokumentację. Nazwa pliku może być kwalifikowana przy użyciu ścieżki. Ujmij `filename` w podwójnym cudzysłowie ("").  
  
 `tagpath`  
 Wymagane. Ścieżka znaczniki `filename` prowadzi to do tagu `name`. Zamknij ścieżkę w znaki podwójnego cudzysłowu ("").  
  
 `name`  
 Wymagane. Określenie nazwy w tagu, który poprzedza komentarze. `Name` będzie miał `id`.  
  
 `id`  
 Wymagane. Identyfikator tagu, który poprzedza komentarze. Umieść identyfikator w znaki pojedynczego cudzysłowu ("").  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<include>` tag do odwoływania się do komentarzy w innym pliku, które opisują typy i elementy członkowskie w kodzie źródłowym. Jest to alternatywa do wprowadzania komentarzy dokumentacji bezpośrednio w pliku kodu źródłowego.  
  
 `<include>` Tag używa zalecenie w wersji 1.0 W3C XML Path Language (XPath). Więcej informacji o sposobach dostosowywania swoje `<include>` użycia znajduje się w temacie http://www.w3.org/TR/xpath.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
