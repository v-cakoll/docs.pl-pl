---
title: Izolowany magazyn
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- data storage using isolated storage
- stores
- storing data using isolated storage
- isolated storage
- location of isolated storage in file system
- standardizing storage systems
- storing data using isolated storage, when not to use
- code, isolated storage
- isolated storage, options
- data storage using isolated storage, when not to use
- storing data using isolated storage, options
- isolated storage, when not to use
- data storage using isolated storage, options
- isolation
ms.assetid: aff939d7-9e49-46f2-a8cd-938d3020e94e
ms.openlocfilehash: ed784bafda2aed829f2e97d7e7e8b2716c48c7ba
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706585"
---
# <a name="isolated-storage"></a>Izolowany magazyn
<a name="top"></a>W przypadku aplikacji klasycznych magazyn izolowany jest mechanizmem magazynu danych, który zapewnia izolację i bezpieczeństwo przez definiowanie ustandaryzowanych metod kojarzenia kodu z zapisanymi danymi. Standaryzacja oferuje także inne korzyści. Administratorzy mogą używać narzędzi przeznaczonych do wykonywania operacji na wydzielonej pamięci masowej w celu konfigurowania ilości miejsca przeznaczonego na pliki, ustawiania zasad zabezpieczeń i usuwania nieużywanych danych. Dzięki wydzielonej pamięci masowej kod nie wymaga unikatowych ścieżek określających bezpieczne lokalizacje w systemie plików, a dane są chronione przed innymi aplikacjami, które mają dostęp tylko do wydzielonej pamięci masowej. Ustalona informacja, która wskazuje, gdzie jest zlokalizowany obszar pamięci aplikacji nie jest potrzebna.

> [!IMPORTANT]
> Izolowany magazyn nie jest dostępny dla aplikacji ze sklepu Windows 8. x. Zamiast tego należy użyć klas danych aplikacji znajdujących się w `Windows.Storage` przestrzenie nazw, które znajdują się w interfejsie API środowisko wykonawcze systemu Windows do przechowywania lokalnych danych i plików. Aby uzyskać więcej informacji, zobacz [dane aplikacji](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) w centrum deweloperów systemu Windows.

Ten temat zawiera następujące sekcje:

