---
title: wiersz polecenia dla deweloperów dla programu Visual Studio
ms.date: 08/14/2018
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59af252967a18eca858035fb0a3465d909734ddf
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044726"
---
# <a name="developer-command-prompt-for-visual-studio"></a>wiersz polecenia dla deweloperów dla programu Visual Studio

Wiersz polecenia dla deweloperów dla programu Visual Studio umożliwia łatwiejsze korzystanie z narzędzi .NET Framework. Jest to wiersz polecenia, który automatycznie ustawia określone zmienne środowiskowe.

> [!div class="button"]
> [Pobierz program Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>Wyszukaj wiersz polecenia na komputerze

W zależności od używanej wersji programu Visual Studio i dowolnych dodatkowych zestawów SDK można wyświetlać wiele wierszy poleceń. Na przykład 64-bitowe wersje programu Visual Studio oferują 32-bitowy i 64-bitowy wiersz polecenia. (32-bitowe i 64-bitowe wersje większości narzędzi są takie same, ale kilka narzędzi wprowadza zmiany specyficzne dla środowisk 32-bit i 64-bitowym). Jeśli poniższe kroki nie działają, możesz spróbować [ręcznie zlokalizować pliki na maszynie](#manually-locate-the-files-on-your-machine) lub [uruchomić wiersz polecenia z wewnątrz programu Visual Studio](#run-the-command-prompt-from-inside-visual-studio).

### <a name="in-windows-10"></a>W systemie Windows 10

1. W polu wyszukiwania na pasku zadań Zacznij wpisywać nazwę narzędzia, `dev` na przykład lub. `developer command prompt` Spowoduje to wyświetlenie listy zainstalowanych aplikacji, które pasują do Twojego wzorca wyszukiwania. Jeśli szukasz innego wiersza polecenia, spróbuj wprowadzić inny termin wyszukiwania, taki jak `prompt`.

2. Wybierz **wiersz polecenia dla deweloperów dla programu Visual Studio** (lub wiersz polecenia, którego chcesz użyć).

### <a name="in-windows-81"></a>W Windows 8.1

1. Przejdź do ekranu **startowego** , naciskając klawisz logo systemu Windows ![na klawiaturze.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) na przykład na klawiaturze.

2. Na ekranie **startowym** naciśnij klawisz **Ctrl**+ **, aby otworzyć** listę **aplikacje** , a następnie wprowadź `V`. Spowoduje to wyświetlenie listy zawierającej wszystkie zainstalowane polecenia programu Visual Studio.

3. Wybierz **wiersz polecenia dla deweloperów** (lub wiersz polecenia, którego chcesz użyć).

### <a name="in-windows-8"></a>W systemie Windows 8

1. Przejdź do ekranu **startowego** , naciskając klawisz logo systemu Windows ![na klawiaturze.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) na przykład na klawiaturze.

2. Na ekranie **startowym** naciśnij klawisz ![logo systemu Windows na klawiaturze.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) `+ Z`.

3. Wybierz ikonę **widok aplikacje** u dołu ekranu, a następnie wprowadź `V`. Spowoduje to wyświetlenie listy zawierającej wszystkie zainstalowane polecenia programu Visual Studio.

4. Wybierz **wiersz polecenia dla deweloperów** (lub wiersz polecenia, którego chcesz użyć).

### <a name="in-windows-7"></a>W systemie Windows 7

1. Wybierz **Start**, rozwiń **Wszystkie programy**, a następnie rozwiń **Microsoft Visual Studio**.

2. W zależności od zainstalowanej wersji programu Visual Studio wybierz **Visual Studio Tools**, **wiersz polecenia programu Visual Studio**lub wiersz polecenia, którego chcesz użyć.

Jeśli zainstalowano inne zestawy SDK, takie jak [zestaw SDK systemu Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) lub [poprzednie wersje](https://developer.microsoft.com/windows/downloads/sdk-archive), mogą pojawić się dodatkowe wiersze poleceń dla architektury ARM, x86 i x64. W dokumentacji poszczególnych narzędzi można sprawdzić, której wersji wiersza polecenia należy użyć.

## <a name="manually-locate-the-files-on-your-machine"></a>Ręczne Lokalizowanie plików na maszynie

Zwykle skróty dla poleceń z zainstalowanymi monitami są umieszczane w folderze **menu Start** dla programu Visual Studio, na przykład w programie C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017 \ Visual Studio Tools. Ale jeśli z jakiegoś powodu, wyszukiwanie w wierszu polecenia nie powoduje przeprowadzenia oczekiwanych wyników, możesz spróbować ręcznie zlokalizować skrót na komputerze. Spróbuj wyszukać nazwę pliku wiersza polecenia, na przykład *VsDevCmd. bat*, lub przejdź do folderu Tools, takiego jak C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools (zmiany ścieżki zgodnie z wersją programu Visual Studio, wersja i lokalizacja instalacji).

## <a name="run-the-command-prompt-from-inside-visual-studio"></a>Uruchom wiersz polecenia z wewnątrz programu Visual Studio

Aby ułatwić dostęp, można dodać program Visual Studio wiersz polecenia dla deweloperów lub dowolny inny wiersz polecenia do menu **Narzędzia** w programie Visual Studio. Aby udostępnić narzędzie, Dodaj je do listy narzędzi zewnętrznych. Oto konkretne kroki:

1. Otwórz program Visual Studio.

2. Wybierz menu **Narzędzia** , a następnie wybierz polecenie **narzędzia zewnętrzne**.

3. W oknie dialogowym **narzędzia zewnętrzne** wybierz przycisk **Dodaj** . Zostanie wyświetlony nowy wpis.

4. Wprowadź **tytuł** dla nowego elementu menu, na przykład `Command Prompt`.

5. W polu **polecenie** Określ plik, który chcesz uruchomić, `%comspec%` na przykład lub. `C:\Windows\System32\cmd.exe`

6. W polu **argumenty** Określ lokalizację, w której ma znajdować się konkretny wiersz polecenia, który ma być `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` używany na przykład (to polecenie powoduje uruchomienie wiersz polecenia dla deweloperów zainstalowanego z programem Visual Studio 2017 Enterprise). Zmień tę wartość zgodnie z wersją programu Visual Studio, wydaniem i lokalizacją instalacji.

7. Wybierz wartość pola **katalog początkowy** , na przykład **Katalog projektu**.

8. Wybierz **OK** przycisku.

   Nowy element menu zostanie dodany i możesz uzyskać dostęp do wiersza polecenia z menu **Narzędzia** .

   ![Element menu wiersza polecenia w programie Visual Studio](./media/command-prompt-vs-menu.png)

## <a name="see-also"></a>Zobacz także

- [Narzędzia](index.md)
- [Zarządzanie narzędziami zewnętrznymi](/visualstudio/ide/managing-external-tools)
