---
title: <example> — Przewodnik programowania w języku C#
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: e8d26f82562cc5140662f5b32ea9fedf5481d8f8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287397"
---
# <a name="example-c-programming-guide"></a>\<example>(Przewodnik programowania w języku C#)

## <a name="syntax"></a>Składnia

```xml
<example>description</example>
```

## <a name="parameters"></a>Parametry

- `description`

  Opis przykładu kodu.

## <a name="remarks"></a>Uwagi

`<example>`Tag pozwala określić przykład użycia metody lub innego elementu członkowskiego biblioteki. Zwykle obejmuje to użycie [\<code>](./code.md) znacznika.

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
