---
title: <example> - Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: 615eccbc427b6a5bbbed061acd0c8b0b9be7f46c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789819"
---
# <a name="example-c-programming-guide"></a>\<przykład> (przewodnik programowania C#)

## <a name="syntax"></a>Składnia

```xml
<example>description</example>
```

## <a name="parameters"></a>Parametry

- `description`

  Opis próbki kodu.

## <a name="remarks"></a>Uwagi

Przykładowy \<tag> umożliwia określenie przykładu użycia metody lub innego członka biblioteki. Wiąże się to często przy użyciu [ \<kodu>](./code.md) tagu.

Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
