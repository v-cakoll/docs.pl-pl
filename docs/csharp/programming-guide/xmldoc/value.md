---
title: <value> — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 120805346672738e614743ab8c98388b8dbac0f7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793349"
---
# <a name="value-c-programming-guide"></a>> wartości \<(C# Przewodnik programowania)

## <a name="syntax"></a>Składnia

```xml
<value>property-description</value>
```

## <a name="parameters"></a>Parametry

- `property-description`

  Opis właściwości.

## <a name="remarks"></a>Uwagi

Tag \<wartość > umożliwia opisanie wartości reprezentowanej przez właściwość. Należy pamiętać, że po dodaniu właściwości za pośrednictwem Kreatora kodu w środowisku deweloperskim Visual Studio .NET zostanie dodany tag [\<summary >](./summary.md) dla nowej właściwości. Następnie należy ręcznie dodać tag \<wartość >, aby opisać wartość, którą reprezentuje właściwość.

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>Zobacz także

- [C#Przewodnik programowania](../index.md)
- [Zalecane Tagi dla komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
