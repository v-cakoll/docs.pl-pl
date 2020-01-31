---
title: <permission> — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 14abb5bd181f401a4e6834d110e20fa920566580
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789734"
---
# <a name="permission-c-programming-guide"></a>> uprawnień \<(C# Przewodnik programowania)

## <a name="syntax"></a>Składnia

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a>Parametry

- cref = "`member`"

  Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji. Kompilator sprawdza, czy dany element kodu istnieje i tłumaczy `member` na nazwę elementu kanonicznego w wyjściowym kodzie XML. *składowa* musi znajdować się w podwójnym cudzysłowie ("").

  Aby uzyskać informacje na temat sposobu tworzenia odwołania cref do typu ogólnego, zobacz [\<see >](./see.md).

- `description`

  Opis dostępu do elementu członkowskiego.

## <a name="remarks"></a>Uwagi

Tag > uprawnień \<umożliwia dokumentowanie dostępu do elementu członkowskiego. Klasa <xref:System.Security.PermissionSet> pozwala określić dostęp do elementu członkowskiego.

Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a>Zobacz także

- [C#Przewodnik programowania](../index.md)
- [Zalecane Tagi dla komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
