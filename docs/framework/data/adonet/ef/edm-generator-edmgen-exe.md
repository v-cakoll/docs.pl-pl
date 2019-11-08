---
title: Generator EDM (EdmGen.exe)
ms.date: 03/30/2017
ms.assetid: fe8297a1-1fc3-48ce-8eeb-f70f63f857aa
ms.openlocfilehash: 858525a81e7779e7631ee8ac959110ba946cf652
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738531"
---
# <a name="edm-generator-edmgenexe"></a>Generator EDM (EdmGen.exe)

EdmGen. exe to narzędzie wiersza polecenia służące do pracy z modelem i plikami mapowania Entity Framework. Za pomocą narzędzia EdmGen. exe można wykonać następujące czynności:

- Nawiązywanie połączenia ze źródłem danych przy użyciu dostawcy danych .NET Framework określonego przez źródło danych i generowanie modelu koncepcyjnego (. csdl), modelu magazynu (. ssdl) i plików mapowania (. MSL), które są używane przez Entity Framework. Aby uzyskać więcej informacji, zobacz [How to: use EdmGen. exe w celu wygenerowania modelu i plików mapowania](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).

- Zweryfikuj istniejący model. Aby uzyskać więcej informacji, zobacz [How to: use EdmGen. exe do walidacji modelu i plików mapowania](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md).

- Generuj plik C# kodu lub Visual Basic, który zawiera klasy obiektów generowane na podstawie pliku modelu koncepcyjnego (CSDL). Aby uzyskać więcej informacji, zobacz [jak: używanie programu EdmGen. exe do generowania kodu warstwy obiektu](how-to-use-edmgen-exe-to-generate-object-layer-code.md).

- Generuj plik C# kodu lub Visual Basic zawierający wstępnie wygenerowane widoki dla istniejącego modelu. Aby uzyskać więcej informacji, [jak: wstępnie wygenerować widoki w celu zwiększenia wydajności zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).

Narzędzie EdmGen. exe jest instalowane w katalogu .NET Framework. W wielu przypadkach znajduje się to w C:\windows\Microsoft.NET\Framework\v4.0. W przypadku systemów 64-bitowych ten program znajduje się w C:\windows\Microsoft.NET\Framework64\v4.0. Możesz również uzyskać dostęp do narzędzia EdmGen. exe z wiersza polecenia programu Visual Studio (kliknij przycisk **Start**, wskaż **Wszystkie programy**, wskaż **Microsoft Visual Studio 2010**, wskaż **Visual Studio Tools**, a następnie kliknij przycisk **Visual Studio 2010 Wiersz polecenia**).

## <a name="syntax"></a>Składnia

```console
EdmGen /mode:choice [options]
```

## <a name="mode"></a>Tryb

W przypadku korzystania z narzędzia EdmGen. exe należy określić jeden z następujących trybów.

|Tryb|Opis|
|----------|-----------------|
|`/mode:ValidateArtifacts`|Sprawdza poprawność plików CSDL, SSDL i MSL oraz wyświetla błędy lub ostrzeżenia.<br /><br /> Ta opcja wymaga co najmniej jednego argumentu `/inssdl` lub `/incsdl`. Jeśli określono `/inmsl`, wymagane są również argumenty `/inssdl` i `/incsdl`.|
|`/mode:FullGeneration`|Używa informacji o połączeniu z bazą danych określonych w opcji `/connectionstring` i generuje pliki CSDL, SSDL, MSL, warstwy obiektów i wyświetlaj.<br /><br /> Ta opcja wymaga argumentu `/connectionstring` i argumentu `/project` lub `/outssdl`, `/outcsdl`, `/outmsdl`, `/outobjectlayer`, `/outviews`, `/namespace`i `/entitycontainer` argumentów.|
|`/mode:FromSSDLGeneration`|Generuje pliki CSDL i MSL, kod źródłowy i widoki z określonego pliku SSDL.<br /><br /> Ta opcja wymaga argumentu `/inssdl` i argumentu `/project` lub argumentów `/outcsdl`, `/outmsl`, `/outobjectlayer`, `/outviews`, `/namespace,` i `/entitycontainer`.|
|`/mode:EntityClassGeneration`|Tworzy plik kodu źródłowego, który zawiera klasy wygenerowane z pliku CSDL.<br /><br /> Ta opcja wymaga argumentu `/incsdl` i argumentu `/project` lub argumentu `/outobjectlayer`. Argument `/language` jest opcjonalny.|
|`/mode:ViewGeneration`|Tworzy plik kodu źródłowego, który zawiera widoki wygenerowane na podstawie plików. csdl,. ssdl i. MSL.<br /><br /> Ta opcja wymaga `/inssdl`, `/incsdl`, `/inmsl,` i `/project` lub `/outviews` argumenty. Argument `/language` jest opcjonalny.|

## <a name="options"></a>Opcje

