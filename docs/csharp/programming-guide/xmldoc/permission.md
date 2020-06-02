---
title: <permission> — Przewodnik programowania w języku C#
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: bb7172042f0b472d03c3fa2d9dbd0d4d4265076b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287275"
---
# <a name="permission-c-programming-guide"></a>\<permission>(Przewodnik programowania w języku C#)

## <a name="syntax"></a>Składnia

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a>Parametry

- cref = " `member` "

  Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji. Kompilator sprawdza, czy dany element kodu istnieje i tłumaczy `member` na nazwę elementu kanonicznego w wyjściowym kodzie XML. *składowa* musi znajdować się w podwójnym cudzysłowie ("").

  Aby uzyskać informacje na temat sposobu tworzenia odwołania cref do typu ogólnego, zobacz [atrybut cref](./cref-attribute.md).

- `description`

  Opis dostępu do elementu członkowskiego.

## <a name="remarks"></a>Uwagi

`<permission>`Tag umożliwia dokumentowanie dostępu do elementu członkowskiego. <xref:System.Security.PermissionSet>Klasa pozwala określić dostęp do elementu członkowskiego.

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
