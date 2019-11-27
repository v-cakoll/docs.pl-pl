---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 2f2bebfd06d4614f05cb66834cc5bef40524ce3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348463"
---
# <a name="include-visual-basic"></a>\<Uwzględnij > (Visual Basic)
Odwołuje się do innego pliku opisującego typy i elementy członkowskie w kodzie źródłowym.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a>Parametry  
 `filename`  
 Wymagana. Nazwa pliku zawierającego dokumentację. Nazwa pliku może być kwalifikowana za pomocą ścieżki. Ujmij `filename` w znaki podwójnego cudzysłowu ("").  
  
 `tagpath`  
 Wymagana. Ścieżka tagów w `filename`, które prowadzą do `name`znacznika. Ujmij ścieżkę w znaki podwójnego cudzysłowu ("").  
  
 `name`  
 Wymagana. Specyfikator Name w tagu, który poprzedza Komentarze. `Name` będzie `id`.  
  
 `id`  
 Wymagana. Identyfikator tagu, który poprzedza Komentarze. Ujmij identyfikator w znaki pojedynczego cudzysłowu (' ').  
  
## <a name="remarks"></a>Uwagi  
 Użyj znacznika `<include>`, aby odwołać się do komentarzy w innym pliku, które opisują typy i elementy członkowskie w kodzie źródłowym. Jest to alternatywa dla umieszczania komentarzy do dokumentacji bezpośrednio w pliku kodu źródłowego.  
  
 Tag `<include>` używa zalecenia XML (W3C) Path Language (XPath) w wersji 1,0. Aby uzyskać więcej informacji o sposobach dostosowywania użycia `<include>`, zobacz <https://www.w3.org/TR/xpath>.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa znacznika `<include>` do importowania komentarzy do dokumentacji członków z pliku o nazwie `commentFile.xml`.  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
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
