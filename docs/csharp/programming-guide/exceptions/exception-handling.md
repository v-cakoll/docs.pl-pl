---
title: Obsługa wyjątków — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: 87a85511669e676f2943bf5f079b54e96b926490
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680561"
---
# <a name="exception-handling-c-programming-guide"></a>Obsługa wyjątków (Przewodnik programowania w języku C#)
A [spróbuj](../../../csharp/language-reference/keywords/try-catch.md) blok jest używany przez programistów C# do kodu partycji, który może mieć wpływ wyjątku. Skojarzone [catch](../../../csharp/language-reference/keywords/try-catch.md) bloki są używane do obsługi wszystkich wyjątków wynikowe. A [na koniec](../../../csharp/language-reference/keywords/try-finally.md) blok zawiera kod, który jest wykonywany niezależnie od tego, czy wyjątek jest zgłaszany w `try` bloku, np. przy zwalnianiu zasobów, które są przydzielane w `try` bloku. A `try` bloku wymaga co najmniej jednym skojarzone `catch` bloków lub `finally` bloku i / lub.  
  
 W poniższych przykładach pokazano `try-catch` instrukcji `try-finally` instrukcji, a `try-catch-finally` instrukcji.  
  
 [!code-csharp[csProgGuideExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#6)]  
  
 [!code-csharp[csProgGuideExceptions#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#7)]  
  
 [!code-csharp[csProgGuideExceptions#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#8)]  
  
 A `try` block bez `catch` lub `finally` bloku powoduje błąd kompilatora.  
  
## <a name="catch-blocks"></a>Bloki catch  
 A `catch` bloku można określić typ wyjątku do przechwytywania. Specyfikacja typu jest nazywany *filtra wyjątku*. Typ wyjątku powinien pochodzić od <xref:System.Exception>. Ogólnie rzecz biorąc, nie określaj <xref:System.Exception> jako wyjątek filtr, chyba że albo wiesz, jak obsługiwać wszystkie wyjątki, które mogą być generowane w `try` bloku lub wprowadzono [throw](../../../csharp/language-reference/keywords/throw.md) instrukcji na końcu Twojej `catch`bloku.  
  
 Wiele `catch` bloki inny wyjątek filtry można łączyć w łańcuch. `catch` Są obliczane bloki, od góry do dołu w kodzie, ale tylko jeden `catch` blok jest wykonywany dla każdego wyjątku, który jest generowany. Pierwszy `catch` jest wykonywany blok, który określa dokładnie tego samego typu lub klasę bazową zgłoszony wyjątek. Jeśli nie `catch` bloku określa zgodne z filtrem wyjątku, `catch` blok, który nie ma filtru jest zaznaczone, jeśli jest obecna w instrukcji. Ważne jest, aby umieścić `catch` bloki z najbardziej (oznacza to, najbardziej pochodnej) dla określonego wyjątku typy najpierw.  
  
 Należy przechwytywać wyjątki, gdy są spełnione następujące warunki:  
  
- Masz dobry zrozumieć Dlaczego wyjątku może zostać zgłoszone, a można zaimplementować określonego odzyskiwania, taką jak monitowanie użytkownika o wprowadzenie nową nazwę pliku, jeśli przechwytujesz <xref:System.IO.FileNotFoundException> obiektu.  
  
- Można tworzyć i wyjątku nowe, bardziej szczegółowe.  
  
     [!code-csharp[csProgGuideExceptions#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#9)]  
  
- Chcesz częściowo obsługi wyjątku przed przekazaniem go celu obsługi dodatkowych. W poniższym przykładzie `catch` blok jest używany, aby dodać wpis do dziennika błędów przed ponownego zgłaszania wyjątku.  
  
     [!code-csharp[csProgGuideExceptions#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#10)]  
  
## <a name="finally-blocks"></a>Bloki finally  
 A `finally` bloku pozwala na czyszczenie akcje, które są wykonywane w `try` bloku. Jeśli jest obecny, `finally` blok jest wykonywany po ostatniej, `try` blok i wszystkie dopasowane `catch` bloku. A `finally` bloku zawsze działa, niezależnie od tego, czy wyjątek jest zgłaszany lub `catch` znajduje się blok odpowiadał typowi wyjątku.  
  
 `finally` Bloku pozwala zwolnić zasoby, takie jak strumienie plików, połączenia z bazą danych i grafiki obsługuje bez oczekiwania na moduł odśmiecania pamięci w środowisku uruchomieniowym, aby zakończyć obiektów. Zobacz [za pomocą instrukcji](../../../csharp/language-reference/keywords/using-statement.md) Aby uzyskać więcej informacji.  
  
 W poniższym przykładzie `finally` blok jest używany do zamknięcia pliku, który jest otwierany w `try` bloku. Należy zauważyć, że stan dojście do pliku jest zaznaczone, przed zamknięciem pliku. Jeśli `try` bloku nie można otworzyć pliku, uchwyt pliku nadal ma wartość `null` i `finally` bloku nie podejmuje próby zamknij go. Alternatywnie Jeśli plik jest otwarty pomyślne `try` bloku, `finally` bloku Zamyka otwarty plik.  
  
 [!code-csharp[csProgGuideExceptions#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#11)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [wyjątki](~/_csharplang/spec/exceptions.md) i [instrukcjami "try"](~/_csharplang/spec/statements.md#the-try-statement) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Wyjątki i obsługa wyjątków](../../../csharp/programming-guide/exceptions/index.md)
- [try-catch](../../../csharp/language-reference/keywords/try-catch.md)
- [try-finally](../../../csharp/language-reference/keywords/try-finally.md)
- [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)
- [using, instrukcja](../../../csharp/language-reference/keywords/using-statement.md)
