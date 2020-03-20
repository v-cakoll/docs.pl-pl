---
title: Wiersz polecenia dewelopera dla programu Visual Studio
ms.date: 01/05/2020
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
ms.openlocfilehash: f028281d477284acf3ac4dac63f5ddbbd79f5259
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715831"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Wiersz polecenia dewelopera dla programu Visual Studio

Wiersz polecenia dewelopera dla programu Visual Studio umożliwia łatwiejsze korzystanie z narzędzi programu .NET Framework. Jest to wiersz polecenia, który automatycznie ustawia określone zmienne środowiskowe. Po otwarciu wiersza polecenia dewelopera można wprowadzić polecenia `ildasm` dla `clrver`narzędzi [programu .NET Framework,](index.md) takich jak lub .

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>Wyszukiwanie wiersza polecenia na komputerze

Może być wiele wierszy polecenia, w zależności od wersji programu Visual Studio i wszelkie dodatkowe zestawy SDK i obciążeń, które zostały zainstalowane. Jeśli poniższe kroki nie działają, możesz spróbować [ręcznie zlokalizować pliki na komputerze](#manually-locate-the-files-on-your-machine) lub uruchomić wiersz polecenia z programu Visual [Studio](#start-the-command-prompt-from-inside-visual-studio).

### <a name="windows-10"></a>Windows 10

1. Wybierz **pozycję Uruchom** ![klawisz logo systemu Windows na klawiaturze.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) i przewiń do litery **V**.

1. Rozwiń folder **programu Visual Studio 2019.**

1. Wybierz **pozycję Developer Command Prompt for VS 2019** (lub wiersz polecenia, którego chcesz użyć).

   Alternatywnie można rozpocząć wpisywanie nazwy wiersza polecenia w polu wyszukiwania na pasku zadań i wybrać wynik, który ma być wyświetlany, gdy lista wyników zacznie wyświetlać dopasowania wyszukiwania.

   ![Animowany gif pokazujący zachowanie wyszukiwania w systemie Windows 10](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Przejdź do ekranu **startowego,** naciskając ![klawisz logo Windows na klawiaturze.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) na klawiaturze.

1. Na ekranie **startowym** naciśnij klawisz **Ctrl**+**Tab,** aby otworzyć listę **Aplikacje,** a następnie naciśnij klawisz **V**. Spowoduje to wyświetlenie listy zawierającej wszystkie zainstalowane wiersze poleceń programu Visual Studio.

1. Wybierz **pozycję Developer Command Prompt for VS 2019** (lub wiersz polecenia, którego chcesz użyć).

### <a name="windows-7"></a>Windows 7

1. Wybierz **pozycję Start,** a następnie rozwiń pozycję **Wszystkie programy**.

1. Wybierz polecenie **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt for VS 2019**lub wiersz polecenia, którego chcesz użyć.

   ![Menu Start systemu Windows 7 z wyróżnionym wierszem polecenia](./media/developer-command-prompt-for-vs/windows7-menu.png)

Jeśli masz zainstalowane inne pakiety SDK, takie jak [windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) lub [poprzednie wersje,](https://developer.microsoft.com/windows/downloads/sdk-archive)mogą zostać wyświetlona dodatkowe monity o polecenia. W dokumentacji poszczególnych narzędzi można sprawdzić, której wersji wiersza polecenia należy użyć.

## <a name="manually-locate-the-files-on-your-machine"></a>Ręczne lokalizowanie plików na komputerze

Zazwyczaj skróty zainstalowanych wierszy polecenia są umieszczane w folderze **Menu Start** programu Visual Studio, na przykład w *programie "ProgramData%\Microsoft\Windows\Menu Start\Programy\Visual Studio 2019\Visual Studio Tools*. Jeśli jednak z jakiegoś powodu wyszukiwanie wiersza polecenia nie daje oczekiwanych rezultatów, możesz spróbować ręcznie zlokalizować skrót na komputerze. Spróbuj wyszukać nazwę pliku wiersza polecenia, takiego jak *VsDevCmd.bat,* lub przejdź do folderu Narzędzia, takiego jak *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (ścieżka zmienia się zgodnie z wersją programu Visual Studio, wersją i lokalizacją instalacji).

## <a name="start-the-command-prompt-from-inside-visual-studio"></a>Uruchamianie wiersza polecenia od wewnątrz programu Visual Studio

Aby uzyskać łatwiejszy dostęp, można dodać wiersz polecenia dewelopera lub dowolny inny wiersz polecenia do menu Narzędzia w programie Visual Studio. Aby udostępnić narzędzie, dodaj je do listy narzędzi zewnętrznych. Oto konkretne kroki:

1. Otwórz program Visual Studio.

1. W oknie startowym wybierz pozycję **Kontynuuj bez kodu**.

1. Na pasku menu wybierz pozycję Narzędzia**zewnętrzne** **Narzędzia** > .

1. W oknie dialogowym **Narzędzia zewnętrzne** wybierz przycisk **Dodaj.** Pojawi się nowy wpis.

1. Wprowadź **tytuł** dla nowego elementu `Command Prompt`menu, takiego jak .

1. W polu **Polecenie** określ plik, który chcesz `%comspec%` `C:\Windows\System32\cmd.exe`uruchomić, na przykład lub .

1. W polu **Argumenty** określ, gdzie ma być używany określony `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`wiersz polecenia, którego chcesz użyć, na przykład . To polecenie uruchamia wiersz polecenia dewelopera, który jest zainstalowany w środowisku społeczności programu Visual Studio 2019. Zmień tę wartość zgodnie z wersją programu Visual Studio, wersją i lokalizacją instalacji.

1. W polu **Katalog początkowy** określ katalog, w którym zostanie uruchomiony wiersz polecenia. Wybierz wartość, taką jak **Katalog projektów,** zaznaczając strzałkę obok pola.

1. Wybierz przycisk **OK.**

   ![Okno dialogowe Narzędzia zewnętrzne z wypełnionymi wartościami pól.](./media/developer-command-prompt-for-vs/add-external-tool.png)

   Nowy element menu zostanie dodany i można uzyskać dostęp do wiersza polecenia z menu Narzędzia.

   ![Pozycja menu wiersza polecenia w programie Visual Studio](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a>Zobacz też

- [Narzędzia programu .NET Framework](index.md)
- [Zarządzanie narzędziami zewnętrznymi](/visualstudio/ide/managing-external-tools)
- [Używanie zestawu narzędzi Microsoft C++ z wiersza polecenia](/cpp/build/building-on-the-command-line)
