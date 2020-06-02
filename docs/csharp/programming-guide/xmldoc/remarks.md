---
title: <remarks> — Przewodnik programowania w języku C#
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 739027786e02e559d86f990bf614e261b497c76f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287288"
---
# <a name="remarks-c-programming-guide"></a>\<remarks>(Przewodnik programowania w języku C#)

## <a name="syntax"></a>Składnia

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a>Parametry

- `Description`

  Opis elementu członkowskiego.

## <a name="remarks"></a>Uwagi

`<remarks>`Tag służy do dodawania informacji o typie, uzupełniając informacje określone za pomocą [\<summary>](./summary.md) . Te informacje są wyświetlane w oknie Przeglądarka obiektów.

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
