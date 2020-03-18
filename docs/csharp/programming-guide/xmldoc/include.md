---
title: <include> - Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 22d87559766c04e53141e843ee8768c8aab89a85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156977"
---
# <a name="include-c-programming-guide"></a>\<obejmują> (przewodnik programowania C#)

## <a name="syntax"></a>Składnia

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## <a name="parameters"></a>Parametry

- `filename`

  Nazwa pliku XML zawierającego dokumentację. Nazwę pliku można zakwalifikować ścieżką względem pliku kodu źródłowego. Zacofij `filename` w pojedynczych cudzysłowu ('').

- `tagpath`

  Ścieżka znaczników `filename` w tym prowadzi `name`do tagu . Ścieżkę ująć w pojedyncze cudzysłowy (' ').

- `name`

  Specyfikator nazw w tagu, który poprzedza komentarze; `name` będzie miał `id`.

- `id`

Identyfikator tagu, który poprzedza komentarze. Identyfikator ujmij w cudzysłów podwójny (" ").

## <a name="remarks"></a>Uwagi

Tag \<> include umożliwia odwoływanie się do komentarzy w innym pliku, które opisują typy i elementy członkowskie w kodzie źródłowym. Jest to alternatywa dla umieszczania komentarzy dokumentacji bezpośrednio w pliku kodu źródłowego. Umieszczając dokumentację w oddzielnym pliku, można zastosować kontrolę źródła do dokumentacji oddzielnie od kodu źródłowego. Jedna osoba może wyewidencjonować plik kodu źródłowego, a ktoś inny może wyewidencjonować plik dokumentacji.

Tag \<> dołączania używa składni XML XPath. W dokumentacji XPath można \<znaleźć sposoby dostosowywania> użycia.

## <a name="example"></a>Przykład

Jest to przykład wieloplikowy. Poniżej przedstawiono pierwszy plik, \<który używa obejmują>.

[!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]

Drugi plik, *xml_include_tag.doc,* zawiera następujące komentarze dokumentacji.

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

Następujące dane wyjściowe są generowane podczas kompilowania testów i testów2 klas z następującym wierszem polecenia: `-doc:DocFileName.xml.` W programie Visual Studio można określić opcję komentarze doc XML w okienku kompilacji projektanta projektu. Gdy kompilator Języka \<C# widzi include> tag, będzie wyszukiwać komentarze dokumentacji w xml_include_tag.doc zamiast bieżącego pliku źródłowego. Kompilator następnie generuje DocFileName.xml, a jest to plik, który jest używany przez narzędzia dokumentacji, takie jak [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle](https://github.com/EWSoftware/SHFB) do produkcji ostatecznej dokumentacji.  
  
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

- [Przewodnik programowania języka C#](../index.md)
- [Zalecane tagi do komentarzy do dokumentacji](./recommended-tags-for-documentation-comments.md)
