---
title: Generator EDM (EdmGen.exe)
ms.date: 03/30/2017
ms.assetid: fe8297a1-1fc3-48ce-8eeb-f70f63f857aa
ms.openlocfilehash: 7f06b393cd7e7ccf3d3637d6fb46eb6d983d943a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607674"
---
# <a name="edm-generator-edmgenexe"></a>Generator EDM (EdmGen.exe)

EdmGen.exe to narzędzie wiersza polecenia służące do pracy z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] modelu i mapowania plików. Można użyć narzędzia EdmGen.exe, wykonaj następujące czynności:

- Łączenie ze źródłem danych przy użyciu dostawcy danych .NET Framework specyficzne dla źródła danych oraz do generowania modelu koncepcyjnego (.csdl), modelu magazynu (ssdl) i pliki mapowania (MSL albo identyfikatorem), które są używane przez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Aby uzyskać więcej informacji, zobacz [jak: Generowanie modelu i mapowania plików za pomocą EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).

- Weryfikowanie istniejącego modelu. Aby uzyskać więcej informacji, zobacz [jak: Walidacja modelu i mapowania plików za pomocą EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md).

- Wygeneruj, C# lub Visual Basic kodu zawierający klasy obiektów wygenerowany na podstawie pliku modelu koncepcyjnego (.csdl). Aby uzyskać więcej informacji, zobacz [jak: Aby wygenerować kod warstwy obiektu za pomocą EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md).

- Generuj plik kodu C# lub Visual Basic, który zawiera wstępnie wygenerowanych widoków dla istniejącego modelu. Aby uzyskać więcej informacji [jak: Wstępnie wygenerować widoków, aby poprawić wydajność zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).

Narzędzie EdmGen.exe jest instalowane w [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] katalogu. W wielu przypadkach znajduje się on w C:\windows\Microsoft.NET\Framework\v4.0. W 64-bitowych systemach znajduje się on w C:\windows\Microsoft.NET\Framework64\v4.0. Można również uzyskać dostęp do narzędzia EdmGen.exe, w wierszu polecenia programu Visual Studio (kliknij **Start**, wskaż **wszystkie programy**, wskaż polecenie **Microsoft Visual Studio 2010**, wskaż polecenie **Visual Studio Tools**, a następnie kliknij przycisk **Visual Studio 2010 Command Prompt**).

## <a name="syntax"></a>Składnia

```
EdmGen /mode:choice [options]
```

## <a name="mode"></a>Tryb

Podczas korzystania z narzędzia EdmGen.exe, należy określić jedną z następujących trybów.

|Tryb|Opis|
|----------|-----------------|
|`/mode:ValidateArtifacts`|Weryfikuje pliki .csdl, ssdl i MSL albo identyfikatorem i wyświetla wszelkie błędy lub ostrzeżenia.<br /><br /> Ta opcja wymaga co najmniej jeden z `/inssdl` lub `/incsdl` argumentów. Jeśli `/inmsl` jest określony, `/inssdl` i `/incsdl` wymagane są również argumentów.|
|`/mode:FullGeneration`|Informacje o połączeniu bazy danych, które zostały określone w używa `/connectionstring` opcji oraz generuje .csdl, ssdl i MSL albo identyfikatorem, obiekt warstwy i przeglądania plików.<br /><br /> Ta opcja wymaga `/connectionstring` argument, a następnie `/project` argument lub `/outssdl`, `/outcsdl`, `/outmsdl`, `/outobjectlayer`, `/outviews`, `/namespace`, i `/entitycontainer` argumentów.|
|`/mode:FromSSDLGeneration`|Generuje pliki .csdl i MSL albo identyfikatorem, kod źródłowy i widoki z pliku określonego ssdl.<br /><br /> Ta opcja wymaga `/inssdl` argument, a następnie `/project` argument lub `/outcsdl`, `/outmsl`, `/outobjectlayer`, `/outviews`, `/namespace,` i `/entitycontainer` argumentów.|
|`/mode:EntityClassGeneration`|Tworzy plik kodu źródłowego, który zawiera klas wygenerowanych na podstawie pliku .csdl.<br /><br /> Ta opcja wymaga `/incsdl` argument, a następnie `/project` argument lub `/outobjectlayer` argumentu. `/language` Argument jest opcjonalny.|
|`/mode:ViewGeneration`|Tworzy plik kodu źródłowego, który zawiera widoki generowane na podstawie .csdl, ssdl i MSL albo identyfikatorem plików.<br /><br /> Ta opcja wymaga `/inssdl`, `/incsdl`, `/inmsl,` i `/project` lub `/outviews` argumentów. `/language` Argument jest opcjonalny.|

## <a name="options"></a>Opcje

