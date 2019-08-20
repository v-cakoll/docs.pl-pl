---
title: 'Instrukcje: Obsługa wyjątku przy użyciu przewodnika try- C# catch-programowanie'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: 5378de09962055fe7d2e100484ad69662c803e0f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590237"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Instrukcje: Obsługuj wyjątek za pomocą try/catch (C# Przewodnik programowania)
Celem bloku [try-catch](../../language-reference/keywords/try-catch.md) jest przechwycenie i obsłużenie wyjątku wygenerowanego przez kod roboczy. Niektóre wyjątki mogą być obsługiwane w `catch` bloku i problem został rozwiązany bez ponownego zgłaszania wyjątku; jednak częściej, którą można wykonać, jest upewnienie się, że jest zgłaszany odpowiedni wyjątek.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie <xref:System.IndexOutOfRangeException> nie jest to najbardziej odpowiedni wyjątek: <xref:System.ArgumentOutOfRangeException> jest to bardziej zrozumiałe dla metody, ponieważ błąd jest spowodowany przez `index` argument, który został przesłany przez obiekt wywołujący.  
  
 [!code-csharp[csProgGuideExceptions#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#5)]  
  
## <a name="comments"></a>Komentarze  
 Kod, który powoduje, że wyjątek jest ujęty `try` w bloku. Instrukcja jest dodawana natychmiast po do dojścia `IndexOutOfRangeException`, jeśli wystąpi. `catch` Blok obsługuje i zgłasza zamiast niego bardziej odpowiedni `ArgumentOutOfRangeException` wyjątek. `IndexOutOfRangeException` `catch` Aby zapewnić wywołującemu możliwie jak najwięcej informacji, rozważ określenie oryginalnego wyjątku jako <xref:System.Exception.InnerException%2A> nowego wyjątku. Ponieważ właściwość jest tylko do odczytu, należy przypisać ją w konstruktorze nowego wyjątku. [](../../language-reference/keywords/readonly.md) <xref:System.Exception.InnerException%2A>  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Wyjątki i obsługa wyjątków](./index.md)
- [Obsługa wyjątków](./exception-handling.md)
