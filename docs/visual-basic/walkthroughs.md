---
title: Język Visual Basic — Wskazówki
description: Instrukcje krok po kroku dotyczące typowych scenariuszy w programie Visual Basic Development
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, walkthroughs
- examples [Visual Basic]
- Visual Basic code, walkthroughs
- walkthroughs [Visual Basic]
ms.assetid: e4e1f849-e1ce-4cf7-8483-d9b4c4887a8e
ms.openlocfilehash: f6a4c5b5376c5ee746bb0fadfeeac7ac9793e91f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040951"
---
# <a name="visual-basic-language-walkthroughs"></a>Język Visual Basic — Wskazówki

Instruktaże zawierają instrukcje krok po kroku dla typowych scenariuszy, co sprawia, że jest dobrym miejscem do rozpoczęcia uczenia się dotyczącej produktu lub określonego obszaru funkcji.

- [Pisanie programu asynchronicznego](./programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 Pokazuje, jak utworzyć rozwiązanie asynchroniczne przy użyciu [Async](language-reference/modifiers/async.md) i [await](language-reference/operators/await-operator.md).

- [Deklarowanie i wywoływanie zdarzeń](programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)  
 Ilustruje sposób deklarowania i zgłaszania zdarzeń w Visual Basic.

- [Obsługa zdarzeń](programming-guide/language-features/events/walkthrough-handling-events.md)  
 Pokazuje, jak obsługiwać zdarzenia przy użyciu standardowego słowa kluczowego `WithEvents` lub nowego `AddHandler`/`RemoveHandler` słów kluczowych.

- [Tworzenie i implementowanie interfejsów](programming-guide/language-features/interfaces/walkthrough-creating-and-implementing-interfaces.md)  
 Pokazuje, jak interfejsy są zadeklarowane i zaimplementowane w Visual Basic.

- [Definiowanie klas](programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)  
 Opisuje sposób deklarowania klasy i jej pól, właściwości, metod i zdarzeń.

- [Pisanie zapytań w Visual Basic](programming-guide/concepts/linq/walkthrough-writing-queries.md)  
 Demonstruje, w jaki sposób można użyć Visual Basic funkcji języka do pisania wyrażeń zapytania [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].

- [Implementowanie interfejsu IEnumerable (Of T) w Visual Basic](programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)  
 Demonstruje sposób tworzenia klasy implementującej interfejs `IEnumerable(Of String)` i klasy implementującej interfejs `IEnumerator(Of String)` do odczytywania pliku tekstowego po jednym wierszu.

- [Wywoływanie interfejsów API systemu Windows](programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 Wyjaśnia, jak używać instrukcji `Declare` i wywoływać interfejsy API systemu Windows. Zawiera informacje o używaniu atrybutów do sterowania kierowaniem do wywołania interfejsu API i sposobu uwidaczniania wywołania interfejsu API jako metody klasy.

- [Tworzenie obiektów COM przy użyciu Visual Basic](programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 Demonstruje sposób tworzenia obiektów COM w Visual Basic, zarówno z szablonem klasy COM, jak i bez niego.

- [Implementowanie dziedziczenia z obiektami COM](programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 Pokazuje, jak używać Visual Basic 6,0 do tworzenia obiektu COM zawierającego klasę, a następnie używania jej jako klasy bazowej w Visual Basic.

- [Ustalanie, gdzie my. Application. Log zapisuje informacje](developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 Opisuje domyślne ustawienia `My.Application.Log` i sposób określania ustawień aplikacji.

- [Zmienianie, gdzie my. Application. Log zapisuje informacje](developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 Pokazuje, w jaki sposób zastąpić domyślne `My.Application.Log` i `My.Log` ustawienia rejestrowania informacji o zdarzeniu i spowodować, że obiekt `Log` ma zapisywać w innych detektorach dzienników.

- [Filtrowanie danych wyjściowych my. Application. log](developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)  
 Pokazuje, jak zmienić domyślne filtrowanie dzienników dla obiektu `My.Application.Log`.

- [Tworzenie niestandardowych odbiorników dziennika](developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)  
 Pokazuje, jak utworzyć odbiornik dziennika niestandardowego i skonfigurować go do nasłuchiwania danych wyjściowych obiektu `My.Application.Log`.

- [Osadzanie typów z zarządzanych zestawów](../standard/assembly/embed-types-visual-studio.md)  
 Opisuje sposób tworzenia zestawu i programu klienckiego, który osadza z niego typy.

- [Weryfikowanie, czy hasła są złożone (Visual Basic)](programming-guide/language-features/strings/walkthrough-validating-that-passwords-are-complex.md)  
 Pokazuje, jak sprawdzać charakterystykę silnych haseł i aktualizować parametr ciągu z informacjami o tym, które sprawdzenia nie powiodło się.

- [Szyfrowanie i odszyfrowywanie ciągów w Visual Basic](programming-guide/language-features/strings/walkthrough-encrypting-and-decrypting-strings.md)  
 Pokazuje, w jaki sposób używać klasy <xref:System.Security.Cryptography.DESCryptoServiceProvider> do szyfrowania i odszyfrowywania ciągów.

- [Manipulowanie plikami i folderami w Visual Basic](developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 Pokazuje, jak używać funkcji Visual Basic do określania informacji o pliku, wyszukiwania ciągu w pliku i zapisu w pliku.

- [Manipulowanie plikami za pomocą metod .NET Framework](developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)  
 Demonstruje sposób użycia .NET Framework metod do określenia informacji o pliku, wyszukania ciągu w pliku i zapisu w pliku.

- [Utrwalanie obiektu w Visual Basic](programming-guide/concepts/serialization/walkthrough-persisting-an-object-in-visual-studio.md)  
 Demonstruje sposób tworzenia prostego obiektu i utrwalania jego danych w pliku.

- [Przewodnik: Obsługa wczesnego testowania przy użyciu funkcji generowania na podstawie sposobu użycia](/visualstudio/ide/walkthrough-test-first-support-with-the-generate-from-usage-feature)  
 Pokazuje, w jaki sposób należy przeprowadzić programowanie w pierwszej kolejności, w której najpierw napisać testy jednostkowe, a następnie napisać kod źródłowy w celu pomyślnego wykonania testów.
