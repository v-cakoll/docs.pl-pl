---
title: <c>— Przewodnik programowania w języku C#
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
ms.openlocfilehash: a09bcd069e2f85f4a21736cb218c42c0e481d70b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287470"
---
# <a name="c-c-programming-guide"></a>\<c>(Przewodnik programowania w języku C#)

## <a name="syntax"></a>Składnia

```xml
<c>text</c>
```

## <a name="parameters"></a>Parametry

- `text`

  Tekst, który ma być wskazywany jako kod.

## <a name="remarks"></a>Uwagi

`<c>`Tag umożliwia wskazanie, że tekst w opisie powinien być oznaczony jako kod. Użyj [\<code>](./code.md) , aby wskazać wiele wierszy jako kod.

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
