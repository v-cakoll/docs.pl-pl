---
title: '&lt;obejmują&gt; (C# przewodnik programowania w języku)'
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: a681a2fcbb874d67b82c8bda73d92dd993928bbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334512"
---
# <a name="ltincludegt-c-programming-guide"></a>&lt;obejmują&gt; (C# przewodnik programowania w języku)
## <a name="syntax"></a>Składnia  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Nazwa pliku XML zawierającego w dokumentacji. Nazwa pliku może być kwalifikowany za pomocą ścieżki. Umieść `filename` w pojedynczym cudzysłowie ("").  
  
 `tagpath`  
 Ścieżka tagów w `filename` prowadzi to do tagu `name`. Ścieżka do ujmij ją w pojedynczym cudzysłowie ("").  
  
 `name`  
 Określenie nazwy w tagu poprzedzający komentarze; `name` będzie mieć `id`.  
  
 `id`  
 Identyfikator znacznika poprzedzający komentarze. Umieść identyfikator w podwójny cudzysłów ("").  
  
## <a name="remarks"></a>Uwagi  
 \<Obejmują > należy odwoływać się do komentarzy w innym pliku, które opisują typy i elementy członkowskie w kodzie źródłowym. Jest to alternatywa do wprowadzania komentarzy do dokumentacji bezpośrednio w pliku kodu źródłowego. Umieszczenie w dokumentacji w osobnym pliku, można zastosować do kontroli źródła do dokumentacji oddzielnie z kodu źródłowego. Jedna osoba może mieć wyewidencjonować pliku źródła kodu, a ktoś inny może mieć plik dokumentacji wyewidencjonowany.  
  
 \<Obejmują > tag używa składni XML XPath. Zapoznaj się z dokumentacją XPath o sposobach dostosowywania Twojej \<obejmują > Użyj.  
  
## <a name="example"></a>Przykład  
 To jest przykład wiele plików. Pierwszy plik, który używa \<obejmują >, to wymienione poniżej:  
  
 [!code-csharp[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]  
  
 Drugi plik, xml_include_tag.doc, zawiera następujące komentarzy dokumentacji:  
  
```xml  
<MyDocs>  
  
<MyMembers name="test">  
<summary>  
The summary for this type.  
</summary>  
</MyMembers>  
  
<MyMembers name="test2">  
<summary>  
The summary for this other type.  
</summary>  
</MyMembers>  
  
</MyDocs>  
```  
  
## <a name="program-output"></a>Dane wyjściowe programu  
 Następujące dane wyjściowe jest generowany, gdy kompilacji testowych i Test2 klas z następującego wiersza polecenia: `/doc:DocFileName.xml.` w programie Visual Studio, możesz określić opcję komentarzy dokumentu XML w okienku kompilacji w Projektancie projektu. Gdy widzi kompilatora C# \<obejmują > tag, przeszukiwane są przeznaczone do komentarzy dokumentacji w xml_include_tag.doc zamiast bieżącego pliku źródłowego. Kompilator generuje następnie DocFileName.xml i jest to plik, który jest używany przez dokumentacji narzędzia, takie jak [Sandcastle](https://github.com/EWSoftware/SHFB) wygenerowało końcowego dokumentacji.  
  
```xml  
<?xml version="1.0"?>   
<doc>   
    <assembly>   
        <name>xml_include_tag</name>   
    </assembly>   
    <members>   
        <member name="T:Test">   
            <summary>   
The summary for this type.   
</summary>   
        </member>   
        <member name="T:Test2">   
            <summary>   
The summary for this other type.   
</summary>   
        </member>   
    </members>   
</doc>   
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Zalecane tagi przeznaczone do komentarzy dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
