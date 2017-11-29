---
title: "Porady: użycie wskaźników do kopiowania tablicy bajtów (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.assetid: ec16fbb4-a24e-45f5-a763-9499d3fabe0a
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 375cab76063e4c77515d6b05b42f2d97ff3efc44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a>Porady: użycie wskaźników do kopiowania tablicy bajtów (Przewodnik programowania w języku C#)
W poniższym przykładzie użyto wskaźników do skopiowania do innej tablicy bajtów.  
  
 W tym przykładzie użyto [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) — słowo kluczowe, co pozwala na użycie wskaźników w `Copy` metody. [Stałej](../../../csharp/language-reference/keywords/fixed-statement.md) instrukcji służy do deklarowania wskaźniki do tablic źródłowym i docelowym. To *numerów PIN* lokalizacja źródłowa i docelowa stałych w pamięci, dzięki czemu nie będą przenoszone przez wyrzucanie elementów bezużytecznych. Bloki pamięci dla tablic są odpiąć, gdy `fixed` bloku zostało zakończone. Ponieważ `Copy` używa metody w tym przykładzie `unsafe` — słowo kluczowe, jego musi być kompilowana przy użyciu **/ unsafe** — opcja kompilatora. Ustawianie opcji w programie Visual Studio, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **właściwości**. Na **kompilacji** wybierz opcję **niebezpiecznego kodu**.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_2.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [/ unsafe (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)  
 [Wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/index.md)
