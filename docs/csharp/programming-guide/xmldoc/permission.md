---
title: <permission> - Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 4f76d28d5531c1b9f01fa950589407934cc1244a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093477"
---
# <a name="permission-c-programming-guide"></a>\<> uprawnień (przewodnik programowania C#)

## <a name="syntax"></a>Składnia

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a>Parametry

- cref = `member`" "

  Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji. Kompilator sprawdza, czy istnieje dany element kodu i tłumaczy `member` się na nazwę elementu kanonicznego w wyjściowym pliku XML. *element członkowski* musi znajdować się w cudzysłowie podwójnym (" ").

  Aby uzyskać informacje na temat tworzenia odwołania cref do typu ogólnego, zobacz [atrybut cref](./cref-attribute.md).

- `description`

  Opis dostępu do elementu członkowskiego.

## <a name="remarks"></a>Uwagi

Uprawnienie \<> tag umożliwia dokumentowanie dostępu członka. Klasa <xref:System.Security.PermissionSet> umożliwia określenie dostępu do elementu członkowskiego.

Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
