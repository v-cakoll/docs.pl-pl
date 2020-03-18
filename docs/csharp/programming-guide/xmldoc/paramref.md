---
title: <paramref>- Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 12df257271369dc7f0a5c066b712a8d8e6c38761
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793403"
---
# <a name="paramref-c-programming-guide"></a>\<paramref> (przewodnik programowania C#)

## <a name="syntax"></a>Składnia

```xml
<paramref name="name"/>
```

## <a name="parameters"></a>Parametry

- `name`

  Nazwa parametru, do który ma się odwoływać. Nazwę ująć w podwójne cudzysłowy (" ").

## <a name="remarks"></a>Uwagi

Tag \<> paramref umożliwia wskazanie, że słowo w komentarzach do \<kodu, \<na przykład w> podsumowującym lub uwagi> bloku odnosi się do parametru. Plik XML można przetworzyć w celu sformatowania tego wyrazu w różny sposób, na przykład czcionką pogrubioną lub kursywą.

Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
