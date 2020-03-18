---
title: 'Samouczek: Instalowanie i używanie narzędzi lokalnych .NET Core'
description: Dowiedz się, jak zainstalować narzędzie .NET i używać go jako narzędzia lokalnego.
ms.date: 02/12/2020
ms.openlocfilehash: a4355886513040e2436bdbd87905e5baee2dd7a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156702"
---
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a>Samouczek: Instalowanie i używanie lokalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core

**Ten artykuł dotyczy:** ✔️ .NET Core 3.0 SDK i nowszych wersji

W tym samouczku nauczycię, jak zainstalować i używać lokalnego narzędzia. Używasz narzędzia, które tworzysz w [pierwszym samouczku tej serii](global-tools-how-to-create.md).

## <a name="prerequisites"></a>Wymagania wstępne

* Ukończ [pierwszy samouczek z tej serii](global-tools-how-to-create.md).
* Zainstaluj program .NET Core 2.1.

  W tym samouczku należy zainstalować i użyć narzędzia przeznaczonego dla programu .NET Core 2.1, więc musisz zainstalować ten czas uruchomieniowy na komputerze. Aby zainstalować czas uruchomieniowy 2.1, przejdź do [strony pobierania .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1) i znajdź łącze instalacji programu Run w kolumnie **Uruchom aplikacje — Czas wykonywania.**

## <a name="create-a-manifest-file"></a>Tworzenie pliku manifestu

Aby zainstalować narzędzie tylko dla dostępu lokalnego (dla bieżącego katalogu i podkatalogów), należy je dodać do pliku manifestu.

Z folderu *microsoft.botsay* przejdź do jednego poziomu do folderu *repozytorium:*

```console
cd ..
```

Utwórz plik manifestu, uruchamiając [polecenie dotnet nowe:](dotnet-new.md)

```dotnetcli
dotnet new tool-manifest
```

Dane wyjściowe wskazują na pomyślne utworzenie pliku.

```console
The template "Dotnet local tool manifest file" was created successfully.
```

Plik *.config/dotnet-tools.json* nie zawiera jeszcze żadnych narzędzi:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

Narzędzia wymienione w pliku manifestu są dostępne dla bieżącego katalogu i podkatalogów. Bieżący katalog to katalog zawierający katalog *konfiguracyjny* z plikiem manifestu.

Korzystając z polecenia wiersza polecenia, które odwołuje się do narzędzia lokalnego, zestaw SDK wyszukuje plik manifestu w bieżącym katalogu i katalogach nadrzędnych. Jeśli znajdzie plik manifestu, ale plik nie zawiera narzędzia, do którego do której dowołuje się, kontynuuje wyszukiwanie w górę za pośrednictwem katalogów nadrzędnych. Wyszukiwanie kończy się, gdy znajdzie narzędzie, do którego `isRoot` istnieje `true`odwołanie, lub znajdzie plik manifestu z ustawieniem .

## <a name="install-botsay-as-a-local-tool"></a>Zainstaluj botsay jako narzędzie lokalne

Zainstaluj narzędzie z pakietu utworzonego w pierwszym samouczku:

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

To polecenie dodaje narzędzie do pliku manifestu utworzonego w poprzednim kroku. Dane wyjściowe polecenia pokazuje, w którym pliku manifestu znajduje się nowo zainstalowane narzędzie:

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

Plik *.config/dotnet-tools.json* ma teraz jedno narzędzie:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "microsoft.botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    }
  }
}
```

## <a name="use-the-tool"></a>Korzystanie z narzędzia

Wywołaj narzędzie, uruchamiając `dotnet tool run` polecenie z folderu *repozytorium:*

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a>Przywracanie lokalnego narzędzia zainstalowanego przez inne osoby

Zazwyczaj instalujesz narzędzie lokalne w katalogu głównym repozytorium. Po zaewidencjonowanie pliku manifestu do repozytorium, inni deweloperzy mogą uzyskać najnowszy plik manifestu. Aby zainstalować wszystkie narzędzia wymienione w pliku manifestu, `dotnet tool restore` można uruchomić jedno polecenie.

1. Otwórz plik *.config/dotnet-tools.json* i zastąp zawartość następującym plikiem JSON:

   ```json
   {
     "version": 1,
     "isRoot": true,
     "tools": {
       "microsoft.botsay": {
         "version": "1.0.0",
         "commands": [
           "botsay"
         ]
       },
       "dotnetsay": {
         "version": "2.1.3",
         "commands": [
           "dotnetsay"
         ]
       }
     }
   }
   ```

1. Zastąp `<name>` nazwę użytą do utworzenia projektu.

1. Zapisz zmiany.

   Wprowadzenie tej zmiany jest taka sama jak uzyskanie najnowszej wersji z repozytorium po zainstalowaniu pakietu `dotnetsay` dla katalogu projektu przez inną osobę.

1. Uruchom polecenie `dotnet tool restore`.

   ```dotnetcli
   dotnet tool restore
   ```

   Polecenie generuje dane wyjściowe, takie jak w poniższym przykładzie:

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. Sprawdź, czy narzędzia są dostępne:

   ```dotnetcli
   dotnet tool list
   ```

   Dane wyjściowe to lista pakietów i poleceń, podobna do następującego przykładu:

   ```console
   Package Id      Version      Commands       Manifest
   --------------------------------------------------------------------------------------------
   microsoft.botsay 1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay        2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. Przetestuj narzędzia:

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a>Aktualizowanie narzędzia lokalnego

Zainstalowana wersja narzędzia `dotnetsay` lokalnego to 2.1.3.  Najnowsza wersja to 2.1.4. Użyj polecenia [dotnet tool update,](dotnet-tool-update.md) aby zaktualizować narzędzie do najnowszej wersji.

```dotnetcli
dotnet tool update dotnetsay
```

Dane wyjściowe wskazują nowy numer wersji:

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

Polecenie update znajdzie pierwszy plik manifestu, który zawiera identyfikator pakietu i aktualizuje go. Jeśli nie ma takiego identyfikatora pakietu w żadnym pliku manifestu, który znajduje się w zakresie wyszukiwania, zestaw SDK dodaje nowy wpis do najbliższego pliku manifestu. Zakres wyszukiwania jest za pośrednictwem katalogów `isRoot = true` nadrzędnych, dopóki nie zostanie znaleziony plik manifestu.

## <a name="remove-local-tools"></a>Usuwanie narzędzi lokalnych

Usuń zainstalowane narzędzia, uruchamiając polecenie [odinstalowywania narzędzia dotnet:](dotnet-tool-uninstall.md)

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a>Rozwiązywanie problemów

Jeśli podczas korzystania z samouczka zostanie wyświetlony komunikat o błędzie, zobacz [Rozwiązywanie problemów z używaniem narzędzia .NET Core](troubleshoot-usage-issues.md).

## <a name="see-also"></a>Zobacz też

Aby uzyskać więcej informacji, zobacz [narzędzia .NET Core](global-tools.md)
