---
title: Utwórz nowy szablon niestandardowy dla platformy dotnet
description: Dowiedz się, jak utworzyć szablon niestandardowy dla platformy dotnet nowe polecenie w fun tego samouczka.
keywords: Szablonu .NET i .NET core, tworzenia szablonów, samouczek, dotnet nowy
author: guardrex
ms.author: mairaw
ms.date: 08/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 519b910a-6efe-4394-9b81-0546aa3e7462
ms.workload:
- dotnetcore
ms.openlocfilehash: 7830a437b46d2080efc65f43f9112503add4c305
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="create-a-custom-template-for-dotnet-new"></a>Utwórz nowy szablon niestandardowy dla platformy dotnet

W tym samouczku przedstawiono sposób do:

- Utwórz szablon podstawowy z istniejącego projektu lub nowy projekt aplikacji konsoli.
- Pakiet szablonu w celu dystrybucji w nuget.org lub z lokalnego *nupkg* pliku.
- Zainstaluj szablonu z nuget.org, lokalnym *nupkg* pliku lub lokalnego systemu plików.
- Odinstaluj szablonu.

Jeśli wolisz przejdź przez samouczek z kompletnego przykładu, Pobierz [przykładowy szablon projektu](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package). Przykładowy szablon jest skonfigurowany do dystrybucji NuGet.

Jeśli chcesz użyć przykładowego pobranego z dystrybucji systemu plików, wykonaj następujące czynności:

- Przenieś zawartość *zawartości* folderu próbki o jeden poziom w górę *GarciaSoftware.ConsoleTemplate.CSharp* folderu.
- Usuń wszystkie puste *zawartości* folderu.
- Usuń *nuspec* pliku.

## <a name="prerequisites"></a>Wymagania wstępne

- Zainstaluj [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) lub nowszy.
- Przeczytaj temat odwołanie [dotnet nowych szablonów niestandardowych](../tools/custom-templates.md).

## <a name="create-a-template-from-a-project"></a>Tworzenie szablonu z projektu

Użyj istniejącego projektu, który został potwierdzony kompiluje i uruchamia lub Utwórz nowy projekt aplikacji konsoli w folderze na dysku twardym. Ten samouczek zakłada, że nazwa folderu projektu *GarciaSoftware.ConsoleTemplate.CSharp* przechowywane w *Documents\Templates* w profilu użytkownika. Projekt samouczka Nazwa szablonu jest w formacie  *\<nazwa firmy >.\< Typ szablonu >. \<Języka programowania >*, ale można go dowolnie nazwa szablon i projektu niczego ma.

