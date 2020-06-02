---
title: <param> — Przewodnik programowania w języku C#
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 396ed716c246091a674268020261069f36dd2be8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287327"
---
# <a name="param-c-programming-guide"></a>\<param>(Przewodnik programowania w języku C#)

## <a name="syntax"></a>Składnia

```xml
<param name="name">description</param>
```

## <a name="parameters"></a>Parametry

- `name`

  Nazwa parametru metody. Ujmij nazwę w znaki podwójnego cudzysłowu ("").

- `description`

  Opis parametru.

## <a name="remarks"></a>Uwagi

`<param>`Tag powinien być używany w komentarzu dla deklaracji metody, aby opisać jeden z parametrów dla metody. Aby udokumentować wiele parametrów, Użyj wielu `<param>` tagów.

Tekst `<param>` znacznika jest wyświetlany w obszarze IntelliSense, Przeglądarka obiektów i raport sieci Web komentarza do kodu.

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
