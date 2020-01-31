---
title: <include> — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 1e3722cbed02775d0ad4f392840ea10275c96be1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793432"
---
# <a name="include-c-programming-guide"></a>\<Uwzględnij >C# (Przewodnik programowania)

## <a name="syntax"></a>Składnia

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## <a name="parameters"></a>Parametry

- `filename`

  Nazwa pliku XML zawierającego dokumentację. Nazwa pliku może być kwalifikowana ze ścieżką względną do pliku kodu źródłowego. Ujmij `filename` w znaki pojedynczego cudzysłowu (' ').

- `tagpath`

  Ścieżka tagów w `filename`, które prowadzą do `name`znacznika. Ujmij ścieżkę w znaki pojedynczego cudzysłowu (' ').

- `name`

  Specyfikator nazwy w tagu, który poprzedza Komentarze; `name` będzie `id`.

- `id`

Identyfikator tagu, który poprzedza Komentarze. Ujmij identyfikator w znaki podwójnego cudzysłowu ("").

## <a name="remarks"></a>Uwagi

\<include tag > umożliwia odwoływanie się do komentarzy w innym pliku, które opisują typy i elementy członkowskie w kodzie źródłowym. Jest to alternatywa dla umieszczania komentarzy do dokumentacji bezpośrednio w pliku kodu źródłowego. Umieszczając dokumentację w osobnym pliku, można zastosować kontrolę źródła do dokumentacji niezależnie od kodu źródłowego. Jedna osoba może mieć wyewidencjonowany plik kodu źródłowego, a ktoś inny może mieć wyewidencjonowany plik dokumentacji.

\<include tag > używa składni XML XPath. Zapoznaj się z dokumentacją XPath, aby dostosowywać \<obejmują > Użycie.

## <a name="example"></a>Przykład

Jest to przykład wieloplikowy. Poniżej znajduje się pierwszy plik, który używa \<zawiera >.

[!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]

Drugi plik, *xml_include_tag. doc*, zawiera następujące Komentarze do dokumentacji.

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

Następujące dane wyjściowe są generowane podczas kompilowania klas test i TEST2 z następującym wierszem polecenia: `-doc:DocFileName.xml.` w programie Visual Studio, należy określić opcję komentarzy w dokumencie XML w okienku kompilacja projektanta projektu. Gdy C# kompilator widzi tag \<include >, będzie wyszukiwał komentarze dokumentacji w xml_include_tag. doc zamiast bieżącego pliku źródłowego. Następnie kompilator generuje DocFileName. XML i jest to plik, który jest używany przez narzędzia dokumentacji, takie jak [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle](https://github.com/EWSoftware/SHFB) , aby utworzyć ostateczną dokumentację.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
