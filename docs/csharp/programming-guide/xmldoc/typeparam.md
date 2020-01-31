---
title: <typeparam> — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 867ecacf58f95533395ded203a8f17bc92558ccf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793366"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam > (C# Przewodnik programowania)

## <a name="syntax"></a>Składnia

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a>Parametry

- `name`

  Nazwa parametru typu. Ujmij nazwę w znaki podwójnego cudzysłowu ("").

- `description`

  Opis parametru typu.

## <a name="remarks"></a>Uwagi

Tag `<typeparam>` powinien być używany w komentarzu dla typu ogólnego lub deklaracji metody, aby opisać parametr typu. Dodaj tag dla każdego parametru typu ogólnego typu lub metody.

Aby uzyskać więcej informacji, zobacz [Ogólne](../generics/index.md).

Tekst dla tagu `<typeparam>` będzie wyświetlany w technologii IntelliSense, Raport internetowy programu [Przeglądarka obiektów](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) komentarzy do kodu okna.

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../../language-reference/index.md)
- [C#Przewodnik programowania](../index.md)
- [Zalecane Tagi dla komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
