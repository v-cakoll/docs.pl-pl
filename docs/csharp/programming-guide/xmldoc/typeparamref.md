---
title: <typeparamref>- Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 266eadad322fd3c4167c7a911cb57ef1e1333012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789659"
---
# <a name="typeparamref-c-programming-guide"></a>\<typeparamref> (przewodnik programowania C#)

## <a name="syntax"></a>Składnia

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a>Parametry

- `name`

  Nazwa parametru typu. Nazwę ująć w podwójne cudzysłowy (" ").

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat parametrów typu w typach ogólnych i metodach, zobacz [Generyk.](../generics/index.md)

Użyj tego tagu, aby umożliwić konsumentom pliku dokumentacji formatowanie wyrazu w różny sposób, na przykład kursywą.

Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
