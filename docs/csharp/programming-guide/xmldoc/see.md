---
title: <see> — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 17d1d344b9a27ffd4995fa4849ee6d5ce7f90f29
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789703"
---
# <a name="see-c-programming-guide"></a>\<Zobacz > (C# Przewodnik programowania)

## <a name="syntax"></a>Składnia

```xml
<see cref="member"/>
```

## <a name="parameters"></a>Parametry

- cref = "`member`"

  Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji. Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w wyjściowym kodzie XML. Umieść *składową* w podwójnym cudzysłowie ("").

## <a name="remarks"></a>Uwagi

\<Zobacz > tag pozwala określić łącze z poziomu tekstu. Użyj [\<seealso — >](./seealso.md) , aby wskazać, że tekst powinien być umieszczony w sekcji Zobacz też. Użyj [atrybutu cref](./cref-attribute.md) , aby utworzyć wewnętrzne hiperłącza do stron dokumentacji dla elementów kodu.

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

W poniższym przykładzie pokazano \<Zobacz tag > w sekcji podsumowania.

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a>Zobacz także

- [C#Przewodnik programowania](../index.md)
- [Zalecane Tagi dla komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