1. Dodaj folder do katalogu głównego projektu o nazwie *. template.config*.
1. Wewnątrz *. template.config* folderu, Utwórz *template.json* plik, aby skonfigurować szablon. Więcej informacji i element członkowski definicje dla *template.json* plików, zobacz [dotnet nowych szablonów niestandardowych](../tools/custom-templates.md#templatejson) tematu i [ *template.json* schemat w magazynie schematów JSON](http://json.schemastore.org/template).

```json
{
    "$schema": "http://json.schemastore.org/template",
    "author": "Catalina Garcia",
    "classifications": [ "Common", "Console" ],
    "identity": "GarciaSoftware.ConsoleTemplate.CSharp",
    "name": "Garcia Software Console Application",
    "shortName": "garciaconsole"
}
```

Szablon został zakończony. W tym momencie masz dwie opcje dystrybucji szablonu. Aby kontynuować, w tym samouczku, wybierz jedną ścieżkę lub innych:

1. [Dystrybucji NuGet](#use-nuget-distribution): Zainstaluj szablonu z NuGet lub lokalnej *nupkg* i użycie szablonu zainstalowane.
2. [Plik dystrybucji systemu](#use-file-system-distribution).

## <a name="use-nuget-distribution"></a>Użyj dystrybucji NuGet

### <a name="pack-the-template-into-a-nuget-package"></a>Pakiet szablonu do pakietu NuGet

1. Utwórz folder pakietu NuGet. Samouczek, nazwy folderu *GarciaSoftware.ConsoleTemplate.CSharp* jest używany, oraz folder jest tworzony w *Documents\NuGetTemplates* folderu w profilu użytkownika. Utwórz folder o nazwie *zawartości* wewnątrz nowego szablonu folderu do przechowywania plików projektu.
1. Kopiuj zawartość folderu projektu, wraz z jego *.template.config/template.json* pliku, do *zawartości* utworzony folder.
1. Obok pozycji *zawartości* folderu, Dodaj [ *nuspec* pliku](/nuget/create-packages/creating-a-package). Plik nuspec jest plik manifestu XML, który opisuje zawartość pakietu i dyskach proces tworzenia pakietu NuGet.
   
   ![Struktura katalogów przedstawiający układ pakietu NuGet](./media/create-custom-template/nugetdirectorylayout.png)

1. Wewnątrz  **\<packageTypes >** element *nuspec* plików, obejmują  **\<packageType >** element z `name` wartość atrybutu `Template`. Zarówno *zawartości* folderu i *nuspec* plik powinien znajdować się w tym samym katalogu. W tabeli przedstawiono minimum *nuspec* pliku elementy wymagane do tworzenia szablonu jako pakietu NuGet.

   | Element            | Typ   | Opis |
   | ------------------ | ------ | ----------- |
   | **\<Autorzy >**     | string | Rozdzielana przecinkami lista autorzy pakietów, zgodne z nazwami profilu na nuget.org. Autorzy są wyświetlane w galerii NuGet w nuget.org i są odwoływania się do pakietów przez tego samego autorów. |
   | **\<Opis elementu >** | string | Długi opis pakietu do wyświetlenia interfejsu użytkownika. |
   | **\<id>**          | string | Identyfikator pakietu bez uwzględniania wielkości liter, który musi być unikatowa w nuget.org lub niezależnie od pakietu będą znajdować się w galerii. Identyfikatory nie może zawierać spacji ani znaków, które nie są prawidłowe dla danego adresu URL i ogólnie zgodne reguły obszaru nazw .NET. Zobacz [wybranie identyfikator unikatowy pakiet i ustawianie numeru wersji](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) orientacji. |
   | **\<packageType>** | string | Umieść ten element wewnątrz  **\<packageTypes >** element między  **\<metadanych >** elementów. Ustaw `name` atrybutu  **\<packageType >** elementu `Template`. |
   | **\<Wersja >**     | string | Wersja pakietu, następujące wzorzec Wersja_główna.WERSJA_POMOCNICZA.poprawka. Numery wersji może zawierać sufiks wersji wstępnej, zgodnie z opisem w [wersje wstępne](/nuget/create-packages/prerelease-packages#semantic-versioning). |

   Zobacz [odwołania .nuspec](/nuget/schema/nuspec) dla pełnej *nuspec* pliku schematu.

   *Nuspec* plik o nazwie samouczka *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* i zawiera następującą zawartość:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns="http://schemas.microsoft.com/packaging/2012/06/nuspec.xsd">
     <metadata>
       <id>GarciaSoftware.ConsoleTemplate.CSharp</id>
       <version>1.0.0</version>
       <description>
         Creates the Garcia Software console app.
       </description>
       <authors>Catalina Garcia</authors>
       <packageTypes>
         <packageType name="Template" />
       </packageTypes>
     </metadata>
   </package>
   ```

1. [Utwórz pakiet](/nuget/create-packages/creating-a-package#creating-the-package) przy użyciu `nuget pack <PATH_TO_NUSPEC_FILE>` polecenia. Polecenie zakłada, że folder, który zawiera zasoby NuGet w *C:\Users\\\<użytkownika > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*. Ale wszędzie tam, gdzie umieścić folder w systemie, `nuget pack` polecenie akceptuje ścieżkę do *nuspec* pliku:

   ```console
   nuget pack C:\Users\<USER>\Documents\NuGetTemplates\GarciaSoftware.ConsoleTemplate.CSharp\GarciaSoftware.ConsoleTemplate.CSharp.nuspec
   ```

### <a name="publishing-the-package-to-nugetorg"></a>Publikowanie pakietu nuget.org

Aby opublikować pakietu NuGet, postępuj zgodnie z instrukcjami w [tworzenie i publikowanie pakietu](/nuget/quickstart/create-and-publish-a-package#publish-the-package) tematu. Firma Microsoft zaleca jednak nie opublikowanie samouczek szablonu NuGet jako nigdy nie można usunąć go po opublikowaniu tylko delisted. Teraz, gdy masz pakiet NuGet w formie *nupkg* plików, zalecamy postępuj zgodnie z instrukcjami poniżej, aby zainstalować szablon bezpośrednio z lokalnej *nupkg* pliku.

### <a name="install-the-template-from-a-nuget-package"></a>Zainstaluj szablonu z pakietem NuGet

#### <a name="install-the-template-from-the-local-nupkg-file"></a>Zainstaluj szablonu z lokalnej *nupkg* pliku

Aby zainstalować szablon z *nupkg* pliku wytworzonego, użyj `dotnet new` z `-i|--install` opcję i wprowadź ścieżkę do *nupkg* pliku:

```console
dotnet new -i C:\Users\<USER>\GarciaSoftware.ConsoleTemplate.CSharp.1.0.0.nupkg
```

#### <a name="install-the-template-from-a-nuget-package-stored-at-nugetorg"></a>Zainstaluj szablonu z pakietem NuGet przechowywane w nuget.org

Jeśli chcesz zainstalować szablonu z przechowywanych na nuget.org, użyj pakietu NuGet `dotnet new` z `-i|--install` opcji i podaj nazwę pakietu NuGet:

```console
dotnet new -i GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> Przykładem jest tylko w celach demonstracyjnych. Nie ma `GarciaSoftware.ConsoleTemplate.CSharp` pakietu NuGet w nuget.org, i nie zaleca się można opublikować i korzystać z szablonów testu z NuGet. Jeśli polecenie zostanie uruchomione, jest zainstalowany żaden szablon. Można jednak zainstalować szablon, który nie został opublikowany nuget.org odwołując *nupkg* pliku bezpośrednio w lokalnym systemie plików, jak pokazano w poprzedniej sekcji [zainstalować szablon z lokalnym nupkg plik](#install-the-template-from-the-local-nupkg-file).

Jeśli chcesz na żywo przykład sposobu instalowania szablonu z pakietu w nuget.org, możesz użyć [NUnit 3 szablon dla nowych dotnet](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/). Ten szablon ustawia się na projekt do przeprowadzania testów jednostkowych NUnit użycia. Aby go zainstalować, użyj następującego polecenia:

```console
dotnet new -i NUnit3.DotNetNew.Template
```

Podczas wyświetlania szablonów `dotnet new -l`, zostanie wyświetlony *projekt testowy 3 NUnit* z krótką nazwę *nunit* na liście szablonów. Możesz użyć szablonu w następnej sekcji.

![Wyświetlana NUnit szablonu na liście z innych szablonów zainstalowanych w oknie konsoli](./media/create-custom-template/nunit1.png)

### <a name="create-a-project-from-the-template"></a>Tworzenie projektu z szablonu

Po zainstalowaniu szablonu z pakietu NuGet, należy użyć szablonu, wykonując `dotnet new <TEMPLATE>` umieścić wyjściowy polecenia z katalogu, w którym ma zostać aparatu szablonu (chyba że `-o|--output` opcję, aby określić określonego katalogu). Aby uzyskać więcej informacji, zobacz [ `dotnet new` opcje](~/docs/core/tools/dotnet-new.md#options). Podaj krótką nazwę szablonu bezpośrednio do `dotnet new` polecenia. Aby utworzyć projekt z szablonu NUnit, uruchom następujące polecenie:

```console
dotnet new nunit
```

Konsoli Pokazuje tworzenia projektu i przywracania pakietów projektu. Po uruchomieniu polecenia Projekt jest gotowy do użycia.

![Okno konsoli wyświetlane dane wyjściowe polecenia Nowy dotnet tworzy projekt NUnit i przywraca zależności projektu](./media/create-custom-template/nunit2.png)

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Aby odinstalować szablonu z pakietem NuGet przechowywane w nuget.org

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> Przykładem jest tylko w celach demonstracyjnych. Nie ma `GarciaSoftware.ConsoleTemplate.CSharp` NuGet zainstalowany przy użyciu zestawu .NET Core SDK lub pakietu w nuget.org. Po uruchomieniu polecenia pakietu/szablonu zostanie odinstalowana i pojawi się następujący wyjątek:
> 
> > Nie można znaleźć elementu odinstalować o nazwie "GarciaSoftware.ConsoleTemplate.CSharp".

Jeśli zainstalowano [NUnit 3 szablon dla nowych dotnet](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) i chcesz go odinstalować, użyj następującego polecenia:

```console
dotnet new -u NUnit3.DotNetNew.Template
```

### <a name="uninstall-the-template-from-a-local-nupkg-file"></a>Odinstaluj szablonu z pliku lokalnego nupkg

Jeśli chcesz odinstalować szablonu nie próbuj Użyj ścieżki do *nupkg* pliku. *Podjęto próbę ją odinstalować przy użyciu szablonu `dotnet new -u <PATH_TO_NUPKG_FILE>` zakończy się niepowodzeniem.* Odwołują się do pakietu przez jego `id`:

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp.1.0.0
```

## <a name="use-file-system-distribution"></a>Użyj dystrybucji systemu plików

Do dystrybucji szablonu, umieścić w folderze szablonów projektu w lokalizacji dostępne dla użytkowników w sieci. Użyj `dotnet new` z `-i|--install` opcji i określ ścieżkę do folderu szablonu (folder projekt zawierający projekt i *. template.config* folderu).

W tym samouczku założono szablon projektu jest przechowywany w *dokumenty/szablonów* folderu profilu użytkownika. Z tej lokalizacji, należy zainstalować szablon z zastąpienia następujące polecenia \<użytkownika > o nazwie profilu użytkownika:

```console
dotnet new -i C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

### <a name="create-a-project-from-the-template"></a>Tworzenie projektu z szablonu

Po zainstalowaniu szablonu z systemu plików za pomocą szablonu, wykonując `dotnet new <TEMPLATE>` umieścić wyjściowy polecenia z katalogu, w którym ma zostać aparatu szablonu (chyba że `-o|--output` opcję, aby określić określonego katalogu). Aby uzyskać więcej informacji, zobacz [ `dotnet new` opcje](~/docs/core/tools/dotnet-new.md#options). Podaj krótką nazwę szablonu bezpośrednio do `dotnet new` polecenia.

Z folderu projektu utworzonego w dniu *C:\Users\\\<użytkownika > \Documents\Projects\MyConsoleApp*, Utwórz projekt z `garciaconsole` szablonu:

```console
dotnet new garciaconsole
```

### <a name="uninstall-the-template"></a>Odinstaluj szablonu

Jeśli szablon został utworzony w lokalnym systemie plików w *C:\Users\\\<użytkownika > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, odinstaluj je z `-u|--uninstall` przełącznika i ścieżki folder szablonu:

```console
dotnet new -u C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> Aby odinstalować szablonu z lokalnego systemu plików, należy do pełnej kwalifikacji ścieżki. Na przykład *C:\Users\\\<użytkownika > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego nie będzie.
> Ponadto nie należy dołączać końcowego ukośnika katalogu zakończenia ścieżki szablonu.

## <a name="see-also"></a>Zobacz także

[repozytorium GitHub DotNet/tworzenia szablonów Wiki](https://github.com/dotnet/templating/wiki)  
[repozytorium GitHub DotNet/dotnet szablonu — przykłady](https://github.com/dotnet/dotnet-template-samples)  
[Jak utworzyć nowe szablony dla platformy dotnet](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)  
[*Template.JSON* schematu w magazynie schematów JSON](http://json.schemastore.org/template)  
