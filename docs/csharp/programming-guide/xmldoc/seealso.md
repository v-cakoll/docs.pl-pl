---
title: <seealso> — Przewodnik programowania w języku C#
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: 1b801ac1b5a0a59d97ccc35ec78930d99223e846
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287223"
---
# <a name="seealso-c-programming-guide"></a>\<seealso>(Przewodnik programowania w języku C#)

## <a name="syntax"></a>Składnia

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a>Parametry

- cref = " `member` "

  Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji. Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w wyjściowym kodzie XML.`member` musi znajdować się w podwójnym cudzysłowie ("").

  Aby uzyskać informacje na temat sposobu tworzenia odwołania cref do typu ogólnego, zobacz [atrybut cref](./cref-attribute.md).

## <a name="remarks"></a>Uwagi

`<seealso>`Tag pozwala określić tekst, który może być wyświetlany w sekcji Zobacz też. Służy [\<see>](./see.md) do określania linku w tekście.

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

Zobacz [\<summary>](./summary.md) , aby zobaczyć przykład użycia \<seealso> .

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
