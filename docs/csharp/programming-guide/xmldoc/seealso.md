---
title: <seealso> - Przewodnik programowania C#
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
ms.openlocfilehash: e24d5910ab21f01aebb5a32ce7646cf56886a81a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093464"
---
# <a name="seealso-c-programming-guide"></a>\<seealso> (przewodnik programowania C#)

## <a name="syntax"></a>Składnia

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a>Parametry

- cref = `member`" "

  Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji. Kompilator sprawdza, czy istnieje `member` dany element kodu i przekazuje do nazwy elementu w wyjściowym pliku XML.`member` muszą znajdować się w cudzysłowie podwójnym (" ").

  Aby uzyskać informacje na temat tworzenia odwołania cref do typu ogólnego, zobacz [atrybut cref](./cref-attribute.md).

## <a name="remarks"></a>Uwagi

Znacznik \<seealso> umożliwia określenie tekstu, który może być wyświetlany w sekcji Zobacz też. Użyj [ \<>,](./see.md) aby określić łącze z poziomu tekstu.

Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

Zobacz [ \<podsumowanie>](./summary.md) przykład \<użyciem seealso>.

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
