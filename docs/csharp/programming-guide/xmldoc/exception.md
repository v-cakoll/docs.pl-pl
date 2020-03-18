---
title: <exception>- Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 14318ac0b0cdf781d0488eecaf934879017d91f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789802"
---
# <a name="exception-c-programming-guide"></a>\<wyjątek> (przewodnik programowania C#)

## <a name="syntax"></a>Składnia

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a>Parametry

- cref = `member`" "

  Odwołanie do wyjątku, który jest dostępny z bieżącego środowiska kompilacji. Kompilator sprawdza, czy dany `member` wyjątek istnieje i przekłada się na nazwę elementu kanonicznego w wyjściowym pliku XML. `member`muszą znajdować się w cudzysłowie podwójnym (" ").

  Aby uzyskać więcej informacji `member` na temat formatowania w celu odwoływania się do typu ogólnego, zobacz [Przetwarzanie pliku XML](processing-the-xml-file.md).

- `description`

  Opis wyjątku.

## <a name="remarks"></a>Uwagi

Znacznik \<> wyjątku pozwala określić, które wyjątki mogą być generowane. Ten tag można zastosować do definicji metod, właściwości, zdarzeń i indeksatorów.

Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.

Aby uzyskać więcej informacji na temat obsługi [wyjątków, zobacz Wyjątki i obsługa wyjątków](../exceptions/index.md).

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](recommended-tags-for-documentation-comments.md)
