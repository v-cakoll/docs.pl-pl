---
title: <exception> — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 14318ac0b0cdf781d0488eecaf934879017d91f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789802"
---
# <a name="exception-c-programming-guide"></a>\<> wyjątków (C# Przewodnik programowania)

## <a name="syntax"></a>Składnia

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a>Parametry

- cref = "`member`"

  Odwołanie do wyjątku, które jest dostępne w bieżącym środowisku kompilacji. Kompilator sprawdza, czy dany wyjątek istnieje i tłumaczy `member` na nazwę elementu kanonicznego w wyjściowym kodzie XML. `member` musi znajdować się w podwójnym cudzysłowie ("").

  Aby uzyskać więcej informacji na temat sposobu formatowania `member` w celu odwoływania się do typu ogólnego, zobacz [przetwarzanie pliku XML](processing-the-xml-file.md).

- `description`

  Opis wyjątku.

## <a name="remarks"></a>Uwagi

Tag \<Exception > pozwala określić, które wyjątki mogą być zgłaszane. Ten tag można zastosować do definicji metod, właściwości, zdarzeń i indeksatorów.

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz [wyjątki i obsługa wyjątków](../exceptions/index.md).

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a>Zobacz także

- [C#Przewodnik programowania](../index.md)
- [Zalecane Tagi dla komentarzy dokumentacji](recommended-tags-for-documentation-comments.md)
