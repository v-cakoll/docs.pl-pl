---
title: <see>— Przewodnik programowania w języku C#
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
ms.openlocfilehash: 0f10feb0931c6d38c817fdecb925f68d439abb59
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287249"
---
# <a name="see-c-programming-guide"></a>\<see>(Przewodnik programowania w języku C#)

## <a name="syntax"></a>Składnia

```xml
<see cref="member"/>
```

## <a name="parameters"></a>Parametry

- cref = " `member` "

  Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji. Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w wyjściowym kodzie XML. Umieść *składową* w podwójnym cudzysłowie ("").

## <a name="remarks"></a>Uwagi

`<see>`Tag pozwala określić łącze z poziomu tekstu. Użyj [\<seealso>](./seealso.md) , aby wskazać, że tekst powinien być umieszczony w sekcji Zobacz też. Użyj [atrybutu cref](./cref-attribute.md) , aby utworzyć wewnętrzne hiperłącza do stron dokumentacji dla elementów kodu.

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

W poniższym przykładzie pokazano `<see>` tag w sekcji podsumowania.

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
