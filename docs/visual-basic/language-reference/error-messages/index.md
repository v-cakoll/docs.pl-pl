---
title: komunikaty o błędach
ms.date: 07/20/2015
helpviewer_keywords:
- errors [Visual Basic]
- error messages
- trappable errors
- errors [Visual Basic], trappable
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
ms.openlocfilehash: 15d12802c92e7b9ed99c83885bd38e381c8b687d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353713"
---
# <a name="error-messages-visual-basic"></a>Komunikaty o błędach (Visual Basic)
Podczas pisania, kompilowania lub uruchamiania aplikacji Visual Basic mogą wystąpić następujące typy błędów:  
  
1. Błędy czasu projektowania, które występują podczas pisania aplikacji w programie Visual Studio.  
  
2. Błędy czasu kompilacji, które występują podczas kompilowania aplikacji w programie Visual Studio lub w wierszu polecenia.  
  
3. Błędy czasu wykonywania, które występują podczas uruchamiania aplikacji w programie Visual Studio lub jako autonomiczny plik wykonywalny.  
  
 Informacje o sposobach rozwiązywania określonego błędu znajdują się w temacie [dodatkowe zasoby dla programistów Visual Basic](../../../visual-basic/getting-started/additional-resources.md).  
  
## <a name="run-time-errors"></a>Błędy czasu wykonywania  
 Jeśli aplikacja Visual Basic próbuje wykonać akcję, której system nie może wykonać, wystąpi błąd czasu wykonywania, a Visual Basic zgłasza obiekt `Exception`. Visual Basic może generować niestandardowe błędy dowolnego typu danych, łącznie z obiektami `Exception`, przy użyciu instrukcji `Throw`. Aplikacja może zidentyfikować błąd, wyświetlając numer błędu i komunikat przechwyconego wyjątku. Jeśli błąd nie zostanie przechwycony, aplikacja zostanie zakończona.  
  
 Kod może Zalewka i sprawdzanie błędów czasu wykonywania. Jeśli zamieścisz kod, który generuje błąd w bloku `Try`, możesz przechwytywać wszystkie zgłoszone błędy w obrębie pasującego bloku `Catch`. Aby dowiedzieć się, jak zalewkować błędy w czasie wykonywania i odpowiadać na nie w kodzie, zobacz [try... Catch... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="compile-time-errors"></a>Błędy kompilacji  
 Jeśli kompilator Visual Basic napotyka problem w kodzie, wystąpi błąd czasu kompilacji. W edytorze kodu można łatwo określić, który wiersz kodu spowodował błąd, ponieważ linia falista pojawia się pod tym wierszem kodu. Komunikat o błędzie jest wyświetlany, gdy użytkownik wskaże podkreślenie faliste lub otworzy **Lista błędów**, w którym znajdują się również inne komunikaty.  
  
 Jeśli identyfikator ma podkreśloną falistą, a krótka podkreślenie pojawia się pod znakiem po prawej stronie, można wygenerować element zastępczy dla klasy, konstruktora, metody, właściwości, pola lub wyliczenia. Aby uzyskać więcej informacji, zobacz [generowanie na podstawie użycia](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).
  
 Rozwiązując ostrzeżenia z kompilatora Visual Basic, może być możliwe napisanie kodu, który działa szybciej i ma mniejszą liczbę błędów. Te ostrzeżenia identyfikują kod, który może spowodować błędy podczas uruchamiania aplikacji. Na przykład kompilator ostrzega, jeśli spróbujesz wywołać element członkowski zmiennej nieprzypisanego obiektu, Wróć z funkcji bez ustawienia wartości zwracanej lub wykonaj blok `Try` z błędami w logice, aby przechwytywać wyjątki. Aby uzyskać więcej informacji na temat ostrzeżeń, w tym sposobu ich włączania i wyłączania, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).
