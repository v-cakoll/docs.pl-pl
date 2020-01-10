---
title: Jak obsłużyć wyjątek przy użyciu przewodnika try C# -catch-programowanie
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: adfc53cbe4fd603ac3a6de6b9a0162320d5a2e19
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712289"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Jak obsłużyć wyjątek za pomocą try/catchC# (Przewodnik programowania)
Celem bloku [try-catch](../../language-reference/keywords/try-catch.md) jest przechwycenie i obsłużenie wyjątku wygenerowanego przez kod roboczy. Niektóre wyjątki mogą być obsługiwane w bloku `catch` i problem rozwiązany bez ponownego zgłaszania wyjątku; Jednak w większości przypadków Jedyną czynnością, którą można wykonać, jest upewnienie się, że jest zgłaszany odpowiedni wyjątek.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie <xref:System.IndexOutOfRangeException> nie jest najbardziej odpowiedni wyjątek: <xref:System.ArgumentOutOfRangeException> ma sens dla metody, ponieważ błąd jest spowodowany przez argument `index` przekazaną przez wywołującego.  
  
 [!code-csharp[csProgGuideExceptions#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#5)]  
  
## <a name="comments"></a>Komentarze  
 Kod, który powoduje wyjątek, jest ujęty w bloku `try`. Instrukcja `catch` jest dodawana natychmiast po `IndexOutOfRangeException`do obsługi, jeśli wystąpi. Blok `catch` obsługuje `IndexOutOfRangeException` i zgłasza zamiast tego bardziej odpowiedni wyjątek `ArgumentOutOfRangeException`. Aby zapewnić wywołującemu możliwie jak najwięcej informacji, rozważ określenie oryginalnego wyjątku jako <xref:System.Exception.InnerException%2A> nowego wyjątku. Ponieważ właściwość <xref:System.Exception.InnerException%2A> jest [tylko do odczytu](../../language-reference/keywords/readonly.md), należy przypisać ją w konstruktorze nowego wyjątku.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Wyjątki i obsługa wyjątków](./index.md)
- [Obsługa wyjątków](./exception-handling.md)
