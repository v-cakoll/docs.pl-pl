---
title: Obsługa wyjątków — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: 895f561c15941d851980ea9b392d2e86db2462f3
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423287"
---
# <a name="exception-handling-c-programming-guide"></a>Obsługa wyjątków (Przewodnik programowania w języku C#)
Programista używa bloku try do partycjonowania kodu, który może mieć wpływ na wyjątek. [](../../language-reference/keywords/try-catch.md) C# Skojarzone bloki [catch](../../language-reference/keywords/try-catch.md) są używane do obsługi wszelkich wyjątków z wynikiem. Blok [finally](../../language-reference/keywords/try-finally.md) zawiera kod, który jest uruchamiany niezależnie od tego, czy wyjątek jest zgłaszany w bloku `try`, na przykład zwalniając zasoby, które są przydzieloną w bloku `try`. Blok `try` wymaga co najmniej jednego skojarzonego bloku `catch` lub bloku `finally` lub obu tych metod.  
  
 W poniższych przykładach pokazano instrukcję `try-catch`, instrukcję `try-finally` i instrukcję `try-catch-finally`.  
  
 [!code-csharp[csProgGuideExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#6)]  
  
 [!code-csharp[csProgGuideExceptions#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#7)]  
  
 [!code-csharp[csProgGuideExceptions#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#8)]  
  
 Blok `try` bez bloku `catch` lub `finally` powoduje błąd kompilatora.  
  
## <a name="catch-blocks"></a>Bloki catch  
 Blok `catch` może określać typ wyjątku do przechwycenia. Specyfikacja typu jest nazywana *filtrem wyjątków*. Typ wyjątku powinien pochodzić od <xref:System.Exception>. Ogólnie rzecz biorąc nie należy określać <xref:System.Exception> jako filtru wyjątków, chyba że wiesz, jak obsługiwać wszystkie wyjątki, które mogą być zgłaszane w bloku `try`, lub dołączono instrukcję [throw](../../language-reference/keywords/throw.md) na końcu bloku `catch`.  
  
 Wiele bloków `catch` z różnymi filtrami wyjątków można łączyć ze sobą. Bloki `catch` są oceniane z góry do dołu w kodzie, ale tylko jeden blok `catch` jest wykonywany dla każdego zgłoszonego wyjątku. Zostanie wykonany pierwszy blok `catch`, który określa typ dokładny lub Klasa bazowa zgłoszonego wyjątku. Jeśli żaden blok `catch` nie określa zgodnego filtru wyjątków, blok `catch`, który nie ma filtra jest zaznaczony, jeśli jeden jest obecny w instrukcji. Ważne jest, aby umieścić bloki `catch` z najbardziej szczegółowymi (najbardziej pochodnymi) typami wyjątków.  
  
 Wyjątki należy przechwytywać, gdy są spełnione następujące warunki:  
  
- Warto zapoznać się z tym, dlaczego wyjątek może być zgłaszany, i można zaimplementować konkretne odzyskiwanie, na przykład monitowanie użytkownika o wprowadzenie nowej nazwy pliku podczas przechwytywania obiektu <xref:System.IO.FileNotFoundException>.  
  
- Można utworzyć i zgłosić nowy, bardziej szczegółowy wyjątek.  
  
     [!code-csharp[csProgGuideExceptions#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#9)]  
  
- Chcesz częściowo obsłużyć wyjątek przed przekazaniem go do dodatkowej obsługi. W poniższym przykładzie blok `catch` jest używany do dodawania wpisu do dziennika błędów przed ponownym wygenerowaniem wyjątku.  
  
     [!code-csharp[csProgGuideExceptions#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#10)]  
  
## <a name="finally-blocks"></a>Bloki finally  
 Blok `finally` umożliwia czyszczenie akcji wykonywanych w bloku `try`. Jeśli jest obecny, blok `finally` jest wykonywany jako ostatni, po bloku `try` i dowolnych dopasowanych bloków `catch`. Blok `finally` jest zawsze uruchamiany, niezależnie od tego, czy wystąpił wyjątek, czy znaleziono blok `catch` pasujący do typu wyjątku.  
  
 Blok `finally` może służyć do zwalniania zasobów, takich jak strumienie plików, połączenia z bazami danych i uchwyty grafiki, bez oczekiwania na zakończenie działania modułu zbierającego elementy bezużyteczne w środowisku uruchomieniowym. Aby uzyskać więcej informacji, zobacz [używanie instrukcji using](../../language-reference/keywords/using-statement.md) .  
  
 W poniższym przykładzie blok `finally` jest używany do zamykania pliku, który jest otwierany w bloku `try`. Przed zamknięciem pliku należy zauważyć, że jego stan jest sprawdzany. Jeśli blok `try` nie może otworzyć pliku, dojście do pliku nadal ma wartość `null` a blok `finally` nie próbuje go zamknąć. Alternatywnie, jeśli plik zostanie pomyślnie otwarty w bloku `try`, blok `finally` zamknie otwarty plik.  
  
 [!code-csharp[csProgGuideExceptions#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#11)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [wyjątki](~/_csharplang/spec/exceptions.md) i [Instrukcje try](~/_csharplang/spec/statements.md#the-try-statement) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz także

- [C#Odwoła](../../language-reference/index.md)
- [Przewodnik programowania w języku C#](../index.md)
- [Wyjątki i obsługa wyjątków](./index.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [using, instrukcja](../../language-reference/keywords/using-statement.md)
