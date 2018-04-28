---
title: Funkcje środowiska deweloperskiego F#
description: 'Dowiedz się, jakie funkcje programu Visual Studio 2012 są obsługiwane w F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: dd5c3165a73bd4f821a26d183094829dab7eaeae
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="visual-f-development-environment-features"></a>Funkcje środowiska deweloperskiego Visual F #

> [!NOTE]
W tym artykule nie jest aktualny najnowsze Visual Studio.  Zostaną zaktualizowane.

Ten temat zawiera informacje o tym, które funkcje programu Visual Studio 2012 są obsługiwane w F #.

## <a name="project-features"></a>Funkcje projektu
Poniższa tabela zawiera podsumowanie szablonów, które są dostępne do użycia w projektach F #. Aby informacji na temat szablonów projektów i elementów, zobacz [NIB tworzenie projektów z szablonów](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2).

|Typ szablonu|Opis|Obsługiwane szablony|
|-------------|-----------|-------------------|
|Szablony projektu|Typy projektów, które są dostępne w **nowy projekt** okno dialogowe.|<ul><li>Aplikacji w języku F #<br /></li><li>Biblioteki języka F #<br /></li><li>Samouczek języka F #<br /></li><li>Biblioteka przenośna F #<br /></li><ul/>|
|Szablony elementu|Typy dostępnych w **Dodaj nowy element** okno dialogowe.|<ul><li>Źródłowy plik języka F # (.fs)<br /></li><li>Skrypt F # (.fsx)<br /></li><li>Podpis plik języka F # (.fsi)<br /></li><li>Plik konfiguracji (config)<br /></li><li>Połączenie z bazą danych SQL (LINQ do SQL dostawca typów)<br /></li><li>Połączenie z bazą danych SQL (LINQ to Entities, dostawca typów)<br /></li><li>Połączenie usługi OData (LINQ dostawca typów)<br /></li><li>Połączenie usługi WSDL (Dostawca typów)<br /></li><li>Plik XML (.xml)<br /></li><li>Plik tekstowy<br /></li><ul/>|
Aby utworzyć aplikację, która może działać jako autonomiczny plik wykonywalny, wybierz typ projektu aplikacji w języku F #. Aby utworzyć bibliotekę (czyli zestaw zarządzany lub. Plik DLL) do użycia na platformie pulpitu systemu Windows, wybierz biblioteki języka F #. Aby utworzyć przenośnej biblioteki, który może służyć na wszystkich obsługiwanych platformach, wybierz język F # przenośnej biblioteki. Wersja pliku FSharp.Core.dll odpowiednią do tworzenia biblioteki języka F # mogą być używane z aplikacji działających na platformach, na przykład aplikacje ze Sklepu Windows, .NET Framework 4.5, Xamarin.iOS i Xamarin.Android odwoływać się do projektów bibliotek przenośnych F #.

Aby uzyskać więcej informacji na temat szablonów elementu dla dostępu do danych, zobacz [dostawców typów](../tutorials/type-providers/index.md).

W poniższej tabeli przedstawiono obsługiwane i nie są obsługiwane w F # funkcje właściwości projektu. Aby uzyskać więcej informacji, zobacz [Konfigurowanie projektów](configuring-projects.md) i [wprowadzenie do projektanta projektu](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7).

|Ustawienia projektu|Obsługiwane w F #?|Uwagi|
|---------------|----------------|-----|
|Pliki zasobów|Tak||
|Kompilacji, debugowania i ustawień odniesienia|Tak||
|Wielowersyjność kodu|Tak||
|Ikony, jak i manifestu|Nie|Dostępne za pośrednictwem opcji wiersza polecenia kompilatora.|
|Usługi klienta programu ASP.NET|Nie||
|ClickOnce|Nie|Użyj projektu klienta w innym języku .NET Framework, jeśli ma to zastosowanie.|
|Silne nazewnictwo|Nie|Dostępne za pośrednictwem opcji wiersza polecenia kompilatora.|
|Zestaw publikowania i przechowywania wersji|Nie||
|Kod — analiza|Nie|Narzędzi analizy kodu można uruchomić ręcznie lub jako część polecenia mające miejsce po kompilacji.|
|Zabezpieczenia (poziomy zaufania zmian)|Nie||

