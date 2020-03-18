---
title: Publikowanie aplikacji .NET Core Hello World za pomocą programu Visual Studio
description: Publikowanie tworzy zestaw plików, które są potrzebne do uruchomienia aplikacji .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: bdd6e28713bdece2bd144e6763bd84d719e91449
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156637"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a>Publikowanie aplikacji .NET Core Hello World za pomocą programu Visual Studio

W [programie Tworzenie aplikacji Hello World z usługą .NET Core w programie Visual Studio](with-visual-studio.md)utworzono aplikację konsoli Hello World. W [debugowania aplikacji Hello World za pomocą programu Visual Studio](debugging-with-visual-studio.md)przetestowano ją przy użyciu debugera Programu Visual Studio. Teraz, gdy masz pewność, że działa zgodnie z oczekiwaniami, możesz go opublikować, aby inni użytkownicy mogli go uruchomić. Publikowanie tworzy zestaw plików, które są potrzebne do uruchomienia aplikacji. Aby wdrożyć pliki, skopiuj je na komputer docelowy.

## <a name="publish-the-app"></a>Publikowanie aplikacji

1. Upewnij się, że program Visual Studio jest tworzenie wersji aplikacji. W razie potrzeby zmień ustawienie konfiguracji kompilacji na pasku narzędzi z **Debug** na **Release**.

   ![Pasek narzędzi programu Visual Studio z wybraną kompilacją wersji](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. Kliknij prawym przyciskiem myszy projekt **HelloWorld** (nie rozwiązanie HelloWorld) i wybierz **polecenie Publikuj** z menu. (Możesz również wybrać **opcję Publikuj HelloWorld** z głównego menu **Kompilacja).**

   ![Visual Studio Publikowanie menu kontekstowe](media/publishing-with-visual-studio/publish-context-menu.png)

1. Na stronie **Wybierz obiekt docelowy publikowania** wybierz pozycję **Folder**, a następnie wybierz pozycję **Utwórz profil**.

   ![Wybieranie obiektu docelowego publikowania w programie Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)

1. Na stronie **Publikowanie** wybierz pozycję **Publikuj**.

   ![Okno Publikowania w programie Visual Studio](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a>Sprawdzanie plików

Proces publikowania tworzy wdrożenie zależne od struktury, które jest typem wdrożenia, w którym opublikowana aplikacja jest uruchamiana na dowolnej platformie obsługiwanej przez program .NET Core z zainstalowanym w systemie .NET Core. Użytkownicy mogą uruchomić opublikowaną aplikację, klikając dwukrotnie plik wykonywalny lub wydając `dotnet HelloWorld.dll` polecenie z wiersza polecenia.

W poniższych krokach przyjrzysz się plikom utworzonym przez proces publikowania.

1. Otwórz wiersz polecenia.

   Jednym ze sposobów otwarcia wiersza polecenia jest wprowadzenie **wiersza polecenia** (lub **skrótu cmd)** w polu wyszukiwania na pasku zadań systemu Windows. Wybierz aplikację **klasyczną Wiersz polecenia** lub naciśnij klawisz **Enter,** jeśli jest już zaznaczona w wynikach wyszukiwania.

1. Przejdź do opublikowanej aplikacji w *katalogu bin\Release\netcoreapp3.1\publish* katalogu projektu aplikacji.

   ![Okno konsoli z wyświetlonymi opublikowanymi plikami](media/publishing-with-visual-studio/published-files-output.png)

   Jak pokazano na obrazie, opublikowane dane wyjściowe zawierają następujące pliki:

      * *HelloWorld.deps.json*

         Jest to plik zależności w czasie wykonywania aplikacji. Definiuje składniki .NET Core i biblioteki (w tym biblioteki łączy dynamicznych, która zawiera aplikację) potrzebne do uruchomienia aplikacji. Aby uzyskać więcej informacji, zobacz [Pliki konfiguracyjne czasu wykonywania](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).

      * *HelloWorld.dll*

         Jest to wersja [wdrożenia zależna od struktury](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikacji. Aby wykonać tę bibliotekę `dotnet HelloWorld.dll` łączy dynamicznych, wprowadź w wierszu polecenia.

      * *HelloWorld.exe (HelloWorld.exe)*

         Jest to [zależna od struktury wykonywalna](../deploying/deploy-with-cli.md#framework-dependent-executable) wersja aplikacji. Aby go uruchomić, wprowadź `HelloWorld.exe` w wierszu polecenia.

      * *HelloWorld.pdb* (opcjonalnie do wdrożenia)

         Jest to plik symboli debugowania. Nie są wymagane do wdrożenia tego pliku wraz z aplikacją, chociaż należy zapisać go w przypadku, gdy trzeba debugować opublikowaną wersję aplikacji.

      * *HelloWorld.runtimeconfig.json*

         Jest to plik konfiguracyjny aplikacji w czasie wykonywania. Identyfikuje wersję programu .NET Core, na którą została zbudowana aplikacja. Można również dodać do niego opcje konfiguracji. Aby uzyskać więcej informacji, zobacz [ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).

## <a name="additional-resources"></a>Zasoby dodatkowe

- [Wdrażanie aplikacji .NET Core](../deploying/index.md)
