---
title: Instalowanie zlokalizowanych plików IntelliSense
description: Dowiedz się, jak skonfigurować komputer deweloperski do korzystania z zlokalizowanych plików IntelliSense dla projektów .NET Core w programie Visual Studio.
author: mairaw
ms.author: mairaw
ms.date: 12/18/2019
ms.openlocfilehash: 98d75544ab853e75c175dd2919991b250cfaa3b0
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75443478"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a>Jak zainstalować zlokalizowane pliki IntelliSense dla platformy .NET Core

[IntelliSense](/visualstudio/ide/using-intellisense) to pomoc dla uzupełniania kodu, która jest dostępna w różnych zintegrowanych środowiskach programistycznych (środowisk IDE), takich jak program Visual Studio. Domyślnie podczas tworzenia projektów programu .NET Core zestaw SDK zawiera tylko angielską wersję plików IntelliSense. W tym artykule wyjaśniono:

- Jak zainstalować zlokalizowaną wersję tych plików.
- Jak zmodyfikować instalację programu Visual Studio tak, aby korzystała z innego języka.

## <a name="prerequisites"></a>Wymagania wstępne

- [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download/dotnet-core) lub nowsza wersja.
- [Program Visual Studio 2019 w wersji 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszej.

## <a name="download-and-install-the-localized-intellisense-files"></a>Pobieranie i Instalowanie zlokalizowanych plików IntelliSense

> [!IMPORTANT]
> Ta procedura wymaga uprawnień administratora do kopiowania plików IntelliSense do folderu instalacji programu .NET Core.

1. Przejdź do strony [pobieranie plików IntelliSense](https://dotnet.microsoft.com/download/dotnet-core/intellisense) .

1. Pobierz plik IntelliSense dla języka i wersji, której chcesz użyć.

1. Wyodrębnij zawartość pliku zip.

1. Przejdź do folderu instalacji programu .NET Core. Domyślnie jest to w obszarze *%ProgramFiles%\dotnet\packs*.

   - Wybierz zestaw SDK, dla którego chcesz zainstalować funkcję IntelliSense, i przejdź do skojarzonej ścieżki. Do wyboru są następujące opcje:

      | Typ zestawu SDK        | Ścieżka                               |
      | --------------- | ---------------------------------- |
      | .NET Core       | *Microsoft. servicecore. app. ref*        |
      | System Windows Desktop | *Microsoft. WindowsDesktop. app. ref* |
      | .NET Standard   | *Standard. Library. ref*          |
   
   - Przejdź do wersji, w której chcesz zainstalować zlokalizowaną funkcję IntelliSense. Na przykład *3.1.0*.
   - Otwórz folder *ref* .
   - Otwórz folder moniker. Na przykład *netcoreapp 3.1*.

   Dlatego pełna ścieżka, która będzie wyglądała, wygląda podobnie do *C:\Program Files\dotnet\packs\Microsoft.NETCore.app.Ref\3.1.0\ref\netcoreapp3.1*.

1. Utwórz podfolder w folderze moniker, który właśnie został otwarty. Nazwa folderu wskazuje język, którego chcesz użyć. W poniższej tabeli określono różne opcje:

   | Język              | Nazwa folderu |
   | --------------------- | ----------- |
   | Portugalski (Brazylia)  | *pt-br*     |
   | Chiński (uproszczony)  | *zh-Hans*   |
   | Chiński (tradycyjny) | *zh-Hant*   |
   | francuski                | *fr*        |
   | niemiecki                | *Ukryj*        |
   | Włoski               | *go*        |
   | japoński              | *Japonia*        |
   | koreański                | *Ko*        |
   | rosyjski               | *ru*        |
   | Hiszpański               | *AK*        |

1. Skopiuj pliki *. XML* wyodrębnione w kroku 3 do tego nowego folderu. Pliki *. XML* są podzielone na foldery zestawu SDK, dlatego skopiuj je do zgodnego zestawu SDK, który został wybrany w kroku 4.

## <a name="modify-visual-studio-language"></a>Modyfikuj język programu Visual Studio

Aby program Visual Studio używał innego języka dla technologii IntelliSense, zainstaluj odpowiedni pakiet językowy. Można to zrobić [podczas instalacji](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) lub w późniejszym czasie, modyfikując instalację programu Visual Studio. Jeśli masz już program Visual Studio skonfigurowany w wybranym języku, instalacja technologii IntelliSense jest gotowa.

### <a name="install-the-language-pack"></a>Instalowanie pakietu językowego

Jeśli podczas instalacji nie został zainstalowany odpowiedni pakiet językowy, zaktualizuj program Visual Studio w następujący sposób, aby zainstalować pakiet językowy:

> [!IMPORTANT]
> Aby zainstalować, zaktualizować lub zmodyfikuj program Visual Studio, musisz zalogować się przy użyciu konta z uprawnieniami administracyjnymi. Aby uzyskać więcej informacji, zobacz [uprawnienia użytkownika i program Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).

1. Znajdowanie Instalatora programu Visual Studio na komputerze.

   Na przykład na komputerze z systemem Windows 10, wybierz pozycję **Start**, a następnie przewiń do list **V**, w którym znajduje się w **Instalatora programu Visual Studio**.

   ![Otwórz Instalator programu Visual Studio z systemu Windows](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > Instalator programu Visual Studio można również znaleźć w następującej lokalizacji:
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   Może być konieczne zaktualizowanie Instalatora przed kontynuowaniem. Jeśli tak, postępuj zgodnie z monitami.

1. W instalatorze poszukaj wersji programu Visual Studio, do której chcesz dodać pakiet językowy, a następnie wybierz **Modyfikuj**.

   ![Aktualizowanie lub modyfikowanie programu Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > Jeśli nie widzisz przycisku **Modyfikuj** , ale zamiast tego zobaczysz **aktualizację** , musisz zaktualizować program Visual Studio przed zmodyfikowaniem instalacji.
   > Po zakończeniu aktualizacji powinien zostać wyświetlony przycisk **Modyfikuj** .

1. Na karcie **pakiety językowe** zaznacz lub odznacz Języki, które chcesz zainstalować lub odinstalować.

   ![Karta pakiety językowe programu Visual Studio](./media/localized-intellisense/vs-modify-language-packs.png)

1. Wybierz **Modyfikuj**. Rozpocznie się aktualizacja.

### <a name="modify-language-settings-in-visual-studio"></a>Modyfikowanie ustawień języka w programie Visual Studio

Po zainstalowaniu żądanych pakietów językowych zmodyfikuj ustawienia programu Visual Studio tak, aby korzystały z innego języka:

1. Otwórz program Visual Studio.

1. W oknie uruchamiania wybierz pozycję **Kontynuuj bez kodu**.

1. W menu głównym wybierz pozycję **narzędzia** > **Opcje**. Zostanie otwarte okno dialogowe Opcje.

1. W obszarze folder **środowiska** wybierz pozycję **Ustawienia międzynarodowe**.

1. Z listy rozwijanej **Język** wybierz odpowiedni język. Wybierz **OK**. 

1. Zostanie wyświetlone okno dialogowe z informacją, że musisz ponownie uruchomić program Visual Studio, aby zmiany zaczęły obowiązywać. Wybierz **OK**.

1. Uruchom ponownie program Visual Studio.

Po wykonaniu tej czynności funkcja IntelliSense powinna działać zgodnie z oczekiwaniami w przypadku otwarcia projektu .NET Core, który jest przeznaczony dla wersji zainstalowanych plików IntelliSense.

## <a name="see-also"></a>Zobacz także

- [Technologia IntelliSense w programie Visual Studio](/visualstudio/ide/using-intellisense)
