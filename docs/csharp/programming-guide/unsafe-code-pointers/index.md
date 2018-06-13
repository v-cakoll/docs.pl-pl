---
title: Niebezpieczny kod i wskaźniki (Przewodnik programowania w języku C#)
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
ms.openlocfilehash: b57a6f607dbdbc84c60889a5ce2b1e3c33d7f435
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331607"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Niebezpieczny kod i wskaźniki (Przewodnik programowania w języku C#)
Aby zachować bezpieczeństwo typów i zabezpieczeń, C# nie obsługuje arytmetyki wskaźnika domyślnie. Jednak przy użyciu [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) — słowo kluczowe, można zdefiniować niebezpiecznym kontekście, w którym można wskaźników. Aby uzyskać więcej informacji na temat wskaźników, zobacz temat [typów wskaźnikowych](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).  
  
> [!NOTE]
>  W środowisko uruchomieniowe języka wspólnego (CLR) niebezpieczny kod jest określana jako kod niemożliwy do zweryfikowania. Niebezpieczny kod w języku C# nie jest zawsze niebezpieczne; jest tylko kod bezpieczeństwa, którego nie można zweryfikować przez środowisko CLR. Środowisko CLR w związku z tym tylko wykona niebezpieczny kod, jeśli jest w pełni zaufanym zestawem. Jeśli używasz niebezpieczny kod jest obowiązek upewnij się, że kodu nie wprowadzają zagrożeniem bezpieczeństwa lub wskaźnik błędów.  
  
## <a name="unsafe-code-overview"></a>Niebezpieczne przegląd kodu  
 Niebezpieczny kod ma następujące właściwości:  
  
-   Metody, typy i bloki kodu mogą być definiowane jako niebezpieczny.  
  
-   W niektórych przypadkach niebezpieczny kod może zwiększyć wydajność aplikacji, usuwając kontroli granice tablicy.  
  
-   Niebezpieczny kod jest wymagany, gdy wywoływać funkcje natywne, które wymagają wskaźników.  
  
-   Przy użyciu niebezpieczny kod wprowadza zagrożenia bezpieczeństwa i stabilności.  
  
-   Aby C# skompilować kod niezabezpieczony, aplikacja musi być kompilowana przy użyciu [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
-   [Bufory o ustalonym rozmiarze](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
-   [Porady: użycie wskaźników do kopiowania tablicy bajtów](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
-   [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
