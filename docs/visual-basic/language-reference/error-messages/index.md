---
title: komunikaty o błędach
ms.date: 07/20/2015
helpviewer_keywords:
- errors [Visual Basic]
- error messages
- trappable errors
- errors [Visual Basic], trappable
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
ms.openlocfilehash: c2d9974f41efdd321af800e6270586d9b18ba6f7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402852"
---
# <a name="error-messages-visual-basic"></a>Komunikaty o błędach (Visual Basic)
Podczas pisania, kompilowania lub uruchamiania aplikacji Visual Basic mogą wystąpić następujące typy błędów:  
  
1. Błędy czasu projektowania, które występują podczas pisania aplikacji w programie Visual Studio.  
  
2. Błędy czasu kompilacji, które występują podczas kompilowania aplikacji w programie Visual Studio lub w wierszu polecenia.  
  
3. Błędy czasu wykonywania, które występują podczas uruchamiania aplikacji w programie Visual Studio lub jako autonomiczny plik wykonywalny.  
  
 Informacje o sposobach rozwiązywania określonego błędu znajdują się w temacie [dodatkowe zasoby dla programistów Visual Basic](../../getting-started/additional-resources.md).  
  
## <a name="run-time-errors"></a>Błędy czasu wykonywania  
 Jeśli aplikacja Visual Basic próbuje wykonać akcję, której system nie może wykonać, wystąpi błąd w czasie wykonywania i Visual Basic zgłasza `Exception` obiekt. Visual Basic może generować niestandardowe błędy dowolnego typu danych, łącznie z `Exception` obiektami, za pomocą `Throw` instrukcji. Aplikacja może zidentyfikować błąd, wyświetlając numer błędu i komunikat przechwyconego wyjątku. Jeśli błąd nie zostanie przechwycony, aplikacja zostanie zakończona.  
  
 Kod może Zalewka i sprawdzanie błędów czasu wykonywania. Jeśli zamieścisz kod, który generuje błąd w `Try` bloku, możesz przechwytywać wszystkie zgłoszone błędy w obrębie zgodnego `Catch` bloku. Aby dowiedzieć się, jak zalewkować błędy w czasie wykonywania i odpowiadać na nie w kodzie, zobacz [try... Catch... Finally — instrukcja](../statements/try-catch-finally-statement.md).  
  
## <a name="compile-time-errors"></a>Błędy kompilacji  
 Jeśli kompilator Visual Basic napotyka problem w kodzie, wystąpi błąd czasu kompilacji. W edytorze kodu można łatwo określić, który wiersz kodu spowodował błąd, ponieważ linia falista pojawia się pod tym wierszem kodu. Komunikat o błędzie jest wyświetlany, gdy użytkownik wskaże podkreślenie faliste lub otworzy **Lista błędów**, w którym znajdują się również inne komunikaty.  
  
 Jeśli identyfikator ma podkreśloną falistą, a krótka podkreślenie pojawia się pod znakiem po prawej stronie, można wygenerować element zastępczy dla klasy, konstruktora, metody, właściwości, pola lub wyliczenia. Aby uzyskać więcej informacji, zobacz [generowanie na podstawie użycia](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).
  
 Rozwiązując ostrzeżenia z kompilatora Visual Basic, może być możliwe napisanie kodu, który działa szybciej i ma mniejszą liczbę błędów. Te ostrzeżenia identyfikują kod, który może spowodować błędy podczas uruchamiania aplikacji. Na przykład kompilator ostrzega w przypadku próby wywołania elementu członkowskiego nieprzypisanej zmiennej obiektu, powrotu z funkcji bez ustawiania wartości zwracanej lub wykonywania `Try` bloku z błędami w logice, aby przechwytywać wyjątki. Aby uzyskać więcej informacji na temat ostrzeżeń, w tym sposobu ich włączania i wyłączania, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).
