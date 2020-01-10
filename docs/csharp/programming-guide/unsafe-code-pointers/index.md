---
title: Niebezpieczny kod i wskaźniki C# — Przewodnik programistyczny
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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711834"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Niebezpieczny kod i wskaźnikiC# (Przewodnik programowania)

Aby zachować bezpieczeństwo typów i zabezpieczenia, C# program nie obsługuje domyślnie arytmetycznego wskaźnika. Jednak za pomocą słowa kluczowego [UNSAFE](../../language-reference/keywords/unsafe.md) można zdefiniować niebezpieczny kontekst, w którym można używać wskaźników. Aby uzyskać więcej informacji na temat wskaźników, zobacz [typy wskaźnika](pointer-types.md).  
  
> [!NOTE]
> W środowisku uruchomieniowym języka wspólnego (CLR) kod niebezpieczny jest określany jako kod niemożliwy do zweryfikowania. Kod niebezpieczny C# w programie nie musi być niebezpieczny; jest to tylko kod, którego bezpieczeństwo nie może być zweryfikowane przez środowisko CLR. W związku z tym środowisko CLR wykona tylko niebezpieczny kod, jeśli znajduje się w w pełni zaufanym zestawie. Jeśli używasz niebezpiecznego kodu, jest odpowiedzialny za upewnienie się, że Twój kod nie wprowadza zagrożeń bezpieczeństwa lub błędy wskaźników.  
  
## <a name="unsafe-code-overview"></a>Przegląd niebezpiecznego kodu

Kod niebezpieczny ma następujące właściwości:

- Metody, typy i bloki kodu można definiować jako niebezpieczne.

- W niektórych przypadkach niebezpieczny kod może zwiększyć wydajność aplikacji przez usunięcie kontroli granic tablicy.

- Kod niebezpieczny jest wymagany po wywołaniu funkcji natywnych, które wymagają wskaźników.

- Użycie niebezpiecznego kodu wprowadza zagrożenia bezpieczeństwa i stabilności.

- Kod, który zawiera niebezpieczne bloki, musi być skompilowany przy użyciu opcji [niebezpiecznego](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilatora.
  
## <a name="related-sections"></a>Sekcje pokrewne

Aby uzyskać więcej informacji, zobacz:

- [Typy wskaźników](pointer-types.md)

- [Bufory o ustalonym rozmiarze](fixed-size-buffers.md)

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz temat dotyczący [niebezpiecznego kodu](~/_csharplang/spec/unsafe-code.md) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
