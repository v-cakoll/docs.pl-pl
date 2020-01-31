---
title: <typeparamref> — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 266eadad322fd3c4167c7a911cb57ef1e1333012
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789659"
---
# <a name="typeparamref-c-programming-guide"></a>\<typeparamref > (C# Przewodnik programowania)

## <a name="syntax"></a>Składnia

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a>Parametry

- `name`

  Nazwa parametru typu. Ujmij nazwę w znaki podwójnego cudzysłowu ("").

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat parametrów typu w typach ogólnych i metodach, zobacz [Generics](../generics/index.md).

Ten tag umożliwia użytkownikom pliku dokumentacji formatowanie wyrazu w niektórych odrębnych przypadkach, na przykład kursywą.

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Zobacz także

- [C#Przewodnik programowania](../index.md)
- [Zalecane Tagi dla komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
