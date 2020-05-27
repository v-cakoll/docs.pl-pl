---
title: Globalizacja i ICU
ms.date: 05/21/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- globalization [.NET Framework], about globalization
- global applications, globalization
- international applications [.NET Framework], globalization
- world-ready applications, globalization
- application development [.NET Framework], globalization
- culture, globalization
- icu, icu on windows, ms-icu
ms.openlocfilehash: 6ea848d4a60069e6702b9d60fd90a55f572fb043
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842528"
---
# <a name="net-globalization-and-icu"></a>Globalizacja i ICU platformy .NET

W przeszłości interfejsy API globalizacji platformy .NET używały różnych bibliotek bazowych na różnych platformach. W systemie UNIX interfejsy API używające [składników międzynarodowych dla standardu Unicode (ICU)](http://site.icu-project.org/home)i w systemie Windows używają [obsługi języków narodowych (NLS)](/windows/win32/intl/national-language-support). Spowodowało to pewne różnice w kilku globalizacji interfejsów API podczas uruchamiania aplikacji na różnych platformach. Różnice w zachowaniu były widoczne w następujących obszarach:

- Kultury i dane kulturowe
- Wielkość liter w postaci ciągów
- Sortowanie i wyszukiwanie ciągów
- Sortuj klucze
- Normalizacja ciągu
- Obsługa międzynarodowych nazw domen (IDN)
- Nazwa wyświetlana strefy czasowej w systemie Linux

Począwszy od platformy .NET 5,0, deweloperzy mają większą kontrolę nad używaną biblioteką, umożliwiając aplikacjom uniknięcie różnic między platformami.

## <a name="icu-on-windows"></a>ICU w systemie Windows

System Windows 10 maja 2019 Update i nowsze wersje zawierają [ICU. dll](/windows/win32/intl/international-components-for-unicode--icu-) w ramach systemu operacyjnego, a program .NET 5,0 i nowsze wersje domyślnie korzystają z ICU. W przypadku uruchamiania w systemie Windows program .NET 5,0 i nowsze wersje próbują załadować, `icu.dll` a jeśli jest dostępny, używa go do implementacji globalizacji.  Jeśli ta biblioteka nie może zostać znaleziona lub załadowana, na przykład w przypadku korzystania ze starszych wersji systemu Windows, program .NET 5,0 i jego nowsze wersje powracają do implementacji opartej na witrynie NLS.

> [!NOTE]
> Nawet w przypadku używania ICU, `CurrentCulture` , `CurrentUICulture` i `CurrentRegion` elementy członkowskie nadal używają interfejsów API systemu operacyjnego Windows do zapamiętania ustawień użytkownika.

### <a name="using-nls-instead-of-icu"></a>Korzystanie z programu NLS zamiast ICU

Użycie ICU zamiast NLS może spowodować różnice w działaniu z pewnymi operacjami związanymi z globalizacją. Aby wrócić do korzystania z usługi NLS, deweloper może zrezygnować z implementacji ICU. Aplikacje mogą włączać tryb NLS w dowolny z następujących sposobów:

- W pliku projektu:

```xml
<ItemGroup>
  <RuntimeHostConfigurationOption Include="System.Globalization.UseNls" Value="true" />
</ItemGroup>
```

- W pliku `runtimeconfig.json`:

```json
{
  "runtimeOptions": {
     "configProperties": {
       "System.Globalization.UseNls": true
      }
  }
}
```

- Ustawienie zmiennej środowiskowej `DOTNET_SYSTEM_GLOBALIZATION_USENLS` na wartość `true` lub `1` .

> [!NOTE]
> Wartość ustawiona w projekcie lub w `runtimeconfig.json` pliku ma pierwszeństwo przed zmienną środowiskową.

Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji w czasie wykonywania](../../core/run-time-config/globalization.md#nls).

## <a name="app-local-icu"></a>ICU lokalna aplikacji

Każda wersja programu ICU może nastąpić wraz z poprawkami błędów IT, a także z zaktualizowanymi danymi wspólnego repozytorium danych ustawień regionalnych (CLDR), które opisują języki na całym świecie. Przechodzenie między wersjami ICU może obsłużyć zachowanie aplikacji w przypadku operacji związanych z globalizacją.  Aby pomóc deweloperom aplikacji zapewnić spójność we wszystkich wdrożeniach, .NET 5,0 i nowszych wersjach, Włącz aplikacje w systemach Windows i UNIX do przenoszenia i używania własnych kopii ICU.

Aplikacje mogą zrezygnować z trybu implementacji ICU na poziomie aplikacji w trybie lokalnym na jeden z następujących sposobów:

- W pliku projektu:

```xml
<ItemGroup>
  <RuntimeHostConfigurationOption Include="System.Globalization.AppLocalIcu" Value="<suffix>:<version> or <version>" />
</ItemGroup>
```

- W pliku `runtimeconfig.json`:

```json
{
  "runtimeOptions": {
     "configProperties": {
       "System.Globalization.AppLocalIcu": "<suffix>:<version> or <version>"
      }
  }
}
```

- Ustawienie zmiennej środowiskowej `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` na wartość `<suffix>:<version>` lub `<version>` .

`<suffix>`: Opcjonalny sufiks o długości poniżej 36 znaków, zgodnie z konwencjami ICU publicznego pakietu. Podczas kompilowania niestandardowych ICU można dostosować je do tworzenia nazw lib i wyeksportowanych nazw symboli, aby zawierały sufiks, na przykład, `libicuucmyapp` gdzie `myapp` jest sufiksem.

`<version>`: Prawidłowa wersja ICU, na przykład 67,1. Ta wersja jest używana do ładowania plików binarnych i uzyskiwania eksportowanych symboli.

Aby załadować ICU w przypadku ustawienia przełącznika lokalnego aplikacji, platforma .NET używa <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> metody, która sonduje wiele ścieżek. Metoda najpierw próbuje znaleźć bibliotekę we `NATIVE_DLL_SEARCH_DIRECTORIES` właściwości, która jest tworzona przez hosta dotnet w oparciu o `deps.json` plik aplikacji. Aby uzyskać więcej informacji, zobacz [domyślne sondowanie](../../core/dependency-loading/default-probing.md).

W przypadku aplikacji, które nie są wymagane przez użytkownika, nie jest wymagana żadna specjalna akcja, inna niż upewnienie się, że ICU znajduje się w katalogu aplikacji (w przypadku aplikacji samodzielnych, domyślnie jest to katalog roboczy `NATIVE_DLL_SEARCH_DIRECTORIES` ).

Jeśli korzystasz z ICU za pośrednictwem pakietu NuGet, działa to w aplikacjach zależnych od platformy. Pakiet NuGet rozwiązuje natywne zasoby i dołącza je do `deps.json` pliku oraz do katalogu wyjściowego dla aplikacji w `runtimes` katalogu. Platforma .NET ładuje ją z tego miejsca.

W przypadku aplikacji zależnych od platformy (nie zawartych w nich), gdzie ICU jest zużywana z lokalnej kompilacji, należy wykonać dodatkowe czynności. Zestaw .NET SDK nie ma jeszcze funkcji "luźnych" natywnych plików binarnych, które mają być włączone `deps.json` (zobacz [ten problem z zestawem SDK](https://github.com/dotnet/sdk/issues/11373)). Zamiast tego można je włączyć przez dodanie dodatkowych informacji do pliku projektu aplikacji. Na przykład:

```xml
<ItemGroup>
  <IcuAssemblies Include="icu\*.so*" />
  <RuntimeTargetsCopyLocalItems Include="@(IcuAssemblies)" AssetType="native" CopyLocal="true" DestinationSubDirectory="runtimes/linux-x64/native/" DestinationSubPath="%(FileName)%(Extension)" RuntimeIdentifier="linux-x64" NuGetPackageId="System.Private.Runtime.UnicodeData" />
</ItemGroup>
```

Należy to zrobić dla wszystkich plików binarnych ICU dla obsługiwanych środowisk uruchomieniowych. Ponadto `NuGetPackageId` metadane w `RuntimeTargetsCopyLocalItems` grupie elementów muszą być zgodne z pakietem NuGet, który rzeczywiście odwołuje się do projektu.

### <a name="macos-behavior"></a>zachowanie macOS

`macOS`Program ma inne zachowanie w zakresie rozpoznawania zależnych bibliotek dynamicznych z poleceń ładowania określonych w `match-o` pliku niż moduł ładujący systemu Linux. W module ładującym systemu Linux .NET może próbować `libicudata` , `libicuuc` i `libicui18n` (w tej kolejności), aby SPEŁNIAŁ wykres zależności ICU. Jednak w macOS nie działa. Podczas kompilowania ICU na macOS, domyślnie Pobierz bibliotekę dynamiczną z tymi poleceniami ładowania w `libicuuc` . Na przykład:

```sh
~/ % otool -L /Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib
/Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib:
 libicuuc.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 libicudata.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 /usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1281.100.1)
 /usr/lib/libc++.1.dylib (compatibility version 1.0.0, current version 902.1.0)
```

Te polecenia po prostu odwołują się do nazw bibliotek zależnych dla innych składników ICU. Moduł ładujący wykonuje wyszukiwanie zgodnie z `dlopen` konwencjami, które obejmują te biblioteki w katalogach systemowych lub ustawienia `LD_LIBRARY_PATH` ENV zmiennych lub ICU w katalogu na poziomie aplikacji. Jeśli nie możesz ustawić `LD_LIBRARY_PATH` lub upewnić się, że pliki binarne ICU znajdują się w katalogu na poziomie aplikacji, musisz wykonać kilka dodatkowych czynności.

Istnieją pewne dyrektywy dotyczące modułu ładującego, takie jak `@loader_path` , które informują program ładujący, aby wyszukał Tę zależność w tym samym katalogu co plik binarny z tym poleceniem ładowania. Istnieją dwa sposoby osiągnięcia tego celu:

- `install_name_tool -change`

  Uruchom następujące polecenia:

```bash
install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicuuc.67.1.dylib
install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicui18n.67.1.dylib
install_name_tool -change "libicuuc.67.dylib" "@loader_path/libicuuc.67.dylib" /path/to/libicui18n.67.1.dylib
```

- Poprawka ICU do tworzenia nazw instalacji z`@loader_path`

  Przed uruchomieniem AUTOCONF ( `./runConfigureICU` ) Zmień [następujące wiersze](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) na:

```
LD_SONAME = -Wl,-compatibility_version -Wl,$(SO_TARGET_VERSION_MAJOR) -Wl,-current_version -Wl,$(SO_TARGET_VERSION) -install_name @loader_path/$(notdir $(MIDDLE_SO_TARGET))
```