## <a name="code-and-text-editor-features"></a>Kod i funkcje edycji tekstu
Poniższe funkcje programu Visual Studiocode i edytory tekstów, są obsługiwane w F #. Aby uzyskać ogólne informacje dotyczące edytowania kodu w programie Visual Studio i funkcje edytora tekstu, zobacz [pisanie kodu w edytorze kodu i tekstu](/visualstudio/ide/writing-code-in-the-code-and-text-editor).

|Funkcja|Opis|Obsługiwane w F #?|
|-------|-----------|----------------|
|Automatycznie komentarza|Można dodać komentarz lub usuń znaczniki komentarza fragmentów kodu.|Tak|
|Automatycznie Formatuj|Formatuje kodu przy użyciu standardowych wcięcia i styl.|Nie|
|Zakładki|Umożliwia zapisanie miejsca w edytorze.|Tak|
|Zmień wcięcie|Zwiększa wcięcie lub unindents zaznaczonych wierszach.|Tak|
|[Znajdowanie i zastępowanie tekstu](/visualstudio/ide/finding-and-replacing-text)|Umożliwia wyszukiwanie w pliku, projekt lub rozwiązanie i potencjalnie zmiany tekstu.|Tak|
|Przejdź do definicji interfejsu API programu .NET Framework|Gdy kursor znajduje się na interfejs API programu .NET Framework, zawiera kod generowany na podstawie .NET Framework — metadane.|Nie|
|Przejdź do definicji dla interfejsu API zdefiniowany przez użytkownika|Gdy kursor znajduje się w jednostce program, który zostanie zdefiniowany przesuwa kursor do lokalizacji w kodzie, w których jest zdefiniowana jednostka.|Tak|
|Przejdź do wiersza|Umożliwia przejście do określonego wiersza w pliku, numer wiersza.|Tak|
|Pasków nawigacji u góry pliku|Umożliwia przejście do lokalizacji w kodzie, na przykład nazwę funkcji.|Tak|
|Obramowanie. Zobacz [zwijania](/visualstudio/ide/outlining).|Umożliwia zwijanie sekcji swój kod, aby utworzyć widok mniejszych.|Tak|
|Tabify — formatowanie|Konwertuje spacje na znaki tabulacji.|Tak|
|Kolorowanie typów|Pokazuje zdefiniowane nazwy typów w kolorze specjalnych.|Tak|
|Szybkie wyszukiwanie. Zobacz Szybkie szukanie, znajdowanie i zamienianie okna.|Umożliwia wyszukiwanie w pliku lub projektu.|Tak|

## <a name="intellisense-features"></a>Funkcje IntelliSense
W poniższej tabeli przedstawiono funkcje IntelliSense obsługiwane i nie są obsługiwane w F #. Aby uzyskać ogólne informacje o funkcji IntelliSense, zobacz [za pomocą funkcji IntelliSense](/visualstudio/ide/using-intellisense).

|Funkcja|Opis|Obsługiwane w F #?|
|-------|-----------|----------------|
|Automatycznie implementować interfejsów|Generuje kod zastępcze metod interfejsu.|Nie|
|Wstawki kodu|Injects kod z biblioteki typowe konstrukcje kodu do tematów.|Nie|
|Dokończ wyraz|Zapisuje wpisanie, wykonując słów i nazwy podczas pisania.|Tak|
|Tryb uzupełniania korzystać z pierwszej|Włączenie tej opcji, powoduje, że ukończenie programu word do wybrania pierwszego dopasowania podczas wpisywania, zamiast czekać na wybranie jednego lub naciśnij klawisz **klawisze CTRL + SPACJA**.|Nie|
|Generowanie elementy kodu|Umożliwia generowanie kodu klasy zastępczej dla różnych konstrukcji.|Nie|
|Lista składników|Po wpisaniu operatora dostępu do elementu członkowskiego (.), zawiera elementy członkowskie dla określonego typu.|Tak|
|Organizowanie deklaracje Using/Otwórz|Umożliwia organizowanie przestrzeni nazw odwołuje się **przy użyciu** instrukcji w języku C# lub **Otwórz** dyrektywy w języku F #.|Nie|
|Informacje o parametrach|Zawiera przydatne informacje na temat parametrów podczas pisania wywołania funkcji.|Tak|
|Szybkie informacje|Wyświetla pełną deklarację dla żadnego identyfikatora w kodzie.|Tak|
Refaktoryzacja o kodzie języka F # nie jest obsługiwana w programie Visual Studio 2012.

