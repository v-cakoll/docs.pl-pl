---
title: <list> — Przewodnik programowania w języku C#
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: 78eec992671dab1aa59717a007a8e3a2662f6e87
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287340"
---
# <a name="list-c-programming-guide"></a>\<list>(Przewodnik programowania w języku C#)

## <a name="syntax"></a>Składnia

```xml
<list type="bullet|number|table">
    <listheader>
        <term>term</term>
        <description>description</description>
    </listheader>
    <item>
        <term>term</term>
        <description>description</description>
    </item>
</list>
```

## <a name="parameters"></a>Parametry

- `term`

  Termin do zdefiniowania, który zostanie zdefiniowany w `description` .

- `description`

  Element na liście punktowanej lub numerowanej lub definicji `term` .
  
## <a name="remarks"></a>Uwagi

`<listheader>`Blok służy do definiowania wiersza nagłówka tabeli lub listy definicji. Podczas definiowania tabeli należy podać tylko wpis dla terminu w nagłówku.

Każdy element na liście jest określony za pomocą `<item>` bloku. Podczas tworzenia listy definicji należy określić zarówno, `term` jak i `description` . Jednak dla tabeli, listy punktowanej lub listy numerowanej wystarczy podać wpis dla `description` .

Lista lub tabela może zawierać tyle `<item>` bloków, ile jest to konieczne.

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