|Opcja|Opis|
|------------|-----------------|
|`/p[roject]:`\<ciąg >|Określa nazwę projektu, należy użyć. Nazwa projektu jest używany jako domyślny dla przestrzeni nazw, ustawiając nazwę modelu i mapowania plików, nazwa pliku źródłowego obiektu i nazwę pliku źródłowego generowania widoku. Nazwa kontenera jednostki jest równa \<Projekt > kontekstu.|
|`/prov[ider]:`\<ciąg >|Nazwa [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] dostawcy danych, które ma być używany do generowania pliku modelu (ssdl) magazynu. Domyślny dostawca jest [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>).|
|`/c[onnectionstring]:`\<Parametry połączenia >|Określa ciąg, który jest używany do połączenia ze źródłem danych.|
|`/incsdl:`\<file>|Określa plik .csdl lub katalogu, w którym znajdują się pliki .csdl. Tego argumentu można określić wiele razy, aby określić kilka katalogów lub .csdl plików. Określanie wielu katalogów mogą być przydatne podczas generowania klasy (`/mode:EntityClassGeneration`) lub widokach (`/mode:ViewGeneration`) podczas modelu koncepcyjnego jest podzielone między kilka plików. Może to być również przydatne, gdy chcesz zweryfikować wielu modeli (`/mode:ValidateArtifacts`).|
|`/refcsdl:`\<file>|Określa dodatkowe .csdl pliku lub plików używany do rozpoznawania odwołań w pliku źródłowym .csdl. (Jest .csdl pliku źródłowego, pliku, określonego przez `/incsdl` opcji). `/refcsdl` Plik zawiera typy, które .csdl pliku źródłowego jest zależny od. Ten argument może być określony wiele razy.|
|`/inmsl:`\<file>|Określa plik MSL albo identyfikatorem lub katalogu, w którym znajdują się pliki MSL albo identyfikatorem. Tego argumentu można określić wiele razy, dzięki czemu można określić kilka katalogów lub MSL albo identyfikatorem plików. Określanie wielu katalogów mogą być przydatne podczas generowania widoki (`/mode:ViewGeneration`) podczas modelu koncepcyjnego jest podzielone między kilka plików. Może to być również przydatne, gdy chcesz zweryfikować wielu modeli (`/mode:ValidateArtifacts`).|
|`/inssdl:`\<file>|Określa plik ssdl lub katalogu, w którym znajduje się plik ssdl. Tego argumentu można określić wiele razy, aby określić kilka katalogów lub ssdl plików. Może to być przydatne, gdy chcesz zweryfikować wielu modeli `(/mode:ValidateArtifacts)`.|
|`/outcsdl:`\<file>|Określa nazwę pliku .csdl, który zostanie utworzony.|
|`/outmsl:`\<file>|Określa nazwę pliku MSL albo identyfikatorem, który zostanie utworzony.|
|`/outssdl:`\<file>|Określa nazwę pliku ssdl, który zostanie utworzony.|
|`/outobjectlayer:`\<file>|Określa nazwę pliku kodu źródłowego, który zawiera obiekty wygenerowany na podstawie pliku .csdl.|
|`/outviews:`\<file>|Określa nazwę pliku kodu źródłowego, który zawiera widoki, które zostały wygenerowane.|
|`/language:`[VB&#124;CSharp]|Określa język dla plików kodu wygenerowanego źródła. Wartością domyślną języka C#.|
|`/namespace:`\<ciąg >|Określa przestrzeń nazw modelu do użycia. Przestrzeń nazw jest ustawiony w pliku .csdl podczas uruchamiania `/mode:FullGeneration` lub `/mode:FromSSDLGeneration`. Przestrzeń nazw nie jest używany podczas uruchamiania `/mode:EntityClassGeneration`.|
|`/entitycontainer:`\<ciąg >|Określa nazwę do zastosowania do `<EntityContainer>` elementu w wygenerowanym modelu i mapowania plików.|
|`/pl[uralize]`|Stosuje zasady język angielski singulars i liczba mnoga do `Entity`, `EntitySet`, i `NavigationProperty` nazw w modelu koncepcyjnym. Ta opcja będzie wykonywać następujące czynności:<br /><br /> — Sprawdź wszystkie `EntityType` nazw pojedynczej.<br />— Sprawdź wszystkie `EntitySet` nazwy w liczbie mnogiej.<br />— Dla każdego `NavigationProperty` zwracającego co najwyżej jedną jednostkę, wprowadzić nazwę pojedynczej.<br />— Dla każdego `NavigationProperty` zwracającego więcej niż jednej jednostce, utworzyć liczba mnoga nazwy.|
|`/SuppressForeignKeyProperties or /nofk`|Zapobiega kolumny klucza obcego są widoczne jako właściwości skalarne na typy jednostek w modelu koncepcyjnym.|
|`/help` lub `?`|Wyświetla składnię polecenia i opcje narzędzia.|
|`/nologo`|Pomija komunikat o prawach autorskich były wyświetlane.|
|`/targetversion:` \<ciąg >|Wersja .NET Framework, która będzie służyć do kompilowania wygenerowanego kodu. Obsługiwane wersje to 4 i 4.5. Wartość domyślna to 4.|

## <a name="in-this-section"></a>W tej sekcji

[Instrukcje: Generowanie modelu i mapowania plików za pomocą EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)

[Instrukcje: Aby wygenerować kod warstwy obiektu za pomocą EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)

[Instrukcje: Walidacja modelu i mapowania plików za pomocą EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)

## <a name="see-also"></a>Zobacz także

- [Narzędzia do modelu danych jednostki ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Model danych jednostki](../../../../../docs/framework/data/adonet/entity-data-model.md)
- [Specyfikacje CSDL, SSDL i MSL](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
