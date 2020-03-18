---
title: <param> - Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d16070a82531519dd276b2ea999623017769d716
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789756"
---
# <a name="param-c-programming-guide"></a>\<param> (przewodnik programowania C#)

## <a name="syntax"></a>Składnia

```xml
<param name="name">description</param>
```

## <a name="parameters"></a>Parametry

- `name`

  Nazwa parametru metody. Nazwę ująć w podwójne cudzysłowy (" ").

- `description`

  Opis parametru.

## <a name="remarks"></a>Uwagi

Tag \<> param powinien być używany w komentarzu dla deklaracji metody, aby opisać jeden z parametrów metody. Aby udokumentować wiele parametrów, należy użyć wielu \<tagów> paramów.

Tekst znacznika \<> param ów będzie wyświetlany w intelliSense, przeglądarce obiektów oraz w raporcie internetowym komentarzu kodu.

Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
