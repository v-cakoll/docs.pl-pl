---
title: Wiersz polecenia programisty dla programu Visual Studio
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
ms.openlocfilehash: 4c95074190419dd3e984c7659ede917b83b97f08
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524719"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Wiersz polecenia programisty dla programu Visual Studio

Wiersz polecenia dla deweloperów programu Visual Studio automatycznie ustawia zmienne środowiskowe, które pozwalają na łatwe używanie narzędzi programu .NET Framework.

> [!div class="button"]
[Pobierz program Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

## <a name="searching-for-the-command-prompt-on-your-machine"></a>Wyszukiwanie w wierszu polecenia na komputerze

Może mieć kilka wierszy polecenia, w zależności od wersji programu Visual Studio oraz wszelkie dodatkowe zainstalowanych zestawów SDK. Na przykład 64-bitowe wersje programu Visual Studio oferują 32-bitowy i 64-bitowy wiersz polecenia. (32-bitowych i 64-bitowe wersje większości narzędzi są takie same; jednak niektóre narzędzia wprowadzają zmiany specyficzne dla środowisk 32-bitowych i 64-bitowych). Jeśli poniższe kroki nie zadziałają, spróbuj [ręcznie lokalizowania plików na maszynie](#manually-locating-the-files-on-your-machine) lub [uruchamiając wiersz polecenia z poziomu programu Visual Studio](#running-command-prompt-from-inside-visual-studio).

### <a name="in-windows-10"></a>W systemie Windows 10

1. W polu wyszukiwania na pasku zadań, należy uruchomić, wpisując nazwę narzędzia, takie jak `dev` lub `developer command prompt`. Wyświetlenie listy zainstalowanych aplikacji spełniających kryteria wyszukiwania. Jeśli potrzebujesz innego wiersza polecenia, spróbuj wprowadzić różne wyszukiwany termin takich jak `prompt`.

2. Wybierz **wiersz polecenia dla deweloperów** (lub wiersza polecenia, którego chcesz użyć).

### <a name="in-windows-81"></a>W Windows 8.1

1. Przejdź do **Start** ekran przez naciśnięcie klawiszy logo Windows ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klawiaturze, na przykład.

2. Na **Start** ekranu, naciśnij klawisz `CTRL + TAB` otworzyć **aplikacje** listy, a następnie wprowadź `V`. Wybranie tej opcji powoduje listy, która zawiera wszystkie zainstalowane wiersz polecenia programu Visual Studio.

3. Wybierz **wiersz polecenia dla deweloperów** (lub wiersza polecenia, którego chcesz użyć).

### <a name="in-windows-8"></a>W systemie Windows 8

1. Przejdź do **Start** ekran przez naciśnięcie klawiszy logo Windows ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klawiaturze, na przykład.

2. Na **Start** ekranu, naciśnij klawisze logo Windows ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.

3. Wybierz **wyświetlić aplikacje** ikony w dolnej części ekranu, a następnie wprowadź `V`. Wybranie tej opcji powoduje listy, która zawiera wszystkie zainstalowane wiersz polecenia programu Visual Studio.

4. Wybierz **wiersz polecenia dla deweloperów** (lub wiersza polecenia, którego chcesz użyć).

### <a name="in-windows-7"></a>W Windows 7

1. Wybierz **Start**, rozwiń węzeł **wszystkie programy**, a następnie rozwiń węzeł **programu Microsoft Visual Studio**.

2. W zależności od wersji programu Visual Studio po zainstalowaniu wybierz **Visual Studio Tools**, **Visual Studio Command Prompt**, lub z wiersza polecenia, którego chcesz użyć.

W przypadku innych zestawów SDK zainstalowany, takich jak [zestawu Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) lub [poprzednie wersje](https://developer.microsoft.com/windows/downloads/sdk-archive), może zostać wyświetlony dodatkowe wiersze polecenia dla ARM, x 86 lub x64 architektury. W dokumentacji poszczególnych narzędzi można sprawdzić, której wersji wiersza polecenia należy użyć.

## <a name="manually-locate-the-files-on-your-machine"></a>Ręcznie lokalizowania plików na komputerze

Zwykle, skróty klawiaturowe wiersz polecenia, zainstalowane są umieszczane na **Start Menu** folderu dla programu Visual Studio, takich jak narzędzia Studio 2017\Visual C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio. Ale jeśli z jakiegoś powodu, wyszukiwanie w wierszu polecenia nie zachowa oczekiwanych rezultatów, możesz spróbować ręcznie zlokalizować skrót na swojej maszynie. Spróbuj wyszukać nazwę pliku polecenia, takie jak *VsDevCmd.bat*, lub przejdź do folderu Tools, np. C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools (ścieżka zmiany na podstawie wizualizacji Studio wersji i edycji oraz z instalacji lokalizacji).

## <a name="run-command-prompt-from-inside-visual-studio"></a>Uruchom polecenie prompt z poziomu programu Visual Studio

W celu ułatwienia dostępu, można dodać wiersz polecenia dla deweloperów Visual Studio lub inne polecenia do **narzędzia** menu w programie Visual Studio. Aby udostępnić narzędzia, należy go dodać do listy zewnętrznych narzędzi. Poniżej przedstawiono kroki:

1. Otwórz program Visual Studio.

2. Wybierz **narzędzia** menu, a następnie wybierz **zewnętrznych narzędzi**.

3. Na **zewnętrznych narzędzi** okna dialogowego wybierz **Dodaj** przycisku. Pojawi się nowy wpis.

4. Wprowadź **tytuł** dla nowego elementu menu, takich jak `Command Prompt`.

5. W **polecenia** Określ plik, który chcesz uruchomić, takich jak `%comspec%` lub `C:\Windows\System32\cmd.exe`.

6. W **argumenty** pola, określ, gdzie można znaleźć określonego wiersza polecenia, którego chcesz użyć, takie jak `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (to polecenie uruchamia wiersz polecenia dla deweloperów jest instalowany z programem Visual Studio 2017 Enterprise). Zmień tę wartość, zgodnie z lokalizacją wersji i edycji oraz z instalacji programu Visual Studio.

7. Wybierz wartość dla **Czątkowy katalog** pola, takie jak **katalogu projektu**.

8. Wybierz **OK** przycisku.

   Zostanie dodany nowy element menu, a są dostępne z wiersza polecenia z **narzędzia** menu.

## <a name="see-also"></a>Zobacz także

- [Narzędzia](../../../docs/framework/tools/index.md)
- [Zarządzanie narzędziami zewnętrznymi](/visualstudio/ide/managing-external-tools)
