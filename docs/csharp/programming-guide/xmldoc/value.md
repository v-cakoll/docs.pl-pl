---
title: <value> — Przewodnik programowania w języku C#
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: bd6630a8d5894fda39ad289c8dd584f6d84e5490
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287197"
---
# <a name="value-c-programming-guide"></a>\<value>(Przewodnik programowania w języku C#)

## <a name="syntax"></a>Składnia

```xml
<value>property-description</value>
```

## <a name="parameters"></a>Parametry

- `property-description`

  Opis właściwości.

## <a name="remarks"></a>Uwagi

`<value>`Tag umożliwia opisanie wartości reprezentowanej przez właściwość. Po dodaniu właściwości za pośrednictwem Kreatora kodu w środowisku deweloperskim Visual Studio .NET dodaje [\<summary>](./summary.md) tag nowej właściwości. Następnie należy ręcznie dodać tag, `<value>` aby opisać wartość, którą reprezentuje właściwość.

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
