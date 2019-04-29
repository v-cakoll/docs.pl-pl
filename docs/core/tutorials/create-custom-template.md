---
title: Utwórz nowy szablon niestandardowy dla platformy dotnet
description: Dowiedz się, jak utworzyć niestandardowy szablon dla nowego polecenia dotnet w tę zabawną samouczka.
author: guardrex
ms.date: 08/12/2017
ms.custom: seodec18
ms.openlocfilehash: 3b45a24c8a249eeb99fb1a4b14918483b978980b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647403"
---
# <a name="create-a-custom-template-for-dotnet-new"></a>Utwórz nowy szablon niestandardowy dla platformy dotnet

Ten samouczek pokazuje, jak do:

- Utwórz szablon podstawowy z istniejący projekt lub nowy projekt aplikacji konsoli.
- Pakiet szablonu do dystrybucji, w witrynie nuget.org lub z lokalnym *nupkg* pliku.
- Zainstalować szablon z witryny nuget.org-lokalnego *nupkg* pliku lub w lokalnym systemie plików.
- Odinstaluj szablonu.

Jeśli wolisz postępuj zgodnie z instrukcjami samouczek z pełny przykład, Pobierz [przykładowy szablon projektu](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package). Przykładowy szablon jest skonfigurowany do dystrybucji NuGet.

Jeśli chcesz korzystać z pobranych próbki z dystrybucją systemu plików, wykonaj następujące czynności:

- Przenieś zawartość *zawartości* folderu próbki do góry o jeden poziom do *GarciaSoftware.ConsoleTemplate.CSharp* folderu.
- Usuwanie pustych *zawartości* folderu.
- Usuń *nuspec* pliku.

## <a name="prerequisites"></a>Wymagania wstępne

- Zainstaluj [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) lub nowszy.
- Zapoznaj się z tematem odwołanie [szablonów niestandardowych dla platformy dotnet nowe](../tools/custom-templates.md).

## <a name="create-a-template-from-a-project"></a>Utwórz szablon z projektu

Użyj istniejącego projektu, który został potwierdzony kompiluje i uruchamia lub utworzyć nowy projekt aplikacji konsoli w folderze na dysku twardym. Ten samouczek zakłada, że nazwa folderu projektu jest *GarciaSoftware.ConsoleTemplate.CSharp* przechowywaną w *Documents\Templates* w profilu użytkownika. Nazwa szablonu w projekcie samouczka jest w formacie  *\<nazwa firmy >.\< Typ szablonu >. \<Język programowania >*, ale możesz nazwę projektu i szablon wszystko chcesz.

