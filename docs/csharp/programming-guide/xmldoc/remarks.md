---
title: <remarks> - Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: e37dac9cb9fed1df6ca027f09f2c95dbbc8ea66d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793375"
---
# <a name="remarks-c-programming-guide"></a>\<uwagi> (przewodnik programowania C#)

## <a name="syntax"></a>Składnia

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a>Parametry

- `Description`

  Opis elementu członkowskiego.

## <a name="remarks"></a>Uwagi

Uwagi \<> tag użyje do dania informacji o typie, uzupełniając informacje określone [ \<>podsumowania ](./summary.md). Informacje te są wyświetlane w oknie Przeglądarka obiektów.

Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
