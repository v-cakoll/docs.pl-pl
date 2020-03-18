---
title: <c>- Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: d5b28ee6db52d191f8454592d792ac0a1e1dc73b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793457"
---
# <a name="c-c-programming-guide"></a>\<c> (przewodnik programowania C#)

## <a name="syntax"></a>Składnia

```xml
<c>text</c>
```

## <a name="parameters"></a>Parametry

- `text`

  Tekst, który chcesz wskazać jako kod.

## <a name="remarks"></a>Uwagi

Tag \<> c umożliwia wskazanie, że tekst w opisie powinien być oznaczony jako kod. Użyj [ \<kodu>,](./code.md) aby wskazać wiele wierszy jako kod.

Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
