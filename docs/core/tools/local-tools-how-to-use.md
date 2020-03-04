---
title: 'Samouczek: Instalowanie i używanie lokalnych narzędzi platformy .NET Core'
description: Dowiedz się, jak zainstalować narzędzie .NET i korzystać z niego jako narzędzia lokalnego.
ms.date: 02/12/2020
ms.openlocfilehash: a4355886513040e2436bdbd87905e5baee2dd7a5
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156702"
---
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a>Samouczek: Instalowanie lokalnego narzędzia .NET Core i używanie go przy użyciu interfejs wiersza polecenia platformy .NET Core

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 3,0 SDK i nowszych wersjach

W tym samouczku przedstawiono sposób instalowania i używania narzędzia lokalnego. Używasz narzędzia, które tworzysz w [pierwszym samouczku tej serii](global-tools-how-to-create.md).

## <a name="prerequisites"></a>Wymagania wstępne

* Wykonaj [pierwszy samouczek tej serii](global-tools-how-to-create.md).
* Zainstaluj środowisko uruchomieniowe programu .NET Core 2,1.

  W tym samouczku zainstalujesz narzędzie, które jest przeznaczone dla platformy .NET Core 2,1, i użyjesz go, więc musisz mieć zainstalowane na maszynie środowisko uruchomieniowe. Aby zainstalować środowisko uruchomieniowe 2,1, przejdź do [strony pobierania programu .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1) i Znajdź link instalacja środowiska uruchomieniowego w kolumnie **Uruchamianie aplikacji — środowisko uruchomieniowe** .

## <a name="create-a-manifest-file"></a>Utwórz plik manifestu

Aby zainstalować narzędzie tylko do dostępu lokalnego (dla bieżącego katalogu i podkatalogów), należy dodać je do pliku manifestu.

W folderze *Microsoft. botsay* przejdź do folderu *repozytorium* w górę o jeden poziom:

```console
cd ..
```

Utwórz plik manifestu, uruchamiając polecenie [dotnet New](dotnet-new.md) :

```dotnetcli
dotnet new tool-manifest
```

Dane wyjściowe wskazują pomyślne utworzenie pliku.

```console
The template "Dotnet local tool manifest file" was created successfully.
```

Plik *config/dotnet-Tools. JSON* nie zawiera jeszcze żadnych narzędzi:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

Narzędzia wymienione w pliku manifestu są dostępne dla bieżącego katalogu i podkatalogów. Bieżącym katalogiem jest ten, który zawiera katalog *. config* z plikiem manifestu.

W przypadku korzystania z polecenia CLI odwołującego się do narzędzia lokalnego zestaw SDK wyszukuje plik manifestu w bieżącym katalogu i katalogach nadrzędnych. Jeśli odnajdzie plik manifestu, ale plik nie zawiera narzędzia, którego dotyczy odwołanie, kontynuuje wyszukiwanie za pomocą katalogów nadrzędnych. Wyszukiwanie zostanie zakończone po znalezieniu narzędzia, którego dotyczy odwołanie, lub znalezienie pliku manifestu z `isRoot`m ustawionym na `true`.

## <a name="install-botsay-as-a-local-tool"></a>Instalowanie botsay jako narzędzia lokalnego

Zainstaluj narzędzie z pakietu utworzonego w pierwszym samouczku:

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

To polecenie dodaje narzędzie do pliku manifestu, który został utworzony w poprzednim kroku. Dane wyjściowe polecenia pokazują plik manifestu, w którym znajduje się nowo zainstalowane narzędzie:

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

Plik *config/dotnet-Tools. JSON* ma teraz jedno narzędzie:

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

Wywołaj narzędzie, uruchamiając polecenie `dotnet tool run` z folderu *repozytorium* :

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a>Przywracanie lokalnego narzędzia zainstalowanego przez inne osoby

Zazwyczaj instalowane jest narzędzie lokalne w katalogu głównym repozytorium. Po zaewidencjonowaniu pliku manifestu do repozytorium inni deweloperzy mogą uzyskać najnowszy plik manifestu. Aby zainstalować wszystkie narzędzia wymienione w pliku manifestu, można uruchomić jedno `dotnet tool restore` polecenie.

1. Otwórz plik *config/dotnet-Tools. JSON* i Zastąp jego zawartość następującym kodem JSON:

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

1. Zastąp `<name>` nazwą użytą podczas tworzenia projektu.

1. Zapisz zmiany.

   Wprowadzenie tej zmiany jest takie samo jak w przypadku pobierania najnowszej wersji z repozytorium, gdy ktoś inny zainstalował pakiet `dotnetsay` dla katalogu projektu.

1. Uruchom polecenie `dotnet tool restore`.

   ```dotnetcli
   dotnet tool restore
   ```

   Polecenie generuje dane wyjściowe podobne do następującego przykładu:

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. Sprawdź, czy narzędzia są dostępne:

   ```dotnetcli
   dotnet tool list
   ```

   Dane wyjściowe to lista pakietów i poleceń, podobnie jak w poniższym przykładzie:

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

Zainstalowana wersja `dotnetsay` lokalnego narzędzia to 2.1.3.  Najnowsza wersja to 2.1.4. Aby zaktualizować narzędzie do najnowszej wersji, użyj polecenia [aktualizacji narzędzia dotnet](dotnet-tool-update.md) .

```dotnetcli
dotnet tool update dotnetsay
```

Dane wyjściowe wskazują nowy numer wersji:

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

Polecenie Update wyszukuje pierwszy plik manifestu zawierający identyfikator pakietu i aktualizuje go. Jeśli nie ma takiego identyfikatora pakietu w żadnym pliku manifestu, który znajduje się w zakresie wyszukiwania, zestaw SDK dodaje nowy wpis do najbliższego pliku manifestu. Zakres wyszukiwania znajduje się w katalogu nadrzędnym, dopóki nie zostanie znaleziony plik manifestu z `isRoot = true`.

## <a name="remove-local-tools"></a>Usuń narzędzia lokalne

Aby usunąć zainstalowane narzędzia, należy uruchomić polecenie [Narzędzia dotnet](dotnet-tool-uninstall.md) :

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a>Rozwiązywanie problemów

Jeśli podczas wykonywania samouczka zostanie wyświetlony komunikat o błędzie, zobacz [Rozwiązywanie problemów z użyciem narzędzia .NET Core](troubleshoot-usage-issues.md).

## <a name="see-also"></a>Zobacz też

Aby uzyskać więcej informacji, zobacz [Narzędzia platformy .NET Core](global-tools.md)
