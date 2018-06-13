---
title: Generator EDM (EdmGen.exe)
ms.date: 03/30/2017
ms.assetid: fe8297a1-1fc3-48ce-8eeb-f70f63f857aa
ms.openlocfilehash: 90d67af0d2ba3ff04ee5c78b7d0a3f061a69bc1d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766273"
---
# <a name="edm-generator-edmgenexe"></a>Generator EDM (EdmGen.exe)
EdmGen.exe to narzędzie wiersza polecenia służące do pracy z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] modelu i mapowania plików. Narzędzie EdmGen.exe wykonaj następujące czynności:  
  
-   Połączenie ze źródłem danych przy użyciu dostawcy danych .NET Framework specyficzne dla źródła danych oraz do generowania modelu koncepcyjnego (CSDL), modelu magazynu (ssdl) i pliki mapowania (MSL), które są używane przez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Aby uzyskać więcej informacji, zobacz [porady: EdmGen.exe używany do generowania modelu i mapowania plików](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
-   Sprawdź poprawność istniejącego modelu. Aby uzyskać więcej informacji, zobacz [porady: EdmGen.exe używany do sprawdzania poprawności modelu i mapowania plików](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md).  
  
-   Generowanie języka C# lub Visual Basic plik kodu, który zawiera klasy obiektów generowane na podstawie pliku modelu koncepcyjnego (CSDL). Aby uzyskać więcej informacji, zobacz [porady: EdmGen.exe używany do generowania kodu warstwy obiektu](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md).  
  
-   Generuj plik kodu C# lub Visual Basic, który zawiera wstępnie wygenerowanych widoków dla istniejącego modelu. Aby uzyskać więcej informacji [porady: Pre-Generate widoków, aby poprawić wydajność kwerend](http://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579).  
  
 Instalacja narzędzia EdmGen.exe w [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] katalogu. W wielu przypadkach to znajduje się w C:\windows\Microsoft.NET\Framework\v4.0. 64-bitowe systemy to znajduje się w C:\windows\Microsoft.NET\Framework64\v4.0. Można również przejść narzędzie EdmGen.exe z wiersza polecenia programu Visual Studio (kliknij **Start**, wskaż **wszystkie programy**, wskaż polecenie **programu Microsoft Visual Studio 2010**, wskaż pozycję **Programu visual Studio Tools**, a następnie kliknij przycisk **programu Visual Studio 2010 polecenie wiersza**).  
  
## <a name="syntax"></a>Składnia  
  
```  
EdmGen /mode:choice [options]  
```  
  
## <a name="mode"></a>Tryb  
 Podczas korzystania z narzędzia EdmGen.exe, należy określić jedną z następujących trybów.  
  
|Tryb|Opis|  
|----------|-----------------|  
|`/mode:ValidateArtifacts`|Weryfikuje pliki CSDL, ssdl i .msl i wyświetla jakiekolwiek błędy i ostrzeżenia.<br /><br /> Ta opcja wymaga co najmniej jeden z `/inssdl` lub `/incsdl` argumentów. Jeśli `/inmsl` jest określony, `/inssdl` i `/incsdl` argumenty są również wymagane.|  
|`/mode:FullGeneration`|Używa bazy danych informacji o połączeniu określonych w `/connectionstring` opcji oraz generuje CSDL, ssdl, MSL, obiekt warstwy i przeglądania plików.<br /><br /> Ta opcja wymaga `/connectionstring` argument, a następnie `/project` argument lub `/outssdl`, `/outcsdl`, `/outmsdl`, `/outobjectlayer`, `/outviews`, `/namespace`, i `/entitycontainer` argumentów.|  
|`/mode:FromSSDLGeneration`|Generuje pliki .csdl i .msl, widoków i kodu źródłowego z pliku ssdl określony.<br /><br /> Ta opcja wymaga `/inssdl` argument, a następnie `/project` argument lub `/outcsdl`, `/outmsl`, `/outobjectlayer`, `/outviews`, `/namespace,` i `/entitycontainer` argumentów.|  
|`/mode:EntityClassGeneration`|Tworzy plik kodu źródłowego, który zawiera klasy generowane na podstawie pliku CSDL.<br /><br /> Ta opcja wymaga `/incsdl` argument, a następnie `/project` argument lub `/outobjectlayer` argumentu. `/language` Argument jest opcjonalny.|  
|`/mode:ViewGeneration`|Tworzy plik kodu źródłowego, który zawiera widoki generowane na podstawie CSDL, ssdl i pliki MSL.<br /><br /> Ta opcja wymaga `/inssdl`, `/incsdl`, `/inmsl,` i `/project` lub `/outviews` argumentów. `/language` Argument jest opcjonalny.|  
  
## <a name="options"></a>Opcje  
  
|Opcja|Opis|  
|------------|-----------------|  
|`/p[roject]:`\<ciąg >|Określa nazwę projektu do użycia. Nazwa projektu jest używany jako domyślny dla przestrzeni nazw Ustawianie nazwy modelu i mapowania plików, nazwa pliku źródła obiektu i nazwę pliku źródłowego generowania widoku. Ustawiono nazwę kontenera jednostek \<projektu > kontekstu.|  
|`/prov[ider]:`\<ciąg >|Nazwa [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] dostawcy danych ma być używany do generowania pliku magazynu modelu (ssdl). Domyślny dostawca jest [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] dostawcy danych programu SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>).|  
|`/c[onnectionstring]:`\<Parametry połączenia >|Określa ciąg, który jest używany do nawiązania połączenia ze źródłem danych.|  
|`/incsdl:`\<file>|Określa plik .csdl lub katalog, w którym znajdują się pliki .csdl. Ten argument można określić wiele razy, dzięki czemu można określić kilka katalogów lub .csdl plików. Określanie wielu katalogów mogą być przydatne podczas generowania klasy (`/mode:EntityClassGeneration`) lub widoków (`/mode:ViewGeneration`) po modelu koncepcyjnego jest podzielone między kilka plików. Może to być również przydatne, gdy chcesz zweryfikować wielu modeli (`/mode:ValidateArtifacts`).|  
|`/refcsdl:`\<file>|Określa dodatkowe .csdl plik lub pliki, używany do rozpoznawania odwołań w pliku CSDL źródła. (Plik .csdl źródła jest plik określony przez `/incsdl` opcja). `/refcsdl` Plik zawiera typy, które jest zależny plik .csdl źródła. Ten argument można podawać wiele razy.|  
|`/inmsl:`\<file>|Określa .msl pliku lub katalogu, w którym znajdują się pliki MSL. Ten argument może być określone wiele razy, dzięki czemu można określić kilka katalogi i pliki MSL. Określanie wielu katalogów mogą być przydatne podczas generowania widoków (`/mode:ViewGeneration`) po modelu koncepcyjnego jest podzielone między kilka plików. Może to być również przydatne, gdy chcesz zweryfikować wielu modeli (`/mode:ValidateArtifacts`).|  
|`/inssdl:`\<file>|Określa plik ssdl lub katalog, w którym znajduje się plik ssdl. Ten argument można określić wiele razy, aby określić wiele katalogów lub plików ssdl. Może to być przydatne, gdy chcesz zweryfikować wielu modeli `(/mode:ValidateArtifacts)`.|  
|`/outcsdl:`\<file>|Określa nazwę pliku CSDL, który zostanie utworzony.|  
|`/outmsl:`\<file>|Określa nazwę pliku MSL, który zostanie utworzony.|  
|`/outssdl:`\<file>|Określa nazwę pliku ssdl, który zostanie utworzony.|  
|`/outobjectlayer:`\<file>|Określa nazwę pliku kodu źródłowego, który zawiera obiekty generowane na podstawie pliku CSDL.|  
|`/outviews:`\<file>|Określa nazwę pliku kodu źródłowego, który zawiera widoki, które zostały wygenerowane.|  
|`/language:`[VB&#124;CSharp]|Określa język dla plików źródłowych wygenerowanego kodu. Wartością domyślną języka C#.|  
|`/namespace:`\<ciąg >|Określa przestrzeń nazw modelu do użycia. Przestrzeń nazw jest ustawiona w pliku CSDL, gdy uruchomione `/mode:FullGeneration` lub `/mode:FromSSDLGeneration`. Przestrzeń nazw nie jest używany podczas uruchamiania `/mode:EntityClassGeneration`.|  
|`/entitycontainer:`\<ciąg >|Określa nazwę, aby zastosować do `<EntityContainer>` elementu w modelu wygenerowanym i mapowania plików.|  
|`/pl[uralize]`|Zastosowanie zasady język angielski singulars i liczba mnoga do `Entity`, `EntitySet`, i `NavigationProperty` nazwy w modelu koncepcyjnym. Ta opcja będzie wykonywać następujące czynności:<br /><br /> -Sprawdź wszystkie `EntityType` pojedynczej nazwy.<br />-Sprawdź wszystkie `EntitySet` nazwy w liczbie mnogiej.<br />— Dla każdej `NavigationProperty` zwracającą co najwyżej jedną jednostkę, sprawdź nazwę pojedynczej.<br />— Dla każdej `NavigationProperty` zwracającą więcej niż jednej jednostki, sprawdź nazwę liczbie mnogiej.|  
|`/SupressForeignKeyProperties or /nofk`|Kolumny klucza obcego zapobiega przed przypadkowym jako właściwości skalarnych na typy jednostek w modelu koncepcyjnym.|  
|`/help` lub `?`|Wyświetla składnię polecenia i opcje narzędzia.|  
|`/nologo`|Pomija wyświetlanie komunikaty o prawach autorskich.|  
|`/targetversion:` \<ciąg >|Wersja .NET Framework, która będzie służyć do kompilowania wygenerowanego kodu. Obsługiwane wersje to 4 i 4.5. Wartość domyślna to 4.|  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Generowanie modelu i mapowania plików za pomocą EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)  
  
 [Instrukcje: Używanie EdmGen.exe, aby wygenerować kod warstwy obiektu](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)  
  
 [Instrukcje: Walidacja modelu i mapowania plików za pomocą EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET Entity Data Model Tools](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [Model danych jednostki](../../../../../docs/framework/data/adonet/entity-data-model.md)  
 [Specyfikacje CSDL, SSDL i MSL](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
