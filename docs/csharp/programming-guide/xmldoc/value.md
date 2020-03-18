---
title: <value> - Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 120805346672738e614743ab8c98388b8dbac0f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793349"
---
# <a name="value-c-programming-guide"></a>\<wartość> (przewodnik programowania C#)

## <a name="syntax"></a>Składnia

```xml
<value>property-description</value>
```

## <a name="parameters"></a>Parametry

- `property-description`

  Opis obiektu.

## <a name="remarks"></a>Uwagi

Wartość \<> tag pozwala opisać wartość, która reprezentuje właściwość. Należy zauważyć, że po dodaniu właściwości za pomocą kreatora kodu w środowisku programistycznym programu Visual Studio .NET doda [ \<podsumowanie>](./summary.md) tag dla nowej właściwości. Następnie należy ręcznie \<dodać wartość> tag, aby opisać wartość, która reprezentuje właściwość.

Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
