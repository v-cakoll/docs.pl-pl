---
title: Instalowanie zlokalizowanych plików IntelliSense
description: Dowiedz się, jak skonfigurować komputer deweloperski do używania zlokalizowanych plików IntelliSense dla projektów .NET Core w programie Visual Studio.
ms.date: 01/23/2020
ms.openlocfilehash: e45e225e58865ca2b529000ada0984fbeca850f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157716"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a>Jak zainstalować zlokalizowane pliki IntelliSense dla programu .NET Core

[IntelliSense](/visualstudio/ide/using-intellisense) to pomoc uzupełniania kodu, która jest dostępna w różnych zintegrowanych środowiskach programistycznych (IDEs), takich jak Visual Studio. Domyślnie podczas opracowywania projektów .NET Core zestaw SDK zawiera tylko angielską wersję plików IntelliSense. W tym artykule wyjaśniono:

- Jak zainstalować zlokalizowane wersje tych plików.
- Jak zmodyfikować instalację programu Visual Studio, aby używać innego języka.

## <a name="prerequisites"></a>Wymagania wstępne

- [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) lub nowsza wersja.
- [Visual Studio 2019 w wersji 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszej wersji.

## <a name="download-and-install-the-localized-intellisense-files"></a>Pobieranie i instalowanie zlokalizowanych plików IntelliSense

> [!IMPORTANT]
> Ta procedura wymaga posiadania uprawnień administratora do kopiowania plików IntelliSense do folderu instalacyjnego .NET Core.

1. Przejdź do strony [Pobierz pliki IntelliSense.](https://dotnet.microsoft.com/download/dotnet-core/intellisense)

1. Pobierz plik IntelliSense dla języka i wersji, której chcesz użyć.

1. Wyodrębnij zawartość pliku zip.

1. Przejdź do folderu .NET Core Intellisense.

   1. Przejdź do folderu instalacyjnego programu .NET Core. Domyślnie znajduje się w obszarze *%ProgramFiles%\dotnet\packs*.
   1. Wybierz zestaw SDK, dla którego chcesz zainstalować program IntelliSense, i przejdź do skojarzonej ścieżki. Istnieją następujące opcje:

      | Typ sdk        | Ścieżka                               |
      | --------------- | ---------------------------------- |
      | .NET Core       | *Plik Microsoft.NETCore.App.Ref*        |
      | Pulpit systemu Windows | *Microsoft.WindowsDesktop.App.Ref* |
      | .NET Standard   | *NETStandard.Library.Ref*          |

   1. Przejdź do wersji, dla której chcesz zainstalować zlokalizowany program IntelliSense. Na przykład *3.1.0*.
   1. Otwórz folder *ref.*
   1. Otwórz folder moniker. Na przykład *netcoreapp3.1*.

   Tak więc pełna ścieżka, do której chcesz przejść, będzie wyglądać podobnie do *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.

1. Utwórz podfolder wewnątrz właśnie otwartego folderu moniker. Nazwa folderu wskazuje, którego języka chcesz użyć. W poniższej tabeli określono różne opcje:

   | Język              | Nazwa folderu |
   | --------------------- | ----------- |
   | Portugalski brazylijski  | *pt-br (pt-br)*     |
   | Chiński (uproszczony)  | *zh-hans (zh-hans)*   |
   | Chiński (tradycyjny) | *zh-hant (zh-hant)*   |
   | Francuski                | *O*        |
   | Niemiecki                | *De*        |
   | Włoski               | *to*        |
   | Japoński              | *ja*        |
   | Koreański                | *Ko*        |
   | Rosyjski               | *Ru*        |
   | Hiszpański               | *Es*        |

1. Skopiuj pliki *xml* wyodrębnione w kroku 3 do tego nowego folderu. Pliki *xml* są podzielone według folderów SDK, więc skopiuj je do pasującego sdk wybranego w kroku 4.

## <a name="modify-visual-studio-language"></a>Modyfikowanie języka programu Visual Studio

Aby program Visual Studio używał innego języka dla programu IntelliSense, zainstaluj odpowiedni pakiet językowy. Można to zrobić [podczas instalacji](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) lub w późniejszym czasie, modyfikując instalację programu Visual Studio. Jeśli program Visual Studio jest już skonfigurowany do wybranego języka, instalacja intelliSense jest gotowa.

### <a name="install-the-language-pack"></a>Instalowanie pakietu językowego

Jeśli podczas instalacji nie zainstalowałeś żądanego pakietu językowego, zaktualizuj program Visual Studio w następujący sposób, aby zainstalować pakiet językowy:

> [!IMPORTANT]
> Aby zainstalować, zaktualizować lub zmodyfikować program Visual Studio, należy zalogować się przy użyciu konta, które ma uprawnienia administratora. Aby uzyskać więcej informacji, zobacz [Uprawnienia użytkownika i Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).

1. Znajdź Instalatorprogramu Visual Studio na komputerze.

   Na przykład na komputerze z systemem Windows 10 wybierz pozycję **Start**, a następnie przewiń do litery **V**, gdzie jest ona wymieniona jako **Instalator programu Visual Studio**.

   ![Otwieranie Instalatora programu Visual Studio z systemu Windows](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > Instalator programu Visual Studio można również znaleźć w następującej lokalizacji:
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   Może być trzeba zaktualizować instalator przed kontynuowaniem. Jeśli tak, postępuj zgodnie z instrukcjami.

1. W instalatorze poszukaj wersji programu Visual Studio, do której chcesz dodać pakiet językowy, a następnie wybierz pozycję **Modyfikuj**.

   ![Aktualizowanie lub modyfikowanie programu Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > Jeśli nie widzisz przycisku **Modyfikuj,** ale zamiast tego zostanie wyświetlony **przycisk Aktualizuj,** musisz zaktualizować program Visual Studio, zanim będzie można zmodyfikować instalację.
   > Po zakończeniu aktualizacji powinien pojawić się przycisk **Modyfikuj.**

1. Na karcie **Pakiety językowe** wybierz lub usuń zaznaczenie języków, które chcesz zainstalować lub odinstalować.

   ![Karta Pakiety językowe programu Visual Studio](./media/localized-intellisense/vs-modify-language-packs.png)

1. Wybierz **pozycję Modyfikuj**. Rozpocznie się aktualizacja.

### <a name="modify-language-settings-in-visual-studio"></a>Modyfikowanie ustawień języka w programie Visual Studio

Po zainstalowaniu żądanych pakietów językowych zmodyfikuj ustawienia programu Visual Studio, aby używać innego języka:

1. Otwórz program Visual Studio.

1. W oknie startowym wybierz pozycję **Kontynuuj bez kodu**.

1. Na pasku menu wybierz pozycję**Opcje** **narzędzi** > . Zostanie otwarte okno dialogowe Opcje.

1. W obszarze **Węzeł Środowisko** wybierz pozycję **Ustawienia międzynarodowe**.

1. W **obszarze** rozwijanym Język wybierz żądany język. Wybierz pozycję **OK**.

1. Okno dialogowe informuje, że należy ponownie uruchomić program Visual Studio, aby zmiany zaczęły obowiązywać. Wybierz pozycję **OK**.

1. Uruchom ponownie program Visual Studio.

Następnie intelliSense powinien działać zgodnie z oczekiwaniami po otwarciu projektu .NET Core, który jest przeznaczony dla wersji właśnie zainstalowanych plików IntelliSense.

## <a name="see-also"></a>Zobacz też

- [IntelliSense w programie Visual Studio](/visualstudio/ide/using-intellisense)
