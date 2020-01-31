---
title: <remarks> — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: e37dac9cb9fed1df6ca027f09f2c95dbbc8ea66d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793375"
---
# <a name="remarks-c-programming-guide"></a>\<uwagi > (C# Przewodnik programowania)

## <a name="syntax"></a>Składnia

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a>Parametry

- `Description`

  Opis elementu członkowskiego.

## <a name="remarks"></a>Uwagi

Tag \<uwagi > służy do dodawania informacji o typie, uzupełnienie informacji określonych za pomocą [\<podsumowania >](./summary.md). Te informacje są wyświetlane w oknie Przeglądarka obiektów.

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane Tagi dla komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
