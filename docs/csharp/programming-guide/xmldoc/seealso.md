---
title: <seealso> — C# Przewodnik programowania
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
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093464"
---
# <a name="seealso-c-programming-guide"></a>\<seealso — > (C# Przewodnik programowania)

## <a name="syntax"></a>Składnia

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a>Parametry

- cref = "`member`"

  Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji. Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w wyjściowym kodzie XML.`member` musi znajdować się w podwójnym cudzysłowie ("").

  Aby uzyskać informacje na temat sposobu tworzenia odwołania cref do typu ogólnego, zobacz [atrybut cref](./cref-attribute.md).

## <a name="remarks"></a>Uwagi

Tag \<seealso — > umożliwia określenie tekstu, który ma być wyświetlany w sekcji Zobacz też. Użyj [\<zobacz >](./see.md) , aby określić łącze z tekstu.

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

Zobacz [\<podsumowanie >](./summary.md) , aby uzyskać przykład użycia \<seealso — >.

## <a name="see-also"></a>Zobacz też

- [C#Przewodnik programowania](../index.md)
- [Zalecane Tagi dla komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
