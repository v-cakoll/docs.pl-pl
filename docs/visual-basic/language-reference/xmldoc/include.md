---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 78a10624107cea349b01f484c641190a945dbd7e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400114"
---
# <a name="include-visual-basic"></a>\<include> (Visual Basic)
Odwołuje się do innego pliku opisującego typy i elementy członkowskie w kodzie źródłowym.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a>Parametry  
 `filename`  
 Wymagany. Nazwa pliku zawierającego dokumentację. Nazwa pliku może być kwalifikowana za pomocą ścieżki. Należy ująć `filename` w znaki podwójnego cudzysłowu ("").  
  
 `tagpath`  
 Wymagany. Ścieżka tagów `filename` , które prowadzą do znacznika `name` . Ujmij ścieżkę w znaki podwójnego cudzysłowu ("").  
  
 `name`  
 Wymagany. Specyfikator Name w tagu, który poprzedza Komentarze. `Name`ma `id` .  
  
 `id`  
 Wymagany. Identyfikator tagu, który poprzedza Komentarze. Ujmij identyfikator w znaki pojedynczego cudzysłowu (' ').  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<include>` znacznika, aby odwołać się do komentarzy w innym pliku, które opisują typy i elementy członkowskie w kodzie źródłowym. Jest to alternatywa dla umieszczania komentarzy do dokumentacji bezpośrednio w pliku kodu źródłowego.  
  
 Ten `<include>` tag używa zalecenia języka XML Path (XPath) w wersji 1,0. Więcej informacji o sposobach dostosowywania `<include>` użycia znajduje się w temacie <https://www.w3.org/TR/xpath> .  
  
## <a name="example"></a>Przykład  
 Ten przykład używa `<include>` znacznika do importowania komentarzy do dokumentacji członków z pliku o nazwie `commentFile.xml` .  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Tagi komentarza XML](index.md)
