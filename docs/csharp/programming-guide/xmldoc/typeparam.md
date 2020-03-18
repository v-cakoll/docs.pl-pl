---
title: <typeparam> - Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 867ecacf58f95533395ded203a8f17bc92558ccf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793366"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam> (przewodnik programowania C#)

## <a name="syntax"></a>Składnia

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a>Parametry

- `name`

  Nazwa parametru typu. Nazwę ująć w podwójne cudzysłowy (" ").

- `description`

  Opis parametru typu.

## <a name="remarks"></a>Uwagi

Tag `<typeparam>` powinien być używany w komentarzu dla typu ogólnego lub deklaracji metody do opisania parametru typu. Dodaj znacznik dla każdego parametru typu typu ogólnego lub metody.

Aby uzyskać więcej informacji, zobacz [Generyk .](../generics/index.md)

Tekst znacznika `<typeparam>` będzie wyświetlany w raporcie internetowym IntelliSense, w raporcie internetowym [kodu okna przeglądarki obiektów.](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser)

Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../language-reference/index.md)
- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