## <a name="debugging-features"></a>Funkcje debugowania
W poniższej tabeli przedstawiono funkcje, które są dostępne podczas debugowania kodu języka F #. Aby uzyskać ogólne informacje o debugerze programu Visual Studio, zobacz [debugowania w programie Visual Studio](https://msdn.microsoft.com/library/sc65sadd.aspx).

|Funkcja|Opis|Obsługiwane w F #?|
|-------|-----------|----------------|
|okno zmiennych automatycznych|Pokazuje zmienne automatyczne lub tymczasowe.|Nie|
|Punkty przerwania|Umożliwia wstrzymuje wykonywanie kodu w określonych punktach podczas debugowania.|Tak|
|Warunkowe punkty przerwania|Umożliwia punktów kontrolnych, które warunek, który określa, czy należy wstrzymać wykonywania testu.|Tak|
|Edytuj i kontynuuj|Umożliwia kod, aby można modyfikować i skompilować, jak debugować uruchomiony program bez zatrzymania i ponownego uruchomienia debugera.|Nie|
|Ewaluator wyrażeń|Oblicza i wykonuje kod w czasie wykonywania.|Nie, ale C# ewaluatora wyrażenia mogą być używane, jednak należy użyć składni języka C#.|
|Debugowanie historyczne|Umożliwia wykonywanie kodu poprzednio wykonane.|Tak|
|okno zmiennych lokalnych|Pokazuje lokalnie zdefiniowane wartości oraz zmienne.|Tak|
|Uruchom do kursora|Umożliwia wykonanie kodu, aż do osiągnięcia wiersz zawierający kursora.|Tak|
|Wkrocz|Umożliwia wcześniejszego wykonania i Przenieś do dowolnej wywołania funkcji.|Tak|
|Przekrocz|Umożliwia wcześniejszego wykonania w bieżącej ramki stosu i przejść wszystkie wywołania funkcji.|Tak|

## <a name="additional-tools"></a>Dodatkowe narzędzia
Poniższa tabela zawiera podsumowanie obsługi F # w narzędziach Visual Studio.

|Narzędzie|Opis|Obsługiwane w F #?|
|----|-----------|----------------|
|Hierarchia wywołań|Wyświetla strukturze zagnieżdżonych funkcji wywołuje w kodzie.|Nie|
|Metryki kodów|Zbiera informacje o kodzie, takich jak liczby wierszy.|Nie|
|Widok klas|Zapewnia widok na podstawie typu kodu w projekcie.|Nie|
|[Okno listy błędów](/visualstudio/ide/reference/error-list-window)|Przedstawia listę błędów w kodzie.|Tak|
|[F# Interactive](../tutorials/fsharp-interactive/index.md)|Umożliwia wpisz (lub skopiuj i Wklej) F # kodu i uruchom go natychmiast, niezależnie od tworzenia projektu. Okno narzędzia F # Interactive jest odczytu, Evaluate, drukowania pętli (REPL).|Tak|
|Przeglądarka obiektów|Umożliwia wyświetlanie typów w zestawie.|Typy F # znajdujące się w skompilowane zestawy nie są dokładnie tak, jak je tworzyć. Reprezentacja skompilowana typów F # można przeglądać, ale nie można wyświetlić typy, jak pojawiają się one od F #.|
|[Okno Dane wyjściowe](/visualstudio/ide/reference/output-window)|Wyświetla dane wyjściowe kompilacji.|Tak|
|Analiza wydajności|Udostępnia narzędzia do pomiaru wydajności kodu.|Tak|
|Okno Właściwości|Wyświetla i umożliwia edytowanie właściwości obiektu w środowisku programistycznym, który ma fokus.|Tak|
|[W Eksploratorze serwera](https://msdn.microsoft.com/library/x603htbk.aspx)|Udostępnia metody interakcji z szerokiej gamy zasobów serwera.|Tak|
|Eksplorator rozwiązań|Umożliwia wyświetlanie i zarządzanie nią projektów i plików.|Tak|
|Lista zadań|Umożliwia zarządzanie elementów roboczych powiązanych z nią kodu.|Tak|
|Projekty testowe|Zawiera funkcje, które ułatwiają testowania kodu.|Nie|
|Przybornik|Wyświetla kart, które zawierają możliwością przeciągania obiekty, takie jak formantów i sekcji tekstu lub kodu.|Tak|

## <a name="see-also"></a>Zobacz też
 [Rozpoczynanie pracy z F # w programie Visual Studio](../get-started/get-started-visual-studio.md)  
 [Konfigurowanie projektów](configuring-projects.md)  
