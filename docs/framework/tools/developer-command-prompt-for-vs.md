---
title: Wiersz polecenia dla programu Visual Studio deweloperów
ms.date: 03/30/2017
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
ms.openlocfilehash: d3ff897e37e3fa2f7202a54c05c8093ba05282c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="developer-command-prompt-for-visual-studio"></a>Wiersz polecenia dla programu Visual Studio deweloperów
Wiersz polecenia dla programu Visual Studio deweloperów automatycznie ustawia zmienne środowiskowe, które pozwalają łatwo za pomocą narzędzia .NET Framework. Wiersz polecenia dewelopera jest instalowany z full lub społeczności wersji programu Visual Studio. Nie jest instalowany z wersji Express programu Visual Studio.  
  
<a name="find"></a>   
## <a name="searching-for-the-command-prompt-on-your-machine"></a>Wyszukiwanie w wierszu polecenia na komputerze  
 Może pojawić się wiele wierszy polecenia, w zależności od wersji programu Visual Studio i wszelkie dodatkowe zestawy SDK został zainstalowany. Na przykład 64-bitowe wersje programu Visual Studio oferują 32-bitowy i 64-bitowy wiersz polecenia. (32-bitowe i 64-bitowe wersje większości narzędzi są identyczne, ale niektóre narzędzia wprowadzają zmiany specyficzne dla środowisk 32-bitowych i 64-bitowych). Jeśli Poniższa procedura nie działa, możesz spróbować [ręcznie lokalizowanie plików na tym komputerze](#alternative) lub [polecenia monitu w programie Visual Studio](#visualstudio).  
  
 **W systemie Windows 10**  
  
1.  Otwórz **Start** menu, naciskając klawisz z logo systemu Windows ![logo systemu Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klawiaturze, na przykład.  
  
2.  Na **Start** menu, wprowadź `dev`. Zostanie wyświetlone listę zainstalowanych aplikacji, spełniających kryteria wyszukiwania. Jeśli szukasz innego wiersza polecenia, spróbuj wprowadzić inny wyszukiwany termin, takich jak `prompt`.  
  
3.  Wybierz **wiersza polecenia dewelopera** (lub w wierszu polecenia, którego chcesz użyć).  
  
 **W Windows 8.1**  
  
1.  Przejdź do **Start** ekran, naciskając klawisz z logo systemu Windows ![logo systemu Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klawiaturze, na przykład.  
  
2.  Na **Start** ekranu, naciśnij klawisz `CTRL + TAB` otworzyć **aplikacje** listy, a następnie wprowadź `V`. Zostanie wyświetlone na liście zawierającej wszystkie zainstalowane wiersz polecenia programu Visual Studio.  
  
3.  Wybierz **wiersza polecenia dewelopera** (lub w wierszu polecenia, którego chcesz użyć).  
  
 **W systemie Windows 8**  
  
1.  Przejdź do **Start** ekran, naciskając klawisz z logo systemu Windows ![logo systemu Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klawiaturze, na przykład.  
  
2.  Na **Start** ekranu, naciśnij klawisz z logo systemu Windows ![logo systemu Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.  
  
3.  Wybierz **wyświetlić aplikacje** ikony w dolnej części ekranu, a następnie wprowadź `V`. Zostanie wyświetlone na liście zawierającej wszystkie zainstalowane wiersz polecenia programu Visual Studio.  
  
4.  Wybierz **wiersza polecenia dewelopera** (lub w wierszu polecenia, którego chcesz użyć).  
  
 **W systemie Windows 7**  
  
1.  Wybierz **Start**, rozwiń węzeł **wszystkie programy**, a następnie rozwiń węzeł **programu Microsoft Visual Studio**.  
  
2.  W zależności od wersji programu Visual Studio został zainstalowany, należy wybrać **programu Visual Studio Tools**, **wiersz polecenia programu Visual Studio**, lub w wierszu polecenia, którego chcesz użyć.  
  
 Jeśli masz [zestaw Windows SDK](http://msdn.microsoft.com/windows/desktop/aa904949) lub [Windows Phone SDK](https://dev.windowsphone.com/downloadsdk) zainstalowany, może zostać wyświetlony dodatkowe polecenie monituje o ARM, x 86 lub x64 architektury. W dokumentacji poszczególnych narzędzi można sprawdzić, której wersji wiersza polecenia należy użyć.  
  
<a name="alternative"></a>   
## <a name="manually-locating-the-files-on-your-machine"></a>Ręcznie lokalizowanie plików na tym komputerze  
  Zwykle, skróty klawiaturowe polecenie monituje o zainstalowaniu zostaną umieszczone w **Start Menu** folderu dla programu Visual Studio, taki jak C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2015\Visual Studio Narzędzia.    Jednak jeśli zaistnieje, wyszukiwanie w wierszu polecenia nie oczekiwanych rezultatów, możesz spróbować ręcznie zlokalizować skrót na komputerze, aby można było go używać.   Spróbuj wyszukiwania dla nazwy pliku wiersza polecenia, takich jak VsDevCmd.bat lub przejdź do folderu narzędzi, takich jak C:\Program Files (x86) \Microsoft Visual Studio 14.0\Common7\Tools (ścieżka zmieni się zgodnie z lokalizacją wersji i instalacji programu Visual Studio).  
  
<a name="visualstudio"></a>   
## <a name="running-command-prompt-from-inside-visual-studio"></a>Uruchomienie polecenia monitu w programie Visual Studio  
 W celu ułatwienia dostępu można dodać wiersz polecenia dewelopera programu Visual Studio lub innych poleceń do menu Narzędzia w programie Visual Studio przez dodanie go do listy narzędzi zewnętrznych. Jest to, jak można wykonać który:  
  
1.  Otwórz program Visual Studio.  
  
2.  Wybierz **narzędzia** menu i wybierz polecenie **zewnętrznych narzędzi...** .  
  
3.  Na **zewnętrznych narzędzi** oknie dialogowym wybierz **Dodaj** przycisku. Pojawi się nowy wpis  
  
4.  Wprowadź **tytuł** dla nowego elementu menu, takich jak `Command Prompt`.  
  
5.  W **polecenia** Określ plik, który chcesz uruchomić, takich jak `%comspec%` lub `C:\Windows\System32\cmd.exe` .  
  
6.  W **argumenty** Określ, gdzie można znaleźć określonego wiersza polecenia, którego chcesz użyć, takich jak `/k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat"` (spowoduje to uruchomienie zainstalowany z wiersza polecenia dewelopera [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]). Ta wartość musi zostać zmienione w zależności od lokalizacji wersji i instalacji programu Visual Studio.  
  
7.  Wybierz wartość dla **katalog początkowy** pola, takie jak **katalogu projektu** .  
  
8.  Wybierz **OK** przycisku.  
  
 Po wykonaniu tej zostanie dodany nowy element menu i może uzyskać dostępu do wiersza polecenia z **narzędzia** menu.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Zarządzanie narzędziami zewnętrznymi](/visualstudio/ide/managing-external-tools)
