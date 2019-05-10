---
title: Niebezpieczny kod i wskaźniki - C# przewodnik programowania
ms.custom: seodec18
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
ms.openlocfilehash: 9f4e74e1e8fa71d1492a10162191822c1edfb635
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64608037"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Niebezpieczny kod i wskaźniki (Przewodnik programowania w języku C#)
Aby zachować bezpieczeństwo typów i zabezpieczeń, C# nie obsługuje arytmetyki wskaźnika domyślnie. Jednak przy użyciu [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) słów kluczowych, można zdefiniować niebezpieczny kontekst, w którym można użyć wskaźników. Aby uzyskać więcej informacji o wskaźnikach, zobacz temat [typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).  
  
> [!NOTE]
>  W środowisko uruchomieniowe języka wspólnego (CLR) niebezpieczny kod nazywa się zweryfikowanie kodu. Niebezpieczny kod w języku C# nie są zawsze niebezpieczne; jest po prostu kod bezpieczeństwa, którego nie można zweryfikować przez środowisko CLR. Środowisko CLR w związku z tym tylko wykona niebezpieczny kod jeśli znajduje się w zestawie całkowicie zaufanym. Jeśli używasz niebezpieczny kod, jest odpowiedzialny za zapewnienie, kod nie wprowadzają zagrożenia dla bezpieczeństwa lub wskaźnik błędów.  
  
## <a name="unsafe-code-overview"></a>Niebezpieczne przegląd kodu  
 Niebezpieczny kod ma następujące właściwości:  
  
- Metody, typy i bloków kodu mogą być definiowane jako niebezpieczny.  
  
- W niektórych przypadkach niebezpieczny kod może zwiększyć wydajność aplikacji, usuwając kontroli granice tablicy.  
  
- Niebezpieczny kod jest wymagany podczas wywoływania funkcji natywnych, które wymagają wskaźników.  
  
- Za pomocą niebezpieczny kod wprowadza zagrożenia bezpieczeństwa i stabilności.  
  
- W kolejności dla języka C# skompilować kod niebezpieczny, aplikacja musi być skompilowana przy użyciu [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Aby uzyskać więcej informacji, zobacz:  
  
- [Typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
- [Bufory o ustalonym rozmiarze](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
- [Instrukcje: Użycie wskaźników do kopiowania tablicy bajtów](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
