---
title: <list> - Przewodnik programowania C#
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
ms.openlocfilehash: cb289b26e9bc12d561892c421fb40da18d8c3513
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789752"
---
# <a name="list-c-programming-guide"></a>\<lista> (przewodnik programowania C#)

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

  Termin do zdefiniowania, który `description`zostanie zdefiniowany w .

- `description`

  Element na liście punktorowej lub numerowanej `term`lub definicja .
  
## <a name="remarks"></a>Uwagi

Blok \<> listheader służy do definiowania wiersza nagłówka tabeli lub listy definicji. Podczas definiowania tabeli, należy podać tylko wpis dla terminu w nagłówku.

Każdy element na liście jest \<określony z elementem> bloku. Podczas tworzenia listy definicji należy określić `term` oba `description`i . Jednak w przypadku tabeli, listy punktowanej lub listy numerowanej wystarczy `description`podać wpis dla .

Lista lub tabela może \<mieć dowolną liczbę elementów> bloków, zgodnie z potrzebami.

Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
