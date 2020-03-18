---
title: Niebezpieczny kod i wskaźniki — przewodnik programowania języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: 013af4e55c8fc396bbc92058d7fb454484f3263e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711834"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Niebezpieczny kod i wskaźniki (Przewodnik programowania C#)

Aby zachować bezpieczeństwo typów i zabezpieczeń, C# nie obsługuje wskaźnik arytmetyczny, domyślnie. Jednak za pomocą [niebezpiecznego](../../language-reference/keywords/unsafe.md) słowa kluczowego można zdefiniować niebezpieczny kontekst, w którym można używać wskaźników. Aby uzyskać więcej informacji o wskaźnikach, zobacz [Typy wskaźników](pointer-types.md).  
  
> [!NOTE]
> W czasie wykonywania języka wspólnego (CLR) niebezpieczny kod jest określany jako kod nieweryfikowalny. Niebezpieczny kod w języku C# niekoniecznie jest niebezpieczne; jest to tylko kod, którego bezpieczeństwo nie może być zweryfikowane przez CLR. W związku z tym clr będzie wykonywać niebezpieczny kod tylko wtedy, gdy znajduje się w pełni zaufanym zestawie. Jeśli używasz niebezpiecznego kodu, to jest twoim obowiązkiem, aby upewnić się, że kod nie wprowadza zagrożenia bezpieczeństwa lub błędy wskaźnika.  
  
## <a name="unsafe-code-overview"></a>Omówienie niebezpiecznego kodu

Niebezpieczny kod ma następujące właściwości:

- Metody, typy i bloki kodu można zdefiniować jako niebezpieczne.

- W niektórych przypadkach niebezpieczny kod może zwiększyć wydajność aplikacji, usuwając kontrole granic tablicy.

- Niebezpieczny kod jest wymagany podczas wywoływania funkcji macierzystych, które wymagają wskaźników.

- Używanie niebezpiecznego kodu wprowadza zagrożenia bezpieczeństwa i stabilności.

- Kod, który zawiera niebezpieczne bloki muszą być skompilowane z [opcją kompilatora -niebezpieczne.](../../language-reference/compiler-options/unsafe-compiler-option.md)
  
## <a name="related-sections"></a>Sekcje pokrewne

Aby uzyskać więcej informacji, zobacz:

- [Typy wskaźnika](pointer-types.md)

- [Bufory o ustalonym rozmiarze](fixed-size-buffers.md)

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz temat [Niebezpieczny kod](~/_csharplang/spec/unsafe-code.md) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
