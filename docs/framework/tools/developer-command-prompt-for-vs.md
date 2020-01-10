---
title: wiersz polecenia dla deweloperów dla programu Visual Studio
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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715831"
---
# <a name="developer-command-prompt-for-visual-studio"></a>wiersz polecenia dla deweloperów dla programu Visual Studio

Wiersz polecenia dla deweloperów dla programu Visual Studio umożliwia łatwiejsze korzystanie z narzędzi .NET Framework. Jest to wiersz polecenia, który automatycznie ustawia określone zmienne środowiskowe. Po otwarciu wiersz polecenia dla deweloperów można wprowadzić polecenia dla [.NET Framework narzędzi](index.md) , takich jak `ildasm` lub `clrver`.

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>Wyszukaj wiersz polecenia na komputerze

W zależności od wersji programu Visual Studio i wszelkich dodatkowych zestawów SDK i obciążeń, które zostały zainstalowane, może być wiele wierszy poleceń. Jeśli poniższe kroki nie działają, możesz spróbować [ręcznie zlokalizować pliki na maszynie](#manually-locate-the-files-on-your-machine) lub [uruchomić wiersz polecenia z poziomu programu Visual Studio](#start-the-command-prompt-from-inside-visual-studio).

### <a name="windows-10"></a>Windows 10

1. Na klawiaturze wybierz pozycję **uruchom** ![klucz logo systemu Windows.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) i przewiń do litery **V**.

1. Rozwiń folder **programu Visual Studio 2019** .

1. Wybierz **wiersz polecenia dla deweloperów dla programu VS 2019** (lub wiersza polecenia, którego chcesz użyć).

   Alternatywnie można rozpocząć wpisywanie nazwy wiersza polecenia w polu wyszukiwania na pasku zadań, a następnie wybrać wynik, który zostanie wyświetlony na liście wyników wyszukiwania.

   ![Animowany plik GIF pokazujący zachowanie wyszukiwania w systemie Windows 10](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Przejdź do ekranu **startowego** , naciskając klawisz logo systemu Windows ![klawisz logo Windows na klawiaturze.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) na przykład na klawiaturze.

1. Na ekranie **startowym** naciśnij klawisze **Ctrl**+**Tab** , aby otworzyć listę **aplikacje** , a następnie naciśnij klawisz **V**. Spowoduje to wyświetlenie listy zawierającej wszystkie zainstalowane polecenia programu Visual Studio.

1. Wybierz **wiersz polecenia dla deweloperów dla programu VS 2019** (lub wiersza polecenia, którego chcesz użyć).

### <a name="windows-7"></a>Windows 7

1. Wybierz przycisk **Start** , a następnie rozwiń pozycję **Wszystkie programy**.

1. Wybierz pozycję **Visual Studio 2019** > **Visual Studio Tools** > **wiersz polecenia dla deweloperów dla programu vs 2019**lub wiersz polecenia, którego chcesz użyć.

   ![Menu Start systemu Windows 7 z wyróżnionym wierszem polecenia](./media/developer-command-prompt-for-vs/windows7-menu.png)

Jeśli zainstalowano inne zestawy SDK, takie jak [zestaw SDK systemu Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) lub [poprzednie wersje](https://developer.microsoft.com/windows/downloads/sdk-archive), mogą pojawić się dodatkowe polecenia. W dokumentacji poszczególnych narzędzi można sprawdzić, której wersji wiersza polecenia należy użyć.

## <a name="manually-locate-the-files-on-your-machine"></a>Ręczne Lokalizowanie plików na maszynie

Zwykle skróty dla poleceń wyświetlanych przez użytkownika są umieszczane w folderze **menu Start** dla programu Visual Studio, na przykład w *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019 \ Visual Studio Tools*. Ale jeśli z jakiegoś powodu, wyszukiwanie w wierszu polecenia nie daje oczekiwanych wyników, możesz spróbować ręcznie zlokalizować skrót na komputerze. Spróbuj wyszukać nazwę pliku wiersza polecenia, na przykład *VsDevCmd. bat*, lub przejdź do folderu Tools, takiego jak *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools* (zmiany ścieżki w zależności od wersji programu Visual Studio, wersji i lokalizacji instalacji).

## <a name="start-the-command-prompt-from-inside-visual-studio"></a>Uruchom wiersz polecenia z wewnątrz programu Visual Studio

Aby ułatwić dostęp, można dodać wiersz polecenia dla deweloperów lub dowolny inny wiersz polecenia do menu Narzędzia w programie Visual Studio. Aby udostępnić narzędzie, Dodaj je do listy narzędzi zewnętrznych. Oto konkretne kroki:

1. Otwórz program Visual Studio.

1. W oknie uruchamiania wybierz pozycję **Kontynuuj bez kodu**.

1. Na pasku menu wybierz kolejno opcje **narzędzia** > **narzędzia zewnętrzne**.

1. W oknie dialogowym **narzędzia zewnętrzne** wybierz przycisk **Dodaj** . Zostanie wyświetlony nowy wpis.

1. Wprowadź **tytuł** dla nowego elementu menu, takiego jak `Command Prompt`.

1. W polu **polecenie** Określ plik, który chcesz uruchomić, taki jak `%comspec%` lub `C:\Windows\System32\cmd.exe`.

1. W polu **argumenty** Określ, gdzie znaleźć konkretny wiersz polecenia, który ma być używany, taki jak `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`. To polecenie powoduje uruchomienie wiersz polecenia dla deweloperów zainstalowanego z programem Visual Studio 2019 Community. Zmień tę wartość zgodnie z wersją programu Visual Studio, wydaniem i lokalizacją instalacji.

1. W polu **katalog początkowy** określ katalog, w którym zostanie uruchomiony wiersz polecenia. Wybierz wartość, na przykład **Katalog projektu** , wybierając strzałkę obok pola.

1. Wybierz **OK** przycisku.

   ![Okno dialogowe zewnętrznych narzędzi z wartościami pól wypełnione.](./media/developer-command-prompt-for-vs/add-external-tool.png)

   Nowy element menu zostanie dodany i możesz uzyskać dostęp do wiersza polecenia z menu Narzędzia.

   ![Element menu wiersza polecenia w programie Visual Studio](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a>Zobacz także

- [Narzędzia .NET Framework](index.md)
- [Zarządzanie narzędziami zewnętrznymi](/visualstudio/ide/managing-external-tools)
- [Korzystanie z zestawu C++ narzędzi firmy Microsoft z poziomu wiersza polecenia](/cpp/build/building-on-the-command-line)
