---
title: <see>- Przewodnik programowania C#
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
ms.openlocfilehash: f4834f88c646b44269f8290c2ad08698c34e714a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627675"
---
# <a name="see-c-programming-guide"></a>\<zobacz> (przewodnik programowania Języka C#)

## <a name="syntax"></a>Składnia

```xml
<see cref="member"/>
```

## <a name="parameters"></a>Parametry

- cref =`member`" "

  Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji. Kompilator sprawdza, czy istnieje `member` dany element kodu i przekazuje do nazwy elementu w wyjściowym pliku XML. Umieść *element członkowski* w cudzysłowie podwójnym (" ").

## <a name="remarks"></a>Uwagi

Znacznik \<> zobacz umożliwia określenie łącza z poziomu tekstu. Użyj [ \<seealso>,](./seealso.md) aby wskazać, że tekst powinien być umieszczony w sekcji Zobacz też. Użyj [atrybutu cref,](./cref-attribute.md) aby utworzyć wewnętrzne hiperłącza do stron dokumentacji dla elementów kodu.

Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.

W poniższym \<przykładzie przedstawiono znacznik> w sekcji podsumowania.

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
