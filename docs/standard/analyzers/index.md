---
title: Analizatory — oparte na platformie Roslyn platformy .NET
description: 'Więcej informacji na temat analizatorów Roslyn na podstawie, znajdować problemy, które sugerują poprawkami tych problemów.'
author: billwagner
ms.author: billwagner
ms.date: 01/24/2018
ms.technology: dotnet-standard
---

# <a name="the-roslyn-based-analyzers"></a>Roslyn na podstawie analizatorów

Oparte na programie Roslyn analizatory Użyj kompilatora zestawu SDK programu .NET (interfejsy API Roslyn) do analizowania kodu źródłowego projektu można znaleźć problemy, a także sugerują poprawki. Analizatory różnych poszukaj różne rodzaje problemów, począwszy od praktyk, które mogą być przyczyną błędów z bezpieczeństwem się zgodnością z interfejsem API.

Oparte na programie Roslyn analizatory współpracować interaktywnie i podczas kompilacji. Analizator wskazówki różne w przypadku programu Visual Studio lub w kompilacji z wiersza polecenia.

Podczas edycji kodu w programie Visual Studio analizatory działać po wprowadzeniu dowolnych zmian, przechwytywanie potencjalne problemy, jak utworzyć kod, który wyzwolić wątpliwości. Wszelkie problemy są wyróżniane faliste linie w dowolnym problemem. Program Visual Studio Wyświetla żarówki, a po jego kliknięciu analizatora sugeruje możliwe poprawki dla tego problemu. Podczas tworzenia projektu w programie Visual Studio lub z wiersza polecenia analizy kodu źródłowego i analizatora zawiera pełną listę potencjalnych problemów. Na poniższej ilustracji przedstawiono przykład.

![problemów zgłaszanych przez analizator struktury](./media/framework-analyzers-2.png)

Oparte na programie Roslyn analizatory raport potencjalnych problemów jako błędy, ostrzeżenia lub informacji na podstawie ich wagi problemu.

Należy zainstalować oparte na programie Roslyn analizatory jako pakiety NuGet w projekcie. Analizatory skonfigurowane wszystkie ustawienia dla każdego analizatora przywrócona i uruchomić na maszynie Każdy deweloper dla tego projektu.

> [!NOTE]
> Środowisko użytkownika oparte na programie Roslyn analizatory jest inny niż w przypadku biblioteki analizy kodu, takich jak starsze wersje programu FxCop i narzędzi do analizy zabezpieczeń.  Nie trzeba jawnie uruchomić analizatory oparte na programie Roslyn. Nie ma potrzeby używania elementów menu "Uruchomienia analizy kodu" w menu "Analizuj" w programie Visual Studio. Oparte na programie Roslyn analizatory są uruchamiane asynchronicznie podczas pracy.

## <a name="more-information-on-specific-analyzers"></a>Więcej informacji na temat określonych analizatorów

W tej sekcji omówione są następujące analizatory:

* [Interfejs API analizatora](api-analyzer.md): Ta analizator sprawdza swój kod pod kątem potencjalnych zagrożeń zgodności lub korzysta z interfejsów API przestarzałych.
* [Analizator struktury](framework-analyzer.md): Ta analizator sprawdza swój kod, aby upewnić się, że jest zgodna z wytycznymi dla aplikacji programu .NET Framework. Zasady te obejmują kilka zaleceń oparty na zabezpieczeniach.
* [Narzędzia .NET portability Analyzer](portability-analyzer.md): Ta analizator sprawdza swój kod, aby sprawdzić, ile pracy jest wymagane, aby Twoje aplikacje zgodne z innych implementacji platformy .NET i profilów, w tym .NET Core, .NET Standard, platformy uniwersalnej systemu Windows i Xamarin dla systemów iOS, Android i Mac.
