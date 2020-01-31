---
title: <param> — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d16070a82531519dd276b2ea999623017769d716
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789756"
---
# <a name="param-c-programming-guide"></a>\<param > (C# Przewodnik programowania)

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

Tag \<param > należy użyć w komentarzu dla deklaracji metody, aby opisać jeden z parametrów dla metody. Aby udokumentować wiele parametrów, Użyj wielu tagów \<param >.

Tekst dla tagu \<param > zostanie wyświetlony w IntelliSense, Przeglądarka obiektów i w raporcie w sieci Web komentarza do kodu.

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a>Zobacz także

- [C#Przewodnik programowania](../index.md)
- [Zalecane Tagi dla komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