1. Dodawanie folderu do katalogu głównego projektu o nazwie *. template.config*.
1. Wewnątrz *. template.config* folderze utwórz *template.json* pliku, aby skonfigurować szablon. Aby uzyskać więcej informacji i elementów członkowskich definicje *template.json* plików, zobacz [szablonów niestandardowych dla platformy dotnet nowe](../tools/custom-templates.md#templatejson) tematu i [ *template.json* schemat w Store schematu JSON](http://json.schemastore.org/template).

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

Szablon jest ukończona. W tym momencie masz dwie opcje dystrybucji szablonu. Aby kontynuować z tego samouczka, wybierz jedną ścieżkę lub innych:

1. [NuGet dystrybucji](#use-nuget-distribution): Zainstaluj szablonu z pakietów NuGet lub z lokalnego *nupkg* i użycie zainstalowanych szablonów.
2. [Plik dystrybucji systemu](#use-file-system-distribution).

## <a name="use-nuget-distribution"></a>Użyj rozkładu NuGet

### <a name="pack-the-template-into-a-nuget-package"></a>Pakiet szablonu do pakietu NuGet

1. Utwórz folder dla pakietu NuGet. Samouczek, nazwa folderu *GarciaSoftware.ConsoleTemplate.CSharp* jest używany, oraz folder jest tworzony w *Documents\NuGetTemplates* folderu w profilu użytkownika. Utwórz folder o nazwie *zawartości* wewnątrz folder szablonów do przechowywania plików projektu.
1. Skopiuj zawartość do folderu projektu, łącznie z jej *.template.config/template.json* pliku do *zawartości* utworzony folder.
1. Obok pozycji *zawartości* folderu, Dodaj [ *nuspec* pliku](/nuget/create-packages/creating-a-package). Soubor nuspec jest plik manifestu XML, który opisuje zawartość pakietu i dyski proces tworzenia pakietu NuGet.

   ![Struktura katalogów przedstawiający układ pakietu NuGet](./media/create-custom-template/nuget-directory-layout.png)

1. Wewnątrz  **\<packageTypes >** element *nuspec* plików, obejmują  **\<packageType >** element z `name` wartość atrybutu `Template`. Zarówno *zawartości* folder i *nuspec* plik powinien znajdować się w tym samym katalogu. W tabeli przedstawiono minimalne *nuspec* pliku elementów wymaganych do utworzenia szablonu jako pakiet NuGet.

   | Element            | Typ   | Opis |
   | ------------------ | ------ | ----------- |
   | **\<authors>**     | string | Rozdzielana przecinkami lista autorów pakietów, pasujące nazwy profilu w witrynie nuget.org. Autorzy są wyświetlane w galerii pakietów NuGet w witrynie nuget.org i są odwoływania się do pakietów przez ten sam autorów. |
   | **\<description>** | string | Długi opis pakietu do wyświetlania w interfejsie użytkownika. |
   | **\<id>**          | string | Identyfikator pakietu bez uwzględniania wielkości liter, który musi być unikatowa w witrynie nuget.org lub cokolwiek innego pakietu będą znajdować się w galerii. Identyfikatory nie może zawierać spacji ani znaków, które nie są prawidłowe dla danego adresu URL i zazwyczaj korzystają z reguły w przestrzeni nazw .NET. Zobacz [wybierając identyfikator unikatowy pakiet i ustawiania numeru wersji](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) wskazówki. |
   | **\<packageType>** | string | Umieść ten element wewnątrz  **\<packageTypes >** element między  **\<metadanych >** elementów. Ustaw `name` atrybutu  **\<packageType >** elementu `Template`. |
   | **\<version>**     | string | Wersja pakietu, następujące Wersja_główna.WERSJA_POMOCNICZA.poprawka. Numery wersji mogą zawierać sufiks wersji wstępnej, zgodnie z opisem w [wersje wstępne](/nuget/create-packages/prerelease-packages#semantic-versioning). |

   Zobacz [odwołania .nuspec](/nuget/schema/nuspec) dla pełnego *nuspec* pliku schematu.

   *Nuspec* plik o nazwie samouczka *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* i zawiera następujące treści:

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

1. [Utwórz pakiet](/nuget/create-packages/creating-a-package#creating-the-package) przy użyciu `nuget pack <PATH_TO_NUSPEC_FILE>` polecenia. Poniższego polecenia założono, że folder, który zawiera zasoby NuGet jest na *C:\Users\\\<użytkownika > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*. Jednak wszędzie tam, gdzie umieścić folder, w tym systemie `nuget pack` polecenie akceptuje ścieżkę do *nuspec* pliku:

   ```console
   nuget pack C:\Users\<USER>\Documents\NuGetTemplates\GarciaSoftware.ConsoleTemplate.CSharp\GarciaSoftware.ConsoleTemplate.CSharp.nuspec
   ```

### <a name="publishing-the-package-to-nugetorg"></a>Publikowanie pakietu na stronie nuget.org

Aby opublikować pakiet NuGet, postępuj zgodnie z instrukcjami [tworzenie i publikowanie pakietu](/nuget/quickstart/create-and-publish-a-package#publish-the-package) tematu. Firma Microsoft zaleca jednak nie opublikowanie szablonu samouczek NuGet jako nigdy nie można usunąć go po opublikowaniu tylko delisted. Teraz, gdy pakiet NuGet w formie *nupkg* plików, zalecamy postępuj zgodnie z poniższymi instrukcjami, aby zainstalować szablon bezpośrednio z poziomu lokalnej *nupkg* pliku.

### <a name="install-the-template-from-a-nuget-package"></a>Zainstaluj szablonu z pakietu NuGet

#### <a name="install-the-template-from-the-local-nupkg-file"></a>Zainstaluj szablonu z lokalnego *nupkg* pliku

Aby zainstalować szablonu z *nupkg* pliku wytworzonego, użyj `dotnet new` polecenia `-i|--install` opcji i podaj ścieżkę do *nupkg* pliku:

```console
dotnet new -i C:\Users\<USER>\GarciaSoftware.ConsoleTemplate.CSharp.1.0.0.nupkg
```

#### <a name="install-the-template-from-a-nuget-package-stored-at-nugetorg"></a>Zainstaluj szablonu z pakietu NuGet, przechowywane w witrynie nuget.org

Jeśli chcesz zainstalować szablonu z przechowywaną w witrynie nuget.org, użyj pakietu NuGet `dotnet new` polecenia `-i|--install` opcji, a następnie podaj nazwę pakietu NuGet:

```console
dotnet new -i GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> W przykładzie występuje tylko w celach demonstracyjnych. Nie ma `GarciaSoftware.ConsoleTemplate.CSharp` pakietu NuGet w witrynie nuget.org, a firma Microsoft nie jest zalecane, możesz publikować i korzystanie z szablonów testowych z pakietów NuGet. Jeśli zostanie uruchomione polecenie szablon nie jest zainstalowany. Można jednak zainstalować szablon, który nie został opublikowany na stronie nuget.org, odwołując się do *nupkg* plików bezpośrednio w lokalnym systemie plików, jak pokazano w poprzedniej sekcji [zainstalować szablon z lokalnym nupkg plik](#install-the-template-from-the-local-nupkg-file).

Jeśli chcesz na żywo przykładem sposobu instalowania szablonu z pakietu w witrynie nuget.org, możesz użyć [szablon NUnit 3-dotnet new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/). Ten szablon konfiguruje projektu, aby użyć testów jednostkowych NUnit. Aby go zainstalować, użyj następującego polecenia:

```console
dotnet new -i NUnit3.DotNetNew.Template
```

Po wyświetleniu listy szablonów za pomocą `dotnet new -l`, zostanie wyświetlony *NUnit 3 Test projekt* nazwą krótkim *nunit* na liście szablonów. Możesz użyć szablonu w następnej sekcji.

![Okno konsoli przedstawiający szablon NUnit z innych szablonów](./media/create-custom-template/nunit-template-console-window.png)

### <a name="create-a-project-from-the-template"></a>Tworzenie projektu z szablonu

Po zainstalowaniu szablonu z pakietów NuGet, należy użyć szablonu, wykonując `dotnet new <TEMPLATE>` polecenie z katalogu, w którym chcesz aparatu szablonów danych wyjściowych umieszczone (chyba że `-o|--output` opcję, aby określić określonego katalogu). Aby uzyskać więcej informacji, zobacz [ `dotnet new` opcje](~/docs/core/tools/dotnet-new.md#options). Podaj krótką nazwę szablonu bezpośrednio do `dotnet new` polecenia. Aby utworzyć projekt z szablonu NUnit, uruchom następujące polecenie:

```console
dotnet new nunit
```

Konsolę pokazuje, że projekt zostanie utworzony i czy projektu pakiety zostaną przywrócone. Po uruchomieniu polecenia Projekt jest gotowy do użycia.

![Oknie konsoli zostaną wyświetlone dane wyjściowe nunit nowe dotnet, w tym Przywracanie zależności projektu](./media/create-custom-template/dotnet-new-nunit-console-output.png)

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Aby odinstalować szablonu z pakietu NuGet, przechowywane w witrynie nuget.org

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> W przykładzie występuje tylko w celach demonstracyjnych. Nie ma `GarciaSoftware.ConsoleTemplate.CSharp` NuGet zainstalowany przy użyciu zestawu .NET Core SDK lub pakietu w witrynie nuget.org. Jeśli zostanie uruchomione polecenie pakietu/szablon nie zostanie odinstalowany i pojawi się następujący wyjątek:
>
> > Nie można odnaleźć coś do odinstalowania o nazwie "GarciaSoftware.ConsoleTemplate.CSharp".

Po zainstalowaniu [NUnit 3 szablon dla nowych dotnet](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) i chcesz je odinstalować, użyj następującego polecenia:

```console
dotnet new -u NUnit3.DotNetNew.Template
```

### <a name="uninstall-the-template-from-a-local-nupkg-file"></a>Odinstaluj szablonu z pliku lokalnego nupkg

Jeśli chcesz odinstalować szablonu nie próbują użyć ścieżki do *nupkg* pliku. *Podjęto próbę ją odinstalować przy użyciu szablonu `dotnet new -u <PATH_TO_NUPKG_FILE>` zakończy się niepowodzeniem.* Odwołują się do pakietu, jego `id`:

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp.1.0.0
```

## <a name="use-file-system-distribution"></a>Użyj dystrybucji systemu plików

Aby dystrybuować szablonu, umieść folderu szablonu projektu w lokalizacji dostępne dla użytkowników w sieci. Użyj `dotnet new` polecenia `-i|--install` opcji, a następnie określ ścieżkę do folderu szablonu (folder projektu, zawierający projekt i *. template.config* folder).

W samouczku przyjęto założenie, szablon projektu jest przechowywany w *dokumenty/szablonów* folderu profilu użytkownika. Z tej lokalizacji, należy zainstalować szablon przy użyciu polecenia następujących, zastępując \<użytkownika > o nazwie profilu użytkownika:

```console
dotnet new -i C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

### <a name="create-a-project-from-the-template"></a>Tworzenie projektu z szablonu

Po zainstalowaniu szablonu z systemu plików, należy użyć szablonu, wykonując `dotnet new <TEMPLATE>` polecenie z katalogu, w którym chcesz aparatu szablonów danych wyjściowych umieszczone (chyba że `-o|--output` opcję, aby określić określonego katalogu). Aby uzyskać więcej informacji, zobacz [ `dotnet new` opcje](~/docs/core/tools/dotnet-new.md#options). Podaj krótką nazwę szablonu bezpośrednio do `dotnet new` polecenia.

Z folderu projektu utworzono *C:\Users\\\<użytkownika > \Documents\Projects\MyConsoleApp*, Utwórz projekt z `garciaconsole` szablonu:

```console
dotnet new garciaconsole
```

### <a name="uninstall-the-template"></a>Odinstaluj szablonu

Jeśli szablon został utworzony w lokalnym systemie plików w *C:\Users\\\<użytkownika > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, odinstaluj je za pomocą `-u|--uninstall` przełącznika i ścieżki do folderu szablonu:

```console
dotnet new -u C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> Aby odinstalować szablonu z lokalnego systemu plików, należy do pełnej kwalifikacji ścieżki. Na przykład *C:\Users\\\<użytkownika > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* będzie działać, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z folderu zawierającego nie będzie.
> Ponadto zawiera końcowego ukośnika katalogu kończącego w zmiennej path szablonu.

## <a name="see-also"></a>Zobacz także

- [repozytorium GitHub DotNet/szablonów witryny typu Wiki](https://github.com/dotnet/templating/wiki)
- [repozytorium GitHub DotNet/dotnet-— przykłady szablonów](https://github.com/dotnet/dotnet-template-samples)
- [Jak utworzyć nowe szablony dla platformy dotnet](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [*Template.JSON* schemat w Store schematu JSON](http://json.schemastore.org/template)