|Opcja|Opis|
|------------|-----------------|
|ciąg \<`/p[roject]:`|Określa nazwę projektu do użycia. Nazwa projektu jest używana jako wartość domyślna dla ustawienia przestrzeń nazw, nazwa modelu i pliki mapowania, nazwa pliku źródłowego obiektu i nazwa pliku źródłowego generacji widoku. Nazwa kontenera jednostek jest ustawiona na \<kontekstu > projektu.|
|ciąg \<`/prov[ider]:`|Nazwa dostawcy danych .NET Framework, który ma zostać użyty do wygenerowania pliku modelu magazynu (SSDL). Domyślny dostawca to .NET Framework Dostawca danych dla SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>).|
|`/c[onnectionstring]:`\<parametry połączenia >|Określa ciąg, który jest używany do nawiązywania połączenia ze źródłem danych.|
|`/incsdl:`\<pliku >|Określa plik CSDL lub katalog, w którym znajdują się pliki. csdl. Ten argument można określić wiele razy, aby można było określić kilka katalogów lub plików CSDL. Określenie wielu katalogów może być przydatne w przypadku generowania klas (`/mode:EntityClassGeneration`) lub widoków (`/mode:ViewGeneration`), gdy model koncepcyjny jest podzielony między kilka plików. Może to być przydatne, jeśli chcesz sprawdzić poprawność wielu modeli (`/mode:ValidateArtifacts`).|
|`/refcsdl:`\<pliku >|Określa dodatkowy plik. csdl lub pliki używane do rozwiązywania wszelkich odwołań w źródłowym pliku CSDL. (Plik. CSDL jest plikiem określonym przez opcję `/incsdl`). Plik `/refcsdl` zawiera typy, od których zależy plik source. csdl. Ten argument można określić wiele razy.|
|`/inmsl:`\<pliku >|Określa plik. MSL lub katalog, w którym znajdują się pliki. MSL. Ten argument można określić wiele razy, aby można było określić kilka katalogów lub plików MSL. Określenie wielu katalogów może być przydatne w przypadku generowania widoków (`/mode:ViewGeneration`), gdy model koncepcyjny jest podzielony na kilka plików. Może to być przydatne, jeśli chcesz sprawdzić poprawność wielu modeli (`/mode:ValidateArtifacts`).|
|`/inssdl:`\<pliku >|Określa plik SSDL lub katalog, w którym znajduje się plik. SSDL. Ten argument można określić wiele razy, aby można było określić kilka katalogów lub plików SSDL. Może to być przydatne, gdy chcesz sprawdzić poprawność wielu modeli `(/mode:ValidateArtifacts)`.|
|`/outcsdl:`\<pliku >|Określa nazwę pliku. csdl, który zostanie utworzony.|
|`/outmsl:`\<pliku >|Określa nazwę pliku. MSL, który zostanie utworzony.|
|`/outssdl:`\<pliku >|Określa nazwę pliku SSDL, który zostanie utworzony.|
|`/outobjectlayer:`\<pliku >|Określa nazwę pliku kodu źródłowego, który zawiera obiekty wygenerowane z pliku CSDL.|
|`/outviews:`\<pliku >|Określa nazwę pliku kodu źródłowego zawierającego widoki, które zostały wygenerowane.|
|`/language:`[VB&#124;CSharp]|Określa język generowanych plików kodu źródłowego. Język jest wartością domyślną C#.|
|ciąg\<`/namespace:`|Określa przestrzeń nazw modelu, która ma być używana. Przestrzeń nazw jest ustawiana w pliku CSDL podczas uruchamiania `/mode:FullGeneration` lub `/mode:FromSSDLGeneration`. Przestrzeń nazw nie jest używana podczas uruchamiania `/mode:EntityClassGeneration`.|
|ciąg\<`/entitycontainer:`|Określa nazwę, która ma zostać zastosowana do elementu `<EntityContainer>` w wygenerowanym modelu i plików mapowania.|
|`/pl[uralize]`|Stosuje reguły języka angielskiego dla liczb pojedynczej i plural do `Entity`, `EntitySet`i `NavigationProperty` nazw w modelu koncepcyjnym. Ta opcja spowoduje wykonanie następujących akcji:<br /><br /> -Wprowadź wszystkie `EntityType` nazwy pojedyncze.<br />-Wprowadź wszystkie `EntitySet` nazwy w liczbie mnogiej.<br />-Dla każdej `NavigationProperty`, która zwraca co najwyżej jedną jednostkę, wprowadź nazwę pojedynczą.<br />-Dla każdej `NavigationProperty`, która zwraca więcej niż jedną jednostkę, wprowadź nazwę w liczbie mnogiej.|
|`/SuppressForeignKeyProperties or /nofk`|Zapobiega ujawnianiu kolumn klucza obcego jako właściwości skalarnych w typach jednostek w modelu koncepcyjnym.|
|`/help` lub `?`|Wyświetla składnię polecenia i opcje narzędzia.|
|`/nologo`|Pomija wyświetlanie komunikatu o prawach autorskich.|
|ciąg \<`/targetversion:` >|Wersja .NET Framework, która będzie używana do kompilowania wygenerowanego kodu. Obsługiwane wersje to 4 i 4,5. Wartość domyślna to 4.|

## <a name="in-this-section"></a>W tej sekcji

[Instrukcje: Generowanie modelu i mapowania plików za pomocą EdmGen.exe](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)

[Instrukcje: Używanie EdmGen.exe, aby wygenerować kod warstwy obiektu](how-to-use-edmgen-exe-to-generate-object-layer-code.md)

[Instrukcje: Walidacja modelu i mapowania plików za pomocą EdmGen.exe](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)

## <a name="see-also"></a>Zobacz także

- [Narzędzia Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Model danych jednostki](../entity-data-model.md)
- [Specyfikacje CSDL, SSDL i MSL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
