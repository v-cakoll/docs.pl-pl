---
title: Generator EDM (EdmGen.exe)
ms.date: 03/30/2017
ms.assetid: fe8297a1-1fc3-48ce-8eeb-f70f63f857aa
ms.openlocfilehash: 82166782e25cb7a7ea23fe7faf7a30cb0e68d631
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854719"
---
# <a name="edm-generator-edmgenexe"></a>Generator EDM (EdmGen.exe)

EdmGen. exe to narzędzie wiersza polecenia służące do pracy z modelem i plikami mapowania Entity Framework. Za pomocą narzędzia EdmGen. exe można wykonać następujące czynności:

- Nawiązywanie połączenia ze źródłem danych przy użyciu dostawcy danych .NET Framework określonego przez źródło danych i generowanie modelu koncepcyjnego (. csdl), modelu magazynu (. ssdl) i plików mapowania (. MSL), które są używane przez Entity Framework. Aby uzyskać więcej informacji, zobacz [jak: Użyj programu EdmGen. exe, aby wygenerować model i pliki](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)mapowania.

- Zweryfikuj istniejący model. Aby uzyskać więcej informacji, zobacz [jak: Użyj EdmGen. exe do walidacji modelu i plików](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)mapowania.

- Generuj plik C# kodu lub Visual Basic, który zawiera klasy obiektów generowane na podstawie pliku modelu koncepcyjnego (CSDL). Aby uzyskać więcej informacji, zobacz [jak: Użyj EdmGen. exe, aby wygenerować kod](how-to-use-edmgen-exe-to-generate-object-layer-code.md)warstwy obiektu.

- Generuj plik C# kodu lub Visual Basic zawierający wstępnie wygenerowane widoki dla istniejącego modelu. Aby uzyskać więcej informacji [, jak: Wstępnie Generuj widoki, aby zwiększyć wydajność](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))zapytań.

Narzędzie EdmGen. exe jest instalowane w katalogu .NET Framework. W wielu przypadkach znajduje się to w C:\windows\Microsoft.NET\Framework\v4.0. W przypadku systemów 64-bitowych ten program znajduje się w C:\windows\Microsoft.NET\Framework64\v4.0. Możesz również uzyskać dostęp do narzędzia EdmGen. exe z wiersza polecenia programu Visual Studio (kliknij przycisk **Start**, wskaż **Wszystkie programy**, wskaż **Microsoft Visual Studio 2010**, wskaż **Visual Studio Tools**, a następnie kliknij przycisk **Visual Studio 2010 Wiersz polecenia**).

## <a name="syntax"></a>Składnia

```
EdmGen /mode:choice [options]
```

## <a name="mode"></a>Tryb

W przypadku korzystania z narzędzia EdmGen. exe należy określić jeden z następujących trybów.

|Tryb|Opis|
|----------|-----------------|
|`/mode:ValidateArtifacts`|Sprawdza poprawność plików CSDL, SSDL i MSL oraz wyświetla błędy lub ostrzeżenia.<br /><br /> Ta opcja wymaga co najmniej jednego `/inssdl` argumentu lub. `/incsdl` Jeśli `/inmsl` jest określona `/inssdl` , wymagane są `/incsdl` również argumenty i.|
|`/mode:FullGeneration`|Program używa informacji o połączeniu z bazą danych `/connectionstring` określonych w opcji i generuje pliki CSDL, SSDL, MSL, warstwy obiektów i wyświetlaj.<br /><br /> Ta opcja `/connectionstring` wymaga argumentu oraz `/outssdl` `/project` `/outcsdl` argumentu,`/outviews` ,,`/entitycontainer` ,,, i argumentów. `/outmsdl` `/outobjectlayer` `/namespace`|
|`/mode:FromSSDLGeneration`|Generuje pliki CSDL i MSL, kod źródłowy i widoki z określonego pliku SSDL.<br /><br /> Ta opcja `/inssdl` wymaga argumentu oraz `/project` argumentu `/outobjectlayer` `/outmsl` `/outcsdl` lubargumentów`/namespace,` ,, ,,`/entitycontainer` i. `/outviews`|
|`/mode:EntityClassGeneration`|Tworzy plik kodu źródłowego, który zawiera klasy wygenerowane z pliku CSDL.<br /><br /> Ta opcja wymaga `/incsdl` argumentu oraz `/project` argumentu lub `/outobjectlayer` argumentu. `/language` Argument jest opcjonalny.|
|`/mode:ViewGeneration`|Tworzy plik kodu źródłowego, który zawiera widoki wygenerowane na podstawie plików. csdl,. ssdl i. MSL.<br /><br /> Ta `/inssdl`opcja wymaga argumentów`/outviews` , `/incsdl`i. `/inmsl,` `/project` `/language` Argument jest opcjonalny.|

## <a name="options"></a>Opcje

