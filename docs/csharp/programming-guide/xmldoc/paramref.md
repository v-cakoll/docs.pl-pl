---
title: <paramref>— Przewodnik programowania w języku C#
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 4f3b521d24c8b4677a05b0b145cb36c31b2793f2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287314"
---
# <a name="paramref-c-programming-guide"></a>\<paramref>(Przewodnik programowania w języku C#)

## <a name="syntax"></a>Składnia

```xml
<paramref name="name"/>
```

## <a name="parameters"></a>Parametry

- `name`

  Nazwa parametru, do którego się odwołuje. Ujmij nazwę w znaki podwójnego cudzysłowu ("").

## <a name="remarks"></a>Uwagi

`<paramref>`Tag umożliwia wskazanie, że słowo w komentarzach do kodu, na przykład w `<summary>` `<remarks>` bloku lub odwołuje się do parametru. Plik XML można przetworzyć, aby sformatować ten wyraz w sposób niezależny, na przykład za pomocą czcionki pogrubionej lub kursywy.

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
