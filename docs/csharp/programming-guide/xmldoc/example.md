---
title: <example> — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: 615eccbc427b6a5bbbed061acd0c8b0b9be7f46c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789819"
---
# <a name="example-c-programming-guide"></a>> \<przykład (C# Przewodnik programowania)

## <a name="syntax"></a>Składnia

```xml
<example>description</example>
```

## <a name="parameters"></a>Parametry

- `description`

  Opis przykładu kodu.

## <a name="remarks"></a>Uwagi

\<przykład > tag pozwala określić przykład użycia metody lub innego elementu członkowskiego biblioteki. Ten proces często obejmuje użycie tagu [> code\<](./code.md) .

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane Tagi dla komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