|Opcja|Opis|
|------------|-----------------|
|`/p[roject]:`\<ciąg >|Określa nazwę projektu do użycia. Nazwa projektu jest używana jako wartość domyślna dla ustawienia przestrzeń nazw, nazwa modelu i pliki mapowania, nazwa pliku źródłowego obiektu i nazwa pliku źródłowego generacji widoku. Nazwa kontenera jednostek jest ustawiona na \<kontekst > projektu.|
|`/prov[ider]:`\<ciąg >|Nazwa dostawcy danych .NET Framework, który ma zostać użyty do wygenerowania pliku modelu magazynu (SSDL). Domyślny dostawca to .NET Framework Dostawca danych dla SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>).|
|`/c[onnectionstring]:`\<> parametrów połączenia|Określa ciąg, który jest używany do nawiązywania połączenia ze źródłem danych.|
|`/incsdl:`\<file>|Określa plik CSDL lub katalog, w którym znajdują się pliki. csdl. Ten argument można określić wiele razy, aby można było określić kilka katalogów lub plików CSDL. Określenie wielu katalogów może być przydatne w przypadku generowania klas`/mode:EntityClassGeneration`() lub widoków`/mode:ViewGeneration`(), gdy model koncepcyjny jest podzielony na kilka plików. Może to być przydatne, jeśli chcesz sprawdzić poprawność wielu modeli`/mode:ValidateArtifacts`().|
|`/refcsdl:`\<file>|Określa dodatkowy plik. csdl lub pliki używane do rozwiązywania wszelkich odwołań w źródłowym pliku CSDL. (Plik. CSDL jest plikiem, który jest określony przez `/incsdl` opcję). `/refcsdl` Plik zawiera typy, od których zależy plik source. csdl. Ten argument można określić wiele razy.|
|`/inmsl:`\<file>|Określa plik. MSL lub katalog, w którym znajdują się pliki. MSL. Ten argument można określić wiele razy, aby można było określić kilka katalogów lub plików MSL. Określenie wielu katalogów może być przydatne w przypadku generowania widoków`/mode:ViewGeneration`(), gdy model koncepcyjny jest podzielony na kilka plików. Może to być przydatne, jeśli chcesz sprawdzić poprawność wielu modeli`/mode:ValidateArtifacts`().|
|`/inssdl:`\<file>|Określa plik SSDL lub katalog, w którym znajduje się plik. SSDL. Ten argument można określić wiele razy, aby można było określić kilka katalogów lub plików SSDL. Może to być przydatne, jeśli chcesz sprawdzić poprawność `(/mode:ValidateArtifacts)`wielu modeli.|
|`/outcsdl:`\<file>|Określa nazwę pliku. csdl, który zostanie utworzony.|
|`/outmsl:`\<file>|Określa nazwę pliku. MSL, który zostanie utworzony.|
|`/outssdl:`\<file>|Określa nazwę pliku SSDL, który zostanie utworzony.|
|`/outobjectlayer:`\<file>|Określa nazwę pliku kodu źródłowego, który zawiera obiekty wygenerowane z pliku CSDL.|
|`/outviews:`\<file>|Określa nazwę pliku kodu źródłowego zawierającego widoki, które zostały wygenerowane.|
|`/language:`[VB&#124;CSharp]|Określa język generowanych plików kodu źródłowego. Język jest wartością domyślną C#.|
|`/namespace:`\<ciąg >|Określa przestrzeń nazw modelu, która ma być używana. Przestrzeń nazw jest ustawiana w pliku CSDL podczas uruchamiania `/mode:FullGeneration` lub. `/mode:FromSSDLGeneration` Przestrzeń nazw nie jest używana podczas uruchamiania `/mode:EntityClassGeneration`.|
|`/entitycontainer:`\<ciąg >|Określa nazwę, która ma zostać zastosowana do `<EntityContainer>` elementu w wygenerowanym modelu i plików mapowania.|
|`/pl[uralize]`|Stosuje reguły języka angielskiego dla liczb pojedynczej i pluralizmu do `Entity`, `EntitySet`i `NavigationProperty` nazwy w modelu koncepcyjnym. Ta opcja spowoduje wykonanie następujących akcji:<br /><br /> — Wprowadź wszystkie `EntityType` nazwy pojedyncze.<br />— Wprowadź wszystkie `EntitySet` nazwy w liczbie mnogiej.<br />-Dla każdej `NavigationProperty` , która zwraca co najwyżej jedną jednostkę, wprowadź nazwę pojedynczą.<br />-Dla każdego `NavigationProperty` , które zwraca więcej niż jedną jednostkę, wprowadź nazwę w liczbie mnogiej.|
|`/SuppressForeignKeyProperties or /nofk`|Zapobiega ujawnianiu kolumn klucza obcego jako właściwości skalarnych w typach jednostek w modelu koncepcyjnym.|
|`/help` lub `?`|Wyświetla składnię polecenia i opcje narzędzia.|
|`/nologo`|Pomija wyświetlanie komunikatu o prawach autorskich.|
|`/targetversion:`\<ciąg >|Wersja .NET Framework, która będzie używana do kompilowania wygenerowanego kodu. Obsługiwane wersje to 4 i 4,5. Wartość domyślna to 4.|

## <a name="in-this-section"></a>W tej sekcji

[Instrukcje: Używanie programu EdmGen. exe do generowania modelu i plików mapowania](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)

[Instrukcje: Generowanie kodu warstwy obiektu za pomocą EdmGen. exe](how-to-use-edmgen-exe-to-generate-object-layer-code.md)

[Instrukcje: Sprawdzanie poprawności modelu i plików mapowania przy użyciu programu EdmGen. exe](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)

## <a name="see-also"></a>Zobacz także

- [Narzędzia Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Model danych jednostki](../entity-data-model.md)
- [Specyfikacje CSDL, SSDL i MSL](./language-reference/csdl-ssdl-and-msl-specifications.md)