- [Przedziały i magazyny danych](#data_compartments_and_stores)

- [Przydziały dla izolowanego magazynu](#quotas)

- [Bezpieczny dostęp](#secure_access)

- [Dozwolone użycie i zagrożenia bezpieczeństwa](#allowed_usage)

- [Lokalizacje izolowanych magazynów](#isolated_storage_locations)

- [Tworzenie, Wyliczanie i usuwanie izolowanego magazynu](#isolated_storage_tasks)

- [Scenariusze dotyczące magazynu izolowanego](#scenarios_for_isolated_storage)

- [Tematy pokrewne](#related_topics)

- [Tematy pomocy](#reference)

<a name="data_compartments_and_stores"></a>

## <a name="data-compartments-and-stores"></a>Przedziały i magazyny danych

Kiedy aplikacja przechowuje dane w pliku, należy ostrożnie wybierać nazwę pliku i lokalizację w pamięci masowej, aby zminimalizować prawdopodobieństwo, że lokalizacja w pamięci masowej będzie znana innej aplikacji, przez co będzie narażona na uszkodzenia. Bez standardowego systemu do zarządzania wymienionymi problemami projektowanie technik ad hoc, które minimalizują konflikty pamięci podręcznej, może być złożone, a wyniki mogą być zawodne.

Dzięki wydzielonej pamięci masowej dane są zawsze izolowane według użytkownika i zestawu. Poświadczenia, takie jak pochodzenie lub silna nazwa zestawu, określają tożsamość zestawu. Użycie podobnych poświadczeń umożliwia też izolowanie danych według domeny aplikacji.

Gdy jest używana wydzielona pamięć masowa, aplikacja zapisuje dane w unikatowym przedziale danych skojarzonym z pewnymi aspektami tożsamości kodu, takimi jak wydawca lub podpis. Przedział danych jest abstrakcyjną, a nie konkretną lokalizacją w pamięci masowej; składa się z co najmniej jednego pliku wydzielonej pamięci masowej, nazywanego magazynem, który zawiera rzeczywistą lokalizację katalogu, w którym są przechowywane dane. Na przykład aplikacja może mieć skojarzony przedział danych, a katalog w systemie plików będzie implementować magazyn, w którym w rzeczywistości są przechowywane dane dla tej aplikacji. Dane zapisane w magazynie mogą być dowolnego rodzaju, od informacji o preferencjach użytkownika po informacje o stanie aplikacji. Lokalizacja przedziału danych jest niewidoczna dla dewelopera. Magazyny zazwyczaj znajdują się na komputerze klienckim, ale aplikacje serwerowe mogą używać izolowanych magazynów do przechowywania informacji, personifikując użytkownika, w imieniu którego działają. Wydzielona pamięć masowa może także przechowywać informacje na serwerze, używając profilu mobilnego użytkownika, dzięki czemu takie informacje mogą podróżować razem z użytkownikiem mobilnym.

<a name="quotas"></a>

## <a name="quotas-for-isolated-storage"></a>Limity izolowanych magazynów

Przydział to limit ilości wydzielonej pamięci masowej, której można używać. Przydział zawiera bajty w przestrzeni plików, a także zapas skojarzony z katalogiem i innymi informacjami w magazynie. Magazyn izolowany korzysta z przydziałów uprawnień, które są limitami magazynu ustawionymi przy użyciu obiektów <xref:System.Security.Permissions.IsolatedStoragePermission>. Jeśli spróbujesz zapisać dane, które przekraczają limit przydziału, zostanie zgłoszony wyjątek <xref:System.IO.IsolatedStorage.IsolatedStorageException>.  Zasady zabezpieczeń, które można modyfikować za pomocą narzędzia .NET Framework Configuration Tool (Mscorcfg.msc), określają uprawnienia udzielane kodowi. Kod, który został udzielony <xref:System.Security.Permissions.IsolatedStoragePermission>, jest ograniczony do używania nie więcej magazynu niż zezwala na Właściwość <xref:System.Security.Permissions.IsolatedStoragePermission.UserQuota%2A>. Jednak kod może obejść przedziały uprawnień, prezentując różne tożsamości użytkownika, więc przydziały uprawnień pełnią rolę wytycznych dotyczących zachowania kodu, a nie stałych limitów zachowania kodu.

Przydziały nie są wymuszane w magazynach mobilnych. Z tego powodu kod musi mieć nieco wyższy poziom uprawnień, aby mógł ich używać. Wartości wyliczeniowe <xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByRoamingUser> i <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByRoamingUser> określają uprawnienia do używania wydzielonej pamięci masowej dla użytkownika mobilnego.

<a name="secure_access"></a>

## <a name="secure-access"></a>Bezpieczny dostęp

Wydzielona pamięć masowa umożliwia częściowo zaufanym aplikacjom przechowywanie danych w sposób kontrolowany przez zasady zabezpieczeń komputera. Jest to szczególnie przydatne w przypadku pobranych składników, które użytkownik może chcieć uruchomić z zachowaniem ostrożności. Zasady zabezpieczeń rzadko udzielają uprawnień kodu tego rodzaju podczas uzyskiwania dostępu do systemu plików przy użyciu standardowych mechanizmów We/Wy. Jednak kod uruchomiony na komputerze lokalnym, w sieci lokalnej lub w Internecie ma domyślnie udzielone prawo do używania wydzielonej pamięci masowej.

Na podstawie odpowiedniego poziomu zaufania administratorzy mogą określić, ile wydzielonej pamięci masowej jest dostępnej dla aplikacji lub użytkownika. Ponadto administratorzy mogą całkowicie usuwać utrwalone dane użytkownika. Aby utworzyć magazyn izolowany lub uzyskać do niego dostęp, należy przyznać mu odpowiednie uprawnienia <xref:System.Security.Permissions.IsolatedStorageFilePermission>.

Aby uzyskać dostęp do wydzielonej pamięci masowej, kod musi mieć wszystkie niezbędne natywne prawa platformy systemu operacyjnego. Wymagana jest zgodność z listami kontroli dostępu (ACL) określającymi, którzy użytkownicy mają prawa do używania systemu plików. Aplikacje programu .NET Framework mają już prawa systemu operacyjnego dotyczące dostępu do wydzielonej pamięci masowej, chyba że wykonują personifikację (specyficzna dla platformy). W tym przypadku aplikacja jest odpowiedzialna za sprawdzanie, czy tożsamość personifikowanego użytkownika ma prawidłowe prawa systemu operacyjnego do uzyskiwania dostępu do wydzielonej pamięci masowej. Ten dostęp oferuje uruchomionemu lub pobranemu z sieci web kodowi wygodny sposób odczytu lub zapisu w obszarze pamięci masowej związanym z konkretnym użytkownikiem.

Aby kontrolować dostęp do magazynu izolowanego, środowisko uruchomieniowe języka wspólnego używa <xref:System.Security.Permissions.IsolatedStorageFilePermission> obiektów. Każdy obiekt ma właściwości, które określają następujące wartości:

- Dozwolone użycie, które wskazuje typ dozwolonego dostępu. Wartości są elementami członkowskimi wyliczenia <xref:System.Security.Permissions.IsolatedStorageContainment>. Aby uzyskać więcej informacji na temat tych wartości, zobacz tabelę w następnej sekcji.

- Przydział pamięci, tak jak omówiono w poprzedniej sekcji.

Środowisko uruchomieniowe wymaga uprawnień <xref:System.Security.Permissions.IsolatedStorageFilePermission>, gdy kod próbuje otworzyć magazyn. Decyduje o tym, czy udzielić tego uprawnienia, w zależności od tego, jaki kod jest zaufany. Jeśli przyznano uprawnienia, dozwolone wartości przydziału użycia i magazynu są określane przez zasady zabezpieczeń i przez żądanie kodu dla <xref:System.Security.Permissions.IsolatedStorageFilePermission>. Zasady zabezpieczeń są ustawiane przy użyciu narzędzia .NET Framework Configuration Tool (Mscorcfg.msc). Wszystkie obiekty wywołujące w stosie wywołań są sprawdzane w celu zagwarantowania, że każdy obiekt wywołujący ma co najmniej jedno odpowiednie dozwolone użycie. Środowisko uruchomieniowe sprawdza też przydział określony przez kod, który otworzył lub utworzył magazyn, w którym mają być zapisywane pliki. Jeśli warunki są spełnione, jest udzielane uprawnienie. Przydział jest sprawdzany ponownie za każdym razem, gdy plik jest zapisywany w magazynie.

Kod aplikacji nie jest wymagany do zażądania uprawnień, ponieważ środowisko uruchomieniowe języka wspólnego przyznaje wszelkie <xref:System.Security.Permissions.IsolatedStorageFilePermission> odpowiednie w oparciu o zasady zabezpieczeń. Istnieją jednak dobre powody, aby zażądać określonych uprawnień wymaganych przez aplikację, w tym <xref:System.Security.Permissions.IsolatedStorageFilePermission>.

<a name="allowed_usage"></a>

## <a name="allowed-usage-and-security-risks"></a>Dopuszczalne użycie i zagrożenia zabezpieczeń

Dozwolone użycie określone przez <xref:System.Security.Permissions.IsolatedStorageFilePermission> określa stopień, w jakim kod będzie mógł utworzyć i używać izolowanego magazynu. W poniższej tabeli pokazano, jak dozwolone użycie określone w uprawnieniu odpowiada typom izolacji, i podsumowano zagrożenia bezpieczeństwa skojarzone z każdym dozwolonym użyciem.

|Dozwolone użycie|Typy izolacji|Wpływ na zabezpieczenia|
|-------------------|---------------------|---------------------|
|<xref:System.Security.Permissions.IsolatedStorageContainment.None>|Użycie wydzielonej pamięci masowej nie jest dozwolone.|Brak wpływu na zabezpieczenia.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser>|Izolacja według użytkownika, domeny i zestawu. Każdy zestaw ma oddzielny podmagazyn w domenie. Magazyny używające tego uprawnienia są także niejawnie izolowane przez komputer.|Ten poziom uprawnień zostawia zasoby otwarte do nieautoryzowanego użycia, mimo że wymuszone przydziały utrudniają takie użycie. Takie działanie jest znanej pod nazwą „ataku typu odmowa usługi”.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByRoamingUser>|Analogicznie jak `DomainIsolationByUser`, ale magazyn jest zapisywany w lokalizacji, która będzie przenoszona w przypadku włączenia profilów użytkowników mobilnych, a limity przydziału nie są wymuszane.|Przydziały muszą być wyłączone, więc zasoby pamięci masowej są bardziej podatne na atak typu „odmowa usługi”.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByUser>|Izolacja według użytkownika i zestawu. Magazyny używające tego uprawnienia są także niejawnie izolowane przez komputer.|Na tym poziomie są wymuszane przydziały, aby zapobiegać atakom typu „odmowa usługi”. Taki sam zestaw w innej domenie może mieć dostęp do magazynu, przez co możliwe jest przeciekanie informacji między aplikacjami.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByRoamingUser>|Analogicznie jak `AssemblyIsolationByUser`, ale magazyn jest zapisywany w lokalizacji, która będzie przenoszona w przypadku włączenia profilów użytkowników mobilnych, a limity przydziału nie są wymuszane.|Analogicznie jak w `AssemblyIsolationByUser`, ale bez przydziałów, ryzyko ataku typu "odmowa usługi" zwiększa się.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>|Izolacja według użytkownika. Zazwyczaj tylko narzędzia administracyjne lub narzędzia do debugowania używają tego poziomu uprawnień.|Dostęp z użyciem tego uprawnienia umożliwia kodowi wyświetlanie i usuwanie dowolnych plików lub katalogów użytkownika przechowywanych w wydzielonej pamięci masowej (niezależnie do izolacji zestawu). Zagrożenia to m.in. wycieki informacji i utrata danych.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.UnrestrictedIsolatedStorage>|Izolacja według wszystkich użytkowników, domen i zestawów. Zazwyczaj tylko narzędzia administracyjne lub narzędzia do debugowania używają tego poziomu uprawnień.|To uprawnienie tworzy potencjalną możliwość naruszenia zabezpieczeń wszystkich izolowanych magazynów wszystkich użytkowników.|

<a name="isolated_storage_locations"></a>

## <a name="isolated-storage-locations"></a>Lokalizacje izolowanych magazynów

Czasami jest ono pomocne podczas weryfikowania zmiany w wydzielonej pamięci masowej za pomocą systemu plików systemu operacyjnego. Czasami mogą być też potrzebne informacje o lokalizacji plików wydzielonej pamięci masowej. Ta lokalizacja zmienia się w zależności od systemu operacyjnego. W poniższej tabeli pokazano główne lokalizacje w najbardziej popularnych systemach operacyjnych, w których jest tworzona wydzielona pamięć masowa. Znajdź katalogi Microsoft\IsolatedStorage w tej lokalizacji głównej. Musisz zmienić ustawienia folderów, aby wyświetlać ukryte pliki i foldery, co umożliwi zobaczenie wydzielonej pamięci masowej w systemie plików.

|System operacyjny|Lokalizacja w systemie plików|
|----------------------|-----------------------------|
|Windows 2000, Windows XP, Windows Server 2003 (uaktualnienie z systemu Windows NT 4.0)|Magazyny z obsługą roamingu =<br /><br /> \<GŁÓWNY_KATALOG_SYSTEMOWY > \Profiles\\< użytkownik\>\Dane danych<br /><br /> Magazyny bez obsługi roamingu =<br /><br /> \<GŁÓWNY_KATALOG_SYSTEMOWY > \Profiles\\< użytkownik\>\Ustawienia Lokalne\dane dane|
|Windows 2000 — czysta instalacja (oraz uaktualnienia z systemu Windows 98 i Windows NT 3.51)|Magazyny z obsługą roamingu =<br /><br /> \<DYSKSYSTEMOWY > \Dokumenty i ustawienia\\< użytkownik\>\Dane danych<br /><br /> Magazyny bez obsługi roamingu =<br /><br /> \<DYSKSYSTEMOWY > \Dokumenty i ustawienia\\< użytkownik\>\Ustawienia Lokalne\dane dane|
|Windows XP, Windows Server 2003 — czysta instalacja (i uaktualnienia z systemu Windows 2000 i Windows 98)|Magazyny z obsługą roamingu =<br /><br /> \<DYSKSYSTEMOWY > \Dokumenty i ustawienia\\< użytkownik\>\Dane danych<br /><br /> Magazyny bez obsługi roamingu =<br /><br /> \<DYSKSYSTEMOWY > \Dokumenty i ustawienia\\< użytkownik\>\Ustawienia Lokalne\dane dane|
|Windows 8, Windows 7, Windows Server 2008, Windows Vista|Magazyny z obsługą roamingu =<br /><br /> \<dysk_systemowy > \Users\\< użytkownika\>\AppData\Roaming<br /><br /> Magazyny bez obsługi roamingu =<br /><br /> \<dysk_systemowy > \Users\\< użytkownika\>\AppData\Local|

<a name="isolated_storage_tasks"></a>

## <a name="creating-enumerating-and-deleting-isolated-storage"></a>Tworzenia, wyliczania i usuwania izolowanych magazynów

.NET Framework zawiera trzy klasy w przestrzeni nazw <xref:System.IO.IsolatedStorage>, które ułatwiają wykonywanie zadań obejmujących izolowany magazyn:

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>, pochodzi od <xref:System.IO.IsolatedStorage.IsolatedStorage?displayProperty=nameWithType> i zapewnia podstawowe zarządzanie przechowywanymi plikami zestawu i aplikacji. Wystąpienie klasy <xref:System.IO.IsolatedStorage.IsolatedStorageFile> reprezentuje pojedynczy magazyn znajdujący się w systemie plików.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> pochodzi od <xref:System.IO.FileStream?displayProperty=nameWithType> i zapewnia dostęp do plików w sklepie.

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope> to wyliczenie, które umożliwia tworzenie i wybieranie magazynu z odpowiednim typem izolacji.

Klasy wydzielonej pamięci masowej umożliwiają tworzenie, wyliczanie oraz usuwanie wydzielonej pamięci masowej. Metody wykonywania tych zadań są dostępne za pomocą obiektu <xref:System.IO.IsolatedStorage.IsolatedStorageFile>. Niektóre operacje wymagają posiadania uprawnienia <xref:System.Security.Permissions.IsolatedStorageFilePermission>, które reprezentuje prawo do administrowania izolowanym magazynem. może być również konieczne posiadanie praw systemu operacyjnego w celu uzyskania dostępu do pliku lub katalogu.

Aby uzyskać szereg przykładów demonstrujących typowe zadania magazynu izolowanego, zapoznaj się z tematami podanymi w [tematach pokrewnych](#related_topics).

<a name="scenarios_for_isolated_storage"></a>

## <a name="scenarios-for-isolated-storage"></a>Scenariusze izolowanych magazynów

Wydzielona pamięć masowa jest przydatna w wielu sytuacjach, włączając w to następujące cztery scenariusze:

- Pobrane formanty. Formanty kodu zarządzanego pobrane z Internetu nie mogą wykonywać operacji zapisu na dysku twardym za pośrednictwem zwykłych klas We/Wy, ale mogą używać wydzielonej pamięci masowej w celu utrwalania stanów aplikacji i ustawień użytkowników.

- Magazyn składników współużytkowanych. Składniki współużytkowane przez różne aplikacje mogą używać wydzielonej pamięci masowej, aby umożliwiać kontrolowany dostęp do danych.

- Magazyn na serwerze. Aplikacje serwerowe mogą używać wydzielonej pamięci masowej, aby dostarczać indywidualne magazyny wielu użytkownikom wysyłającym żądania do aplikacji. Ponieważ wydzielona pamięć masowa zawsze jest segregowana według użytkowników, serwer musi dokonać personifikacji użytkownika zgłaszającego żądanie. W takim przypadku dane są izolowane na podstawie tożsamości podmiotu zabezpieczeń, która jest tą samą tożsamością, której aplikacja używa do rozróżniania między użytkownikami.

- Roaming. Aplikacje mogą również używać wydzielonej pamięci masowej z mobilnymi profilami użytkownika. Dzięki temu użytkownik może uzyskiwać mobilny dostęp do swoich izolowanych magazynów, używając profilu.

Wydzielonej pamięci masowej nie należy używać w następujących sytuacjach:

- Do przechowywania tajemnic o wysokiej wartości, takich jak niezaszyfrowane klucze lub hasła, ponieważ wydzielona pamięć masowa nie jest chroniona przed wysoce zaufanym kodem, kodem niezarządzanym oraz zaufanymi użytkownikami komputera.

- Do przechowywania kodu.

- Do przechowywania ustawień konfiguracji i wdrażania kontrolowanych przez administratorów. (Preferencje użytkownika nie są uważane za ustawienia konfiguracji, ponieważ administratorzy nie mają kontroli nad nimi).

Wiele aplikacji używa bazy danych do przechowywania i izolowania danych; w takim przypadku jeden lub większa liczba wierszy w bazie danych może reprezentować pamięć masową dla określonego użytkownika. Można użyć wydzielonej pamięci masowej zamiast bazy danych, gdy liczba użytkowników jest mała, gdy obciążenie związane z użyciem bazy danych jest znaczące lub gdy nie istnieje infrastruktura baz danych. Również gdy aplikacja wymaga pamięci masowej, która będzie bardziej elastyczna oraz złożona niż to, co oferuje wiersz w bazie danych, wydzielona pamięć masowa może być wartą rozważenia alternatywą.

<a name="related_topics"></a>

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Typy izolacji](../../../docs/standard/io/types-of-isolation.md)|Opis różnych typów izolacji.|
|[Instrukcje: uzyskiwanie magazynów dla wydzielonej pamięci masowej](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)|Stanowi przykład użycia klasy <xref:System.IO.IsolatedStorage.IsolatedStorageFile>, aby uzyskać magazyn izolowany przez użytkownika i zestaw.|
|[Instrukcje: wyliczanie magazynów dla wydzielonej pamięci masowej](../../../docs/standard/io/how-to-enumerate-stores-for-isolated-storage.md)|Pokazuje, w jaki sposób używać metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType>, aby obliczyć rozmiar całego izolowanego magazynu dla użytkownika.|
|[Instrukcje: usuwanie danych z wydzielonej pamięci masowej](../../../docs/standard/io/how-to-delete-stores-in-isolated-storage.md)|Pokazuje, jak używać metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A?displayProperty=nameWithType> na dwa różne sposoby usuwania izolowanych magazynów.|
|[Instrukcje: przewidywanie warunków braku miejsca w wydzielonej pamięci masowej](../../../docs/standard/io/how-to-anticipate-out-of-space-conditions-with-isolated-storage.md)|Opis sposobu mierzenia ilości pozostałego miejsca w izolowanym magazynie.|
|[Instrukcje: tworzenie plików i katalogów w wydzielonej pamięci masowej](../../../docs/standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|Przykłady tworzenia plików i katalogów w izolowanym magazynie.|
|[Instrukcje: znajdowanie istniejących plików i katalogów w wydzielonej pamięci masowej](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|Opis sposobu odczytywania struktury katalogów i plików w wydzielonej pamięci masowej.|
|[Instrukcje: odczyt i zapis w plikach w wydzielonej pamięci masowej](../../../docs/standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|Przykład zapisywania ciągu w pliku w wydzielonej pamięci masowej i odczytywania go z powrotem.|
|[Instrukcje: usuwanie plików i katalogów w wydzielonej pamięci masowej](../../../docs/standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|Opis sposobu usuwania plików i katalogów wydzielonej pamięci masowej.|
|[We/Wy plików i strumieni](../../../docs/standard/io/index.md)|Opis sposobu synchronicznego i asynchronicznego uzyskiwania dostępu do pliku i strumienia danych.|

<a name="reference"></a>

## <a name="reference"></a>Tematy pomocy

- <xref:System.IO.IsolatedStorage.IsolatedStorage?displayProperty=nameWithType>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream?displayProperty=nameWithType>

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope?displayProperty=nameWithType>
