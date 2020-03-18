---
title: Jak obsługiwać wyjątek za pomocą try-catch - C# Programming Guide
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: adfc53cbe4fd603ac3a6de6b9a0162320d5a2e19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712289"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Jak obsługiwać wyjątek przy użyciu try/catch (Przewodnik programowania C#)
Celem bloku [try-catch](../../language-reference/keywords/try-catch.md) jest catch i obsługi wyjątku generowanego przez kod roboczy. Niektóre wyjątki mogą być `catch` obsługiwane w bloku i problem rozwiązany bez ponownego wystąpienia wyjątku; jednak częściej jedyną rzeczą, którą możesz zrobić, to upewnić się, że zostanie zgłoszony odpowiedni wyjątek.  
  
## <a name="example"></a>Przykład  
 W tym <xref:System.IndexOutOfRangeException> przykładzie nie jest najbardziej <xref:System.ArgumentOutOfRangeException> odpowiedni wyjątek: ma większy sens dla `index` metody, ponieważ błąd jest spowodowany przez argument przekazany przez obiekt wywołujący.  
  
 [!code-csharp[csProgGuideExceptions#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#5)]  
  
## <a name="comments"></a>Komentarze  
 Kod, który powoduje wyjątek jest `try` ujęty w bloku. Instrukcja `catch` jest dodawana natychmiast po obsłudze `IndexOutOfRangeException`, jeśli występuje. Blok `catch` obsługuje `IndexOutOfRangeException` i zgłasza bardziej odpowiedni `ArgumentOutOfRangeException` wyjątek zamiast tego. Aby zapewnić obiekt wywołujący z jak najwięcej informacji, jak to <xref:System.Exception.InnerException%2A> możliwe, należy rozważyć określenie oryginalnego wyjątku jako nowego wyjątku. Ponieważ <xref:System.Exception.InnerException%2A> właściwość jest [tylko do odczytu](../../language-reference/keywords/readonly.md), należy przypisać go w konstruktorze nowego wyjątku.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Wyjątki i obsługa wyjątków](./index.md)
- [Obsługa wyjątków](./exception-handling.md)
