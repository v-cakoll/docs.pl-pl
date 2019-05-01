---
title: Komunikaty o błędach (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- errors [Visual Basic]
- error messages
- trappable errors
- errors [Visual Basic], trappable
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
ms.openlocfilehash: 822c0f266e7dd68f063043d98a9f4af308ae93fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013819"
---
# <a name="error-messages-visual-basic"></a>Komunikaty o błędach (Visual Basic)
Podczas pisania, kompilacji lub uruchamiania aplikacji w języku Visual Basic mogą wystąpić następujące błędy:  
  
1. Błędy czasu projektowania, które występują, gdy napisać aplikację w programie Visual Studio.  
  
2. Błędy kompilacji, które występują, gdy kompilujesz aplikację w programie Visual Studio lub w wierszu polecenia.  
  
3. Błędy środowiska wykonawczego, które występują podczas uruchamiania aplikacji w programie Visual Studio lub jako autonomicznego pliku wykonywalnego.  
  
 Aby dowiedzieć się, jak rozwiązywać problemy z określonego błędu, zobacz [zasoby dodatkowe dla programistów Visual Basic](../../../visual-basic/getting-started/additional-resources.md).  
  
## <a name="run-time-errors"></a>Błędy wykonania  
 Jeśli aplikacji Visual Basic podejmie próbę wykonania działania, które system nie może wykonać, wystąpi błąd czasu wykonywania i Visual Basic zgłasza `Exception` obiektu. Visual Basic mogą generować błędy niestandardowe wszelkich danych typu, w tym `Exception` obiektów przy użyciu `Throw` instrukcji. Aplikację można zidentyfikować ten błąd, wyświetlając numer błędu i komunikacie przechwycony wyjątek. Jeśli nie jest przechwycony błąd, kończy się aplikacja.  
  
 Kod można pułapek i zbadaj błędy czasu wykonywania. Jeśli uwzględnisz kod, który generuje błąd w `Try` bloku, można przechwytywać wszelkie zgłoszonego błędu, w ramach odpowiadającego `Catch` bloku. Aby uzyskać informacje na temat wyłapuje błędy w czasie wykonywania i Reaguj na nie w kodzie, zobacz [spróbuj... CATCH... Na koniec instrukcji](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="compile-time-errors"></a>Błędy czasu kompilacji  
 Jeśli kompilator Visual Basic napotyka problem w kodzie, wystąpi błąd kompilacji. W edytorze kodu można łatwo zidentyfikować która linia kodu spowodowały błąd, ponieważ linia falista jest wyświetlany w obszarze wiersza kodu. Komunikat o błędzie jest wyświetlany, jeśli albo wskaż faliste podkreślenie lub Otwórz **lista błędów**, które wyświetla również inne komunikaty.  
  
 Jeśli identyfikator ma linią falistą i krótki podkreślenie pojawia się w obszarze znak po prawej stronie, można wygenerować klasy zastępczej dla klasy, Konstruktor, metody, właściwości, pola lub typu wyliczeniowego. Aby uzyskać więcej informacji, zobacz [Generowanie z użycia](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).
  
 Przez rozwiązanie ostrzeżeń kompilatora języka Visual Basic, można napisać kod, który działa szybciej i ma mniejszą liczbę usterek. Ostrzeżenia te Zidentyfikuj kod, który może powodować błędy, gdy aplikacja jest uruchomiona. Na przykład, kompilator wyświetla ostrzeżenie, możesz Jeśli zostanie podjęta próba wywołania członkiem zmienną spowodowało utworzenie nieprzypisanego obiektu Zwróć z funkcji bez ustawienia zwracanej wartości lub wykonania `Try` bloku błędów w logice przechwytują wyjątki. Aby uzyskać więcej informacji na temat ostrzeżenia, w tym jak włączyć je włączać i wyłączać, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).
