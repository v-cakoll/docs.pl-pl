---
title: Komunikaty o błędach (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- errors [Visual Basic]
- error messages
- trappable errors
- errors [Visual Basic], trappable
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
ms.openlocfilehash: c326b781222429d68ec4385d95507a6ba99eafcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590137"
---
# <a name="error-messages-visual-basic"></a>Komunikaty o błędach (Visual Basic)
Podczas zapisu, kompilacji lub uruchamianie aplikacji Visual Basic, mogą wystąpić następujące błędy:  
  
1.  Błędy czasu projektowania, podczas pisania aplikacji w programie Visual Studio.  
  
2.  Błędy kompilacji podczas kompilowania aplikacji w programie Visual Studio lub w wierszu polecenia.  
  
3.  Błędy środowiska wykonawczego, które występują po uruchomieniu aplikacji w programie Visual Studio lub jako autonomicznego pliku wykonywalnego.  
  
 Aby uzyskać informacje o rozwiązywaniu problemów z określonego błędu, zobacz [zasoby dodatkowe dla programistów Visual Basic](../../../visual-basic/getting-started/additional-resources.md).  
  
## <a name="run-time-errors"></a>Błędy wykonania  
 Jeśli aplikacji Visual Basic próbuje wykonać akcję systemu nie można wykonać, wystąpi błąd czasu wykonywania i Visual Basic generuje `Exception` obiektu. Visual Basic mogą generować błędy niestandardowe wszelkich danych typu, łącznie z `Exception` obiektów przy użyciu `Throw` instrukcji. Aplikację można zidentyfikować błędu wyświetlając numer błędu i komunikat zgłoszony wyjątek. Jeśli nie jest zgłoszony błąd, kończy się aplikacja.  
  
 Kod można przechwytują i sprawdzić błędy środowiska wykonawczego. Jeśli umieść kod, który powoduje błąd w `Try` bloku, można przechwycić zgłoszenia błędu w odpowiadającego mu `Catch` bloku. Aby uzyskać informacje na temat reagowania na je w kodzie i przechwytywać błędy w czasie wykonywania, zobacz [spróbuj... CATCH... Instrukcji finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="compile-time-errors"></a>Błędy w czasie kompilacji  
 Jeśli kompilator Visual Basic napotka problem w kodzie, występuje błąd kompilacji. W edytorze kodu można łatwo zidentyfikować które wiersz kodu spowodował błąd, ponieważ faliste pozycji zostanie wiersza kodu. Komunikat o błędzie jest wyświetlany, jeśli albo wskazania faliste podkreślenie lub Otwórz **listy błędów**, który zawiera również inne komunikaty.  
  
 Jeśli identyfikator ma faliste podkreślenie i krótki podkreślenie jest wyświetlany w obszarze znak po prawej stronie, można wygenerować klasy zastępczej dla klasy, konstruktora, metody, właściwości, pola lub wyliczenia. Aby uzyskać więcej informacji, zobacz [Generowanie z użycia](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).
  
 Rozwiązując ostrzeżenia kompilatora Visual Basic, można napisać kod, który działa szybciej i ma mniejszą liczbę usterek. Te ostrzeżenia dotyczące identyfikowania kod, który może powodować błędy po uruchomieniu aplikacji. Na przykład kompilator ostrzega możesz próba wywołania elementu członkowskiego zmiennej obiektu nieprzypisane zwracanie z funkcji bez ustawienia wartości zwracanej lub wykonać `Try` bloku błędów w logice przechwytują wyjątki. Aby uzyskać więcej informacji na temat ostrzeżenia, łącznie ze sposobem jej włączanie i wyłączanie, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).
