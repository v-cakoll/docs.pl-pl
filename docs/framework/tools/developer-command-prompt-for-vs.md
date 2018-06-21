---
title: Wiersz polecenia dla programu Visual Studio deweloperów
ms.date: 06/18/2018
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
ms.openlocfilehash: 7e91822f172de8700b04847541c4b80010a22b53
ms.sourcegitcommit: 3d42e1d73e21c35c540dd4adbea23efcbe1b8b0a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2018
ms.locfileid: "36270490"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Wiersz polecenia dla programu Visual Studio deweloperów

Wiersz polecenia dla programu Visual Studio deweloperów automatycznie ustawia zmienne środowiskowe, które pozwalają łatwo za pomocą narzędzia .NET Framework. Wiersz polecenia dewelopera jest instalowany z full lub społeczności wersji programu Visual Studio. Nie jest on instalowany w wersjach Express programu Visual Studio.

> [!div class="button"]
[Pobierz program Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

## <a name="searching-for-the-command-prompt-on-your-machine"></a>Wyszukiwanie w wierszu polecenia na komputerze

Może pojawić się wiele wierszy polecenia, w zależności od wersji programu Visual Studio i wszelkie dodatkowe zestawy SDK został zainstalowany. Na przykład 64-bitowe wersje programu Visual Studio oferują 32-bitowy i 64-bitowy wiersz polecenia. (Wersje 32-bitowe i 64-bitowe Większość narzędzi są takie same; jednak kilka narzędzi zmiany określonego środowiska 32-bitowe i 64-bitowe). Jeśli nie działają następujące kroki, możesz spróbować [ręcznie lokalizowanie plików na tym komputerze](#manually-locating-the-files-on-your-machine) lub [polecenia monitu w programie Visual Studio](#running-command-prompt-from-inside-visual-studio).

### <a name="in-windows-10"></a>W systemie Windows 10

1. W polu wyszukiwania na pasku zadań, rozpocznij wpisywanie nazwy narzędzia, takie jak `dev` lub `developer command prompt`. Dzięki temu udostępniają listę zainstalowanych aplikacji, spełniających kryteria wyszukiwania. Jeśli szukasz innego wiersza polecenia, spróbuj wprowadzić inny wyszukiwany termin, takich jak `prompt`.

2. Wybierz **wiersza polecenia dewelopera** (lub w wierszu polecenia, którego chcesz użyć).

### <a name="in-windows-81"></a>W Windows 8.1

1. Przejdź do **Start** ekran, naciskając klawisz z logo systemu Windows ![logo systemu Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klawiaturze, na przykład.

2. Na **Start** ekranu, naciśnij klawisz `CTRL + TAB` otworzyć **aplikacje** listy, a następnie wprowadź `V`. Wybranie tej opcji powoduje listy, która zawiera wszystkie zainstalowane wiersz polecenia programu Visual Studio.

3. Wybierz **wiersza polecenia dewelopera** (lub w wierszu polecenia, którego chcesz użyć).

### <a name="in-windows-8"></a>W systemie Windows 8

1. Przejdź do **Start** ekran, naciskając klawisz z logo systemu Windows ![logo systemu Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klawiaturze, na przykład.

2. Na **Start** ekranu, naciśnij klawisz z logo systemu Windows ![logo systemu Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.

3. Wybierz **wyświetlić aplikacje** ikony w dolnej części ekranu, a następnie wprowadź `V`. Wybranie tej opcji powoduje listy, która zawiera wszystkie zainstalowane wiersz polecenia programu Visual Studio.

4. Wybierz **wiersza polecenia dewelopera** (lub w wierszu polecenia, którego chcesz użyć).

### <a name="in-windows-7"></a>W systemie Windows 7

1. Wybierz **Start**, rozwiń węzeł **wszystkie programy**, a następnie rozwiń węzeł **programu Microsoft Visual Studio**.

2. W zależności od wersji programu Visual Studio po zainstalowaniu, wybierz **programu Visual Studio Tools**, **wiersz polecenia programu Visual Studio**, lub w wierszu polecenia, którego chcesz użyć.

Jeśli masz inne zainstalowano zestaw SDK usługi takie jak [zestawu Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) lub [poprzednie wersje](https://developer.microsoft.com/windows/downloads/sdk-archive) zainstalowany, może zostać wyświetlony dodatkowe polecenie monituje o ARM, x 86 lub x64 architektury. W dokumentacji poszczególnych narzędzi można sprawdzić, której wersji wiersza polecenia należy użyć.

## <a name="manually-locating-the-files-on-your-machine"></a>Ręcznie lokalizowanie plików na tym komputerze

Zwykle, skróty klawiaturowe polecenie monituje o zainstalowaniu są umieszczane na **Start Menu** folderu dla programu Visual Studio, taki jak C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual w Studio Tools. Ale jeśli z jakiegoś powodu wyszukiwanie w wierszu polecenia nie zachowa oczekiwanych rezultatów, możesz spróbować ręcznie zlokalizować skrót na tym komputerze. Spróbuj wyszukiwania dla nazwy pliku wiersza polecenia, takich jak *VsDevCmd.bat*, lub przejdź do folderu narzędzi takich jak C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools (ścieżka zmian zgodnie z Visual Studio wersji, wersji i instalacji lokalizacji).

## <a name="running-command-prompt-from-inside-visual-studio"></a>Uruchomienie polecenia monitu w programie Visual Studio

W celu ułatwienia dostępu można dodać wiersz polecenia dewelopera programu Visual Studio lub innych poleceń do menu Narzędzia w programie Visual Studio przez dodanie go do listy narzędzi zewnętrznych. Jest to, jak można wykonać który:

1. Otwórz program Visual Studio.

2. Wybierz **narzędzia** menu i wybierz polecenie **zewnętrznych narzędzi**.

3. Na **zewnętrznych narzędzi** oknie dialogowym wybierz **Dodaj** przycisku. Zostanie wyświetlony nowy wpis.

4. Wprowadź **tytuł** dla nowego elementu menu, takich jak `Command Prompt`.

5. W **polecenia** Określ plik, który chcesz uruchomić, takich jak `%comspec%` lub `C:\Windows\System32\cmd.exe`.

6. W **argumenty** Określ, gdzie można znaleźć określonego wiersza polecenia, którego chcesz użyć, takich jak `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (to polecenie uruchamia Developer wierszu polecenia, który jest instalowany z programu Visual Studio Enterprise 2017). Zmień tę wartość w zależności od lokalizacji wersji, wersji i instalacji programu Visual Studio.

7. Wybierz wartość dla **katalog początkowy** pola, takie jak **katalogu projektu**.

8. Wybierz **OK** przycisku.

Po wykonaniu tej zostanie dodany nowy element menu i może uzyskać dostępu do wiersza polecenia z **narzędzia** menu.

## <a name="see-also"></a>Zobacz także

 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Zarządzanie narzędziami zewnętrznymi](/visualstudio/ide/managing-external-tools)  
