---
title: Izolowany magazyn
description: Poznaj izolowany magazyn, który jest mechanizmem magazynu danych, który zapewnia izolację & bezpieczeństwa przez definiowanie standardowych metod kojarzenia kodu z zapisanymi danymi.
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
ms.openlocfilehash: b9915faff2593cc51868c20e1a83a05ffca9f548
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325937"
---
# <a name="isolated-storage"></a>Izolowany magazyn
<a name="top"></a>W przypadku aplikacji klasycznych magazyn izolowany jest mechanizmem magazynu danych, który zapewnia izolację i bezpieczeństwo przez definiowanie ustandaryzowanych metod kojarzenia kodu z zapisanymi danymi. Standaryzacja oferuje także inne korzyści. Administratorzy mogą używać narzędzi przeznaczonych do wykonywania operacji na wydzielonej pamięci masowej w celu konfigurowania ilości miejsca przeznaczonego na pliki, ustawiania zasad zabezpieczeń i usuwania nieużywanych danych. Dzięki wydzielonej pamięci masowej kod nie wymaga unikatowych ścieżek określających bezpieczne lokalizacje w systemie plików, a dane są chronione przed innymi aplikacjami, które mają dostęp tylko do wydzielonej pamięci masowej. Ustalona informacja, która wskazuje, gdzie jest zlokalizowany obszar pamięci aplikacji nie jest potrzebna.

> [!IMPORTANT]
> Izolowany magazyn nie jest dostępny dla aplikacji ze sklepu Windows 8. x. Zamiast tego należy użyć klas danych aplikacji w `Windows.Storage` przestrzeniach nazw uwzględnionych w interfejsie API środowisko wykonawcze systemu Windows do przechowywania lokalnych danych i plików. Aby uzyskać więcej informacji, zobacz [dane aplikacji](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) w centrum deweloperów systemu Windows.

Ten temat zawiera następujące sekcje:

- [Przedziały i magazyny danych](#data_compartments_and_stores)

- [Limity izolowanych magazynów](#quotas)

- [Bezpieczny dostęp](#secure_access)

- [Dopuszczalne użycie i zagrożenia zabezpieczeń](#allowed_usage)

- [Lokalizacje izolowanych magazynów](#isolated_storage_locations)

- [Tworzenia, wyliczania i usuwania izolowanych magazynów](#isolated_storage_tasks)

- [Scenariusze izolowanych magazynów](#scenarios_for_isolated_storage)

- [Tematy pokrewne](#related_topics)

- [Tematy pomocy](#reference)

<a name="data_compartments_and_stores"></a>

## <a name="data-compartments-and-stores"></a>Przedziały i magazyny danych

Kiedy aplikacja przechowuje dane w pliku, należy ostrożnie wybierać nazwę pliku i lokalizację w pamięci masowej, aby zminimalizować prawdopodobieństwo, że lokalizacja w pamięci masowej będzie znana innej aplikacji, przez co będzie narażona na uszkodzenia. Bez standardowego systemu do zarządzania wymienionymi problemami projektowanie technik ad hoc, które minimalizują konflikty pamięci podręcznej, może być złożone, a wyniki mogą być zawodne.

Dzięki wydzielonej pamięci masowej dane są zawsze izolowane według użytkownika i zestawu. Poświadczenia, takie jak pochodzenie lub silna nazwa zestawu, określają tożsamość zestawu. Użycie podobnych poświadczeń umożliwia też izolowanie danych według domeny aplikacji.

Gdy jest używana wydzielona pamięć masowa, aplikacja zapisuje dane w unikatowym przedziale danych skojarzonym z pewnymi aspektami tożsamości kodu, takimi jak wydawca lub podpis. Przedział danych jest abstrakcyjną, a nie konkretną lokalizacją w pamięci masowej; składa się z co najmniej jednego pliku wydzielonej pamięci masowej, nazywanego magazynem, który zawiera rzeczywistą lokalizację katalogu, w którym są przechowywane dane. Na przykład aplikacja może mieć skojarzony przedział danych, a katalog w systemie plików będzie implementować magazyn, w którym w rzeczywistości są przechowywane dane dla tej aplikacji. Dane zapisane w magazynie mogą być dowolnego rodzaju, od informacji o preferencjach użytkownika po informacje o stanie aplikacji. Lokalizacja przedziału danych jest niewidoczna dla dewelopera. Magazyny zazwyczaj znajdują się na komputerze klienckim, ale aplikacje serwerowe mogą używać izolowanych magazynów do przechowywania informacji, personifikując użytkownika, w imieniu którego działają. Wydzielona pamięć masowa może także przechowywać informacje na serwerze, używając profilu mobilnego użytkownika, dzięki czemu takie informacje mogą podróżować razem z użytkownikiem mobilnym.

<a name="quotas"></a>

## <a name="quotas-for-isolated-storage"></a>Limity izolowanych magazynów

Przydział to limit ilości wydzielonej pamięci masowej, której można używać. Przydział zawiera bajty w przestrzeni plików, a także zapas skojarzony z katalogiem i innymi informacjami w magazynie. Magazyn izolowany korzysta z przydziałów uprawnień, które są limitami magazynu ustawionymi za pomocą <xref:System.Security.Permissions.IsolatedStoragePermission> obiektów. Jeśli spróbujesz zapisać dane, które przekraczają limit przydziału, <xref:System.IO.IsolatedStorage.IsolatedStorageException> zostanie zgłoszony wyjątek.  Zasady zabezpieczeń, które można modyfikować za pomocą narzędzia .NET Framework Configuration Tool (Mscorcfg.msc), określają uprawnienia udzielane kodowi. Kod, który został udzielony, <xref:System.Security.Permissions.IsolatedStoragePermission> jest ograniczony do używania nie więcej miejsca do magazynowania niż <xref:System.Security.Permissions.IsolatedStoragePermission.UserQuota%2A> zezwala na właściwość. Jednak kod może obejść przedziały uprawnień, prezentując różne tożsamości użytkownika, więc przydziały uprawnień pełnią rolę wytycznych dotyczących zachowania kodu, a nie stałych limitów zachowania kodu.

Przydziały nie są wymuszane w magazynach mobilnych. Z tego powodu kod musi mieć nieco wyższy poziom uprawnień, aby mógł ich używać. Wartości wyliczeniowe <xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByRoamingUser> i <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByRoamingUser> określają uprawnienia do używania wydzielonej pamięci masowej dla użytkownika mobilnego.

<a name="secure_access"></a>

## <a name="secure-access"></a>Bezpieczny dostęp

Wydzielona pamięć masowa umożliwia częściowo zaufanym aplikacjom przechowywanie danych w sposób kontrolowany przez zasady zabezpieczeń komputera. Jest to szczególnie przydatne w przypadku pobranych składników, które użytkownik może chcieć uruchomić z zachowaniem ostrożności. Zasady zabezpieczeń rzadko udzielają uprawnień kodu tego rodzaju podczas uzyskiwania dostępu do systemu plików przy użyciu standardowych mechanizmów We/Wy. Jednak kod uruchomiony na komputerze lokalnym, w sieci lokalnej lub w Internecie ma domyślnie udzielone prawo do używania wydzielonej pamięci masowej.

Na podstawie odpowiedniego poziomu zaufania administratorzy mogą określić, ile wydzielonej pamięci masowej jest dostępnej dla aplikacji lub użytkownika. Ponadto administratorzy mogą całkowicie usuwać utrwalone dane użytkownika. Aby utworzyć magazyn izolowany lub uzyskać do niego dostęp, należy przyznać mu odpowiednie <xref:System.Security.Permissions.IsolatedStorageFilePermission> uprawnienia.

Aby uzyskać dostęp do wydzielonej pamięci masowej, kod musi mieć wszystkie niezbędne natywne prawa platformy systemu operacyjnego. Wymagana jest zgodność z listami kontroli dostępu (ACL) określającymi, którzy użytkownicy mają prawa do używania systemu plików. Aplikacje programu .NET Framework mają już prawa systemu operacyjnego dotyczące dostępu do wydzielonej pamięci masowej, chyba że wykonują personifikację (specyficzna dla platformy). W tym przypadku aplikacja jest odpowiedzialna za sprawdzanie, czy tożsamość personifikowanego użytkownika ma prawidłowe prawa systemu operacyjnego do uzyskiwania dostępu do wydzielonej pamięci masowej. Ten dostęp oferuje uruchomionemu lub pobranemu z sieci web kodowi wygodny sposób odczytu lub zapisu w obszarze pamięci masowej związanym z konkretnym użytkownikiem.

Aby kontrolować dostęp do magazynu izolowanego, środowisko uruchomieniowe języka wspólnego używa <xref:System.Security.Permissions.IsolatedStorageFilePermission> obiektów. Każdy obiekt ma właściwości, które określają następujące wartości:

- Dozwolone użycie, które wskazuje typ dozwolonego dostępu. Wartości są elementami członkowskimi <xref:System.Security.Permissions.IsolatedStorageContainment> wyliczenia. Aby uzyskać więcej informacji na temat tych wartości, zobacz tabelę w następnej sekcji.

- Przydział pamięci, tak jak omówiono w poprzedniej sekcji.

Środowisko uruchomieniowe wymaga <xref:System.Security.Permissions.IsolatedStorageFilePermission> uprawnień, gdy kod próbuje otworzyć magazyn. Decyduje o tym, czy udzielić tego uprawnienia, w zależności od tego, jaki kod jest zaufany. Jeśli przyznano uprawnienia, dozwolone wartości przydziału użycia i magazynu są określane przez zasady zabezpieczeń i przez żądanie kodu dla <xref:System.Security.Permissions.IsolatedStorageFilePermission> . Zasady zabezpieczeń są ustawiane przy użyciu narzędzia .NET Framework Configuration Tool (Mscorcfg.msc). Wszystkie obiekty wywołujące w stosie wywołań są sprawdzane w celu zagwarantowania, że każdy obiekt wywołujący ma co najmniej jedno odpowiednie dozwolone użycie. Środowisko uruchomieniowe sprawdza też przydział określony przez kod, który otworzył lub utworzył magazyn, w którym mają być zapisywane pliki. Jeśli warunki są spełnione, jest udzielane uprawnienie. Przydział jest sprawdzany ponownie za każdym razem, gdy plik jest zapisywany w magazynie.

Kod aplikacji nie jest wymagany do zażądania uprawnień, ponieważ środowisko uruchomieniowe języka wspólnego udzieli <xref:System.Security.Permissions.IsolatedStorageFilePermission> odpowiedniej wartości na podstawie zasad zabezpieczeń. Jednak istnieją dobre powody, aby zażądać określonych uprawnień wymaganych przez aplikację, w tym <xref:System.Security.Permissions.IsolatedStorageFilePermission> .

<a name="allowed_usage"></a>

## <a name="allowed-usage-and-security-risks"></a>Dopuszczalne użycie i zagrożenia zabezpieczeń

Dozwolone użycie określone przez <xref:System.Security.Permissions.IsolatedStorageFilePermission> określa stopień, w jakim kod będzie mógł utworzyć i używać izolowanego magazynu. W poniższej tabeli pokazano, jak dozwolone użycie określone w uprawnieniu odpowiada typom izolacji, i podsumowano zagrożenia bezpieczeństwa skojarzone z każdym dozwolonym użyciem.

|Dozwolone użycie|Typy izolacji|Wpływ na zabezpieczenia|
|-------------------|---------------------|---------------------|
|<xref:System.Security.Permissions.IsolatedStorageContainment.None>|Użycie wydzielonej pamięci masowej nie jest dozwolone.|Brak wpływu na zabezpieczenia.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser>|Izolacja według użytkownika, domeny i zestawu. Każdy zestaw ma oddzielny podmagazyn w domenie. Magazyny używające tego uprawnienia są także niejawnie izolowane przez komputer.|Ten poziom uprawnień zostawia zasoby otwarte do nieautoryzowanego użycia, mimo że wymuszone przydziały utrudniają takie użycie. Takie działanie jest znanej pod nazwą „ataku typu odmowa usługi”.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByRoamingUser>|Analogicznie jak `DomainIsolationByUser` , ale magazyn jest zapisywany w lokalizacji, która będzie przenoszona w przypadku włączenia profilów użytkowników mobilnych, a limity przydziału nie są wymuszane.|Przydziały muszą być wyłączone, więc zasoby pamięci masowej są bardziej podatne na atak typu „odmowa usługi”.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByUser>|Izolacja według użytkownika i zestawu. Magazyny używające tego uprawnienia są także niejawnie izolowane przez komputer.|Na tym poziomie są wymuszane przydziały, aby zapobiegać atakom typu „odmowa usługi”. Taki sam zestaw w innej domenie może mieć dostęp do magazynu, przez co możliwe jest przeciekanie informacji między aplikacjami.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByRoamingUser>|Analogicznie jak `AssemblyIsolationByUser` , ale magazyn jest zapisywany w lokalizacji, która będzie przenoszona w przypadku włączenia profilów użytkowników mobilnych, a limity przydziału nie są wymuszane.|Tak samo jak w `AssemblyIsolationByUser` przypadku, ale bez przydziałów, ryzyko ataku typu "odmowa usługi" zwiększa się.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>|Izolacja według użytkownika. Zazwyczaj tylko narzędzia administracyjne lub narzędzia do debugowania używają tego poziomu uprawnień.|Dostęp z użyciem tego uprawnienia umożliwia kodowi wyświetlanie i usuwanie dowolnych plików lub katalogów użytkownika przechowywanych w wydzielonej pamięci masowej (niezależnie do izolacji zestawu). Zagrożenia to m.in. wycieki informacji i utrata danych.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.UnrestrictedIsolatedStorage>|Izolacja według wszystkich użytkowników, domen i zestawów. Zazwyczaj tylko narzędzia administracyjne lub narzędzia do debugowania używają tego poziomu uprawnień.|To uprawnienie tworzy potencjalną możliwość naruszenia zabezpieczeń wszystkich izolowanych magazynów wszystkich użytkowników.|

## <a name="safety-of-isolated-storage-components-with-regard-to-untrusted-data"></a>Bezpieczeństwo izolowanych składników magazynu w odniesieniu do niezaufanych danych

__Ta sekcja ma zastosowanie do następujących platform:__

- .NET Framework (wszystkie wersje)
- .NET Core 2.1 +
- .NET 5.0 +

.NET Framework i .NET Core oferują [izolowany magazyn](/dotnet/standard/io/isolated-storage) jako mechanizm utrwalania danych dla użytkownika, aplikacji lub składnika. Jest to starszy składnik przeznaczony głównie do realizacji przestarzałych scenariuszy zabezpieczeń dostępu do kodu.

Do odczytywania danych między granicami zaufania można używać różnych izolowanych interfejsów API i narzędzi magazynu. Na przykład odczyt danych z zakresu całego komputera może agregować dane z innych, prawdopodobnie mniej zaufanych kont użytkowników na komputerze. Składniki lub aplikacje odczytane z oddzielonych na cały komputer zakresów magazynu powinny mieć świadomość skutków odczytu tych danych.

### <a name="security-sensitive-apis-which-can-read-from-the-machine-wide-scope"></a>Zależne od zabezpieczeń interfejsy API, które mogą odczytywać z zakresu całego komputera

Składniki lub aplikacje, które wywołują dowolne z następujących interfejsów API, Odczytaj z zakresu całego komputera:

* [IsolatedStorageFile. GetEnumerator](/dotnet/api/system.io.isolatedstorage.isolatedstoragefile.getenumerator), przekazywanie zakresu, który zawiera flagę IsolatedStorageScope. Machine
* [IsolatedStorageFile.GetMachineStoreForApplication](/dotnet/api/system.io.isolatedstorage.isolatedstoragefile.getmachinestoreforapplication)
* [IsolatedStorageFile.GetMachineStoreForAssembly](/dotnet/api/system.io.isolatedstorage.isolatedstoragefile.getmachinestoreforassembly)
* [IsolatedStorageFile.GetMachineStoreForDomain](/dotnet/api/system.io.isolatedstorage.isolatedstoragefile.getmachinestorefordomain)
* [IsolatedStorageFile. GetStore](/dotnet/api/system.io.isolatedstorage.isolatedstoragefile.getstore), przekazywanie zakresu zawierającego flagę IsolatedStorageScope. Machine
* [IsolatedStorageFile. Remove](/dotnet/api/system.io.isolatedstorage.isolatedstoragefile.remove), przekazywanie zakresu zawierającego `IsolatedStorageScope.Machine` flagę

Działanie [Narzędzia izolowanego magazynu](/dotnet/framework/tools/storeadm-exe-isolated-storage-tool) `storeadm.exe` ma wpływ na to `/machine` , jak pokazano w poniższym kodzie:

```txt
storeadm.exe /machine [any-other-switches]
```

Narzędzie izolowanego magazynu jest dostępne jako część programu Visual Studio i zestawu SDK .NET Framework.

Jeśli aplikacja nie obejmuje wywołań do poprzednich interfejsów API lub jeśli przepływ pracy nie wymaga wywołania `storeadm.exe` w ten sposób, ten dokument nie ma zastosowania.

### <a name="impact-in-multi-user-environments"></a>Wpływ na środowiska z obsługą wielu użytkowników

Jak wspomniano wcześniej, wpływ na zabezpieczenia z tych interfejsów API wynika z danych zapisanych z jednego środowiska zaufania, które są odczytywane z innego środowiska zaufania. Magazyn izolowany zwykle używa jednej z trzech lokalizacji do odczytu i zapisu danych:

1. `%LOCALAPPDATA%\IsolatedStorage\`: Na przykład `C:\Users\<username>\AppData\Local\IsolatedStorage\` , dla `User` zakresu.
2. `%APPDATA%\IsolatedStorage\`: Na przykład `C:\Users\<username>\AppData\Roaming\IsolatedStorage\` , dla `User|Roaming` zakresu.
3. `%PROGRAMDATA%\IsolatedStorage\`: Na przykład `C:\ProgramData\IsolatedStorage\` , dla `Machine` zakresu.

Pierwsze dwie lokalizacje są izolowane dla poszczególnych użytkowników. System Windows zapewnia, że różne konta użytkowników na tym samym komputerze nie będą miały dostępu do folderów profilu użytkownika. Dwa różne konta użytkowników, którzy korzystają `User` ze `User|Roaming` sklepów lub nie będą widzieć danych nawzajem i nie mogą zakłócać działania danych.

Trzecia lokalizacja jest udostępniana dla wszystkich kont użytkowników na komputerze. Różne konta mogą odczytywać i zapisywać dane w tej lokalizacji, a następnie mogą zobaczyć, jak się znajdują.

Powyższe ścieżki mogą się różnić w zależności od używanej wersji systemu Windows.

Teraz Rozważmy system z obsługą dwóch użytkowników z dwoma zarejestrowanymi użytkownikami _Mallory_ i _Roberta_. Mallory ma możliwość uzyskiwania dostępu do katalogu profilu użytkownika `C:\Users\Mallory\` i może uzyskać dostęp do udostępnionej lokalizacji magazynu na całym komputerze `C:\ProgramData\IsolatedStorage\` . Nie może uzyskać dostępu do katalogu profilu użytkownika Roberta `C:\Users\Bob\` .

Jeśli Mallory życzy sobie atakującej, może ona zapisywać dane w lokalizacji przechowywania w całej maszynie, a następnie próbować wpływać na odczytanie ze sklepu na całym komputerze. Gdy Robert uruchamia aplikację, która odczytuje z tego magazynu, ta aplikacja będzie działać na Mallory danych umieszczonych w tym miejscu, ale w kontekście konta użytkownika Roberta. W pozostałej części tego dokumentu opisano różne wektory ataków oraz czynności, które można wykonać, aby zminimalizować ryzyko związane z atakami.

__Uwaga:__ Aby atak miał miejsce, Mallory wymaga:

* Konto użytkownika na komputerze.
* Możliwość umieszczenia pliku w znanej lokalizacji w systemie plików.
* Wiedza o tym, że Robert będzie w pewnym momencie uruchamiać aplikację, która próbuje odczytać te dane.

Nie są to wektory zagrożeń, które mają zastosowanie w standardowych środowiskach klasycznych jednego użytkownika, takich jak komputery domowe lub stacje robocze przedsiębiorstwa z pojedynczym pracownikiem.

#### <a name="elevation-of-privilege"></a>Podniesienie uprawnień

__Podniesienie poziomu uprawnień__ występuje, gdy aplikacja Roberta odczytuje plik Mallory i automatycznie próbuje wykonać jakąś akcję na podstawie zawartości tego ładunku. Rozważmy aplikację, która odczytuje zawartość skryptu uruchamiania ze sklepu dla całego komputera i przekazuje tę zawartość do programu `Process.Start` . Jeśli Mallory może umieścić złośliwy skrypt w sklepie dla całej maszyny, gdy Robert uruchomi swoją aplikację:

* Aplikacja analizuje i uruchamia złośliwy skrypt Mallory _w kontekście profilu użytkownika Roberta_.
* Mallory uzyskuje dostęp do konta Roberta na komputerze lokalnym.

#### <a name="denial-of-service"></a>Odmowa usługi

Atak __typu "odmowa usługi"__ występuje, gdy aplikacja Roberta odczytuje plik i awarie Mallory, lub w przeciwnym razie przestaje działać poprawnie. Rozważ ponownie aplikację wspomnianą wcześniej, która próbuje analizować skrypt uruchamiania ze sklepu dla całego komputera. Jeśli Mallory może umieścić plik z nieprawidłowo utworzoną zawartością w sklepie dla całego komputera, może:

* Przed wczesnym wyrzucaniem przez aplikację Roberta wyjątku w ścieżce początkowej.
* Uniemożliwiaj pomyślne uruchomienie aplikacji z powodu wyjątku.

Następnie odmówił Roberta możliwość uruchomienia aplikacji przy użyciu własnego konta użytkownika.

#### <a name="information-disclosure"></a>Ujawnienie informacji

Atak z __ujawnianiem informacji__ występuje, gdy Mallory może dowiedzieć się, jak wycofać zawartość pliku, do którego Mallory zwykle nie ma dostępu. Należy wziąć pod uwagę, że Robert ma plik tajny *C:\Users\Bob\secret.txt* Mallory. Zna ścieżkę do tego pliku, ale nie może go odczytać, ponieważ system Windows zabrania sobie dostępu do katalogu profilu użytkownika Roberta.

Zamiast tego Mallory umieszcza twarde łącze w sklepie dla całego komputera. Jest to specjalny rodzaj pliku, który nie zawiera żadnej zawartości, a nie wskazuje na inny plik na dysku. Próba odczytania pliku linku twardego spowoduje odczytanie zawartości pliku, którego dotyczy link. Po utworzeniu twardego linku Mallory nadal nie można odczytać zawartości pliku, ponieważ nie ma dostępu do elementu docelowego ( `C:\Users\Bob\secret.txt` ) łącza. Jednak _Robert ma_ dostęp do tego pliku.

Gdy aplikacja Roberta odczytuje dane ze sklepu na całym komputerze, teraz przypadkowo odczytuje zawartość `secret.txt` pliku, podobnie jak w przypadku, gdy sam plik był obecny w sklepie dla całego komputera. Gdy aplikacja Roberta zostanie zakończona, jeśli spróbuje ponownie zapisać plik w sklepie dla całego komputera, spowoduje to zakończenie umieszczania rzeczywistej kopii pliku w katalogu * C:\ProgramData\IsolatedStorage \* . Ponieważ ten katalog jest odczytywany przez dowolnego użytkownika na komputerze, Mallory może teraz odczytać zawartość pliku.

### <a name="best-practices-to-defend-against-these-attacks"></a>Najlepsze rozwiązania dotyczące obrony przed atakami

__Ważne:__ Jeśli środowisko ma wielu niezaufanych użytkowników, nie wywołuj interfejsu API ani __nie__ `IsolatedStorageFile.GetEnumerator(IsolatedStorageScope.Machine)` Wywołaj tego narzędzia `storeadm.exe /machine /list` . Oba te założono, że działają na zaufanych danych. Jeśli osoba atakująca może obsłużyć złośliwy ładunek w sklepie dla całego komputera, ten ładunek może prowadzić do podniesienia uprawnień w kontekście użytkownika, który uruchamia te polecenia.

Jeśli działa w środowisku z obsługą kilku użytkowników, należy rozważyć użycie izolowanych funkcji magazynu, które są ukierunkowane na zakres _maszyn_ . Jeśli aplikacja musi odczytywać dane z lokalizacji w całej maszynie, wolisz odczytywać dane z lokalizacji, która jest tylko do zapisu na kontach administratorów. `%PROGRAMFILES%`Katalog i `HKLM` gałąź rejestru to przykłady lokalizacji zapisywalnych przez administratorów i odczytywane przez wszystkich użytkowników. Dane odczytane z tych lokalizacji są uważane za wiarygodne.

Jeśli aplikacja musi używać zakresu _maszyn_ w środowisku wielu użytkowników, zweryfikuj zawartość dowolnego pliku odczytywanego ze sklepu dla całego komputera. Jeśli aplikacja odserializacja grafów obiektów z tych plików, rozważ użycie bezpieczniejszych serializacji, takich jak `XmlSerializer` zamiast niebezpiecznych serializatorów, takich jak `BinaryFormatter` lub `NetDataContractSerializer` . Należy zachować ostrożność przy użyciu głęboko zagnieżdżonych wykresów obiektów lub grafów obiektów, które wykonują alokację zasobów na podstawie zawartości pliku.

<a name="isolated_storage_locations"></a>

## <a name="isolated-storage-locations"></a>Lokalizacje izolowanych magazynów

Czasami jest ono pomocne podczas weryfikowania zmiany w wydzielonej pamięci masowej za pomocą systemu plików systemu operacyjnego. Czasami mogą być też potrzebne informacje o lokalizacji plików wydzielonej pamięci masowej. Ta lokalizacja zmienia się w zależności od systemu operacyjnego. W poniższej tabeli pokazano główne lokalizacje w najbardziej popularnych systemach operacyjnych, w których jest tworzona wydzielona pamięć masowa. Znajdź katalogi Microsoft\IsolatedStorage w tej lokalizacji głównej. Musisz zmienić ustawienia folderów, aby wyświetlać ukryte pliki i foldery, co umożliwi zobaczenie wydzielonej pamięci masowej w systemie plików.

|System operacyjny|Lokalizacja w systemie plików|
|----------------------|-----------------------------|
|Windows 2000, Windows XP, Windows Server 2003 (uaktualnienie z systemu Windows NT 4.0)|Magazyny z obsługą roamingu =<br /><br /> \<SYSTEMROOT>\Profiles \\<użytkownik \> \Dane danych<br /><br /> Magazyny bez obsługi roamingu =<br /><br /> \<SYSTEMROOT>\Profiles \\<użytkownik \> \Ustawienia lokalne\Dane|
|Windows 2000 — czysta instalacja (oraz uaktualnienia z systemu Windows 98 i Windows NT 3.51)|Magazyny z obsługą roamingu =<br /><br /> \<SYSTEMDRIVE>\Dokumenty i ustawienia \\<użytkownik \> \Dane danych<br /><br /> Magazyny bez obsługi roamingu =<br /><br /> \<SYSTEMDRIVE>\Documents and Settings \\<użytkownika \> \Ustawienia Lokalne\dane — dane|
|Windows XP, Windows Server 2003 — czysta instalacja (i uaktualnienia z systemu Windows 2000 i Windows 98)|Magazyny z obsługą roamingu =<br /><br /> \<SYSTEMDRIVE>\Dokumenty i ustawienia \\<użytkownik \> \Dane danych<br /><br /> Magazyny bez obsługi roamingu =<br /><br /> \<SYSTEMDRIVE>\Documents and Settings \\<użytkownika \> \Ustawienia Lokalne\dane — dane|
|Windows 8, Windows 7, Windows Server 2008, Windows Vista|Magazyny z obsługą roamingu =<br /><br /> \<SYSTEMDRIVE>\Users \\<użytkownika \> \AppData\Roaming<br /><br /> Magazyny bez obsługi roamingu =<br /><br /> \<SYSTEMDRIVE>\Users \\<użytkownika \> \AppData\Local|

<a name="isolated_storage_tasks"></a>

## <a name="creating-enumerating-and-deleting-isolated-storage"></a>Tworzenia, wyliczania i usuwania izolowanych magazynów

.NET Framework zawiera trzy klasy w <xref:System.IO.IsolatedStorage> przestrzeni nazw, które ułatwiają wykonywanie zadań obejmujących izolowany magazyn:

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>, pochodzi z <xref:System.IO.IsolatedStorage.IsolatedStorage?displayProperty=nameWithType> i zapewnia podstawowe zarządzanie przechowywanymi plikami zestawu i aplikacji. Wystąpienie <xref:System.IO.IsolatedStorage.IsolatedStorageFile> klasy reprezentuje pojedynczy magazyn znajdujący się w systemie plików.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>pochodzi z <xref:System.IO.FileStream?displayProperty=nameWithType> i zapewnia dostęp do plików w sklepie.

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>jest wyliczeniem umożliwiającym tworzenie i wybieranie magazynu z odpowiednim typem izolacji.

Klasy wydzielonej pamięci masowej umożliwiają tworzenie, wyliczanie oraz usuwanie wydzielonej pamięci masowej. Metody wykonywania tych zadań są dostępne za pomocą <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektu. Niektóre operacje wymagają posiadania <xref:System.Security.Permissions.IsolatedStorageFilePermission> uprawnienia, które reprezentuje prawo do administrowania izolowanym magazynem. może być również konieczne posiadanie praw systemu operacyjnego w celu uzyskania dostępu do pliku lub katalogu.

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
|[Typy izolacji](types-of-isolation.md)|Opis różnych typów izolacji.|
|[Instrukcje: Uzyskiwanie magazynów dla izolowanego magazynu](how-to-obtain-stores-for-isolated-storage.md)|Stanowi przykład użycia <xref:System.IO.IsolatedStorage.IsolatedStorageFile> klasy w celu uzyskania magazynu izolowanego przez użytkownika i zestaw.|
|[Instrukcje: Wykazywanie magazynów dla izolowanego magazynu](how-to-enumerate-stores-for-isolated-storage.md)|Pokazuje, w jaki sposób używać <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> metody do obliczania rozmiaru całego izolowanego magazynu dla użytkownika.|
|[Instrukcje: Usuwanie danych z izolowanego magazynu](how-to-delete-stores-in-isolated-storage.md)|Pokazuje, jak używać <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A?displayProperty=nameWithType> metody na dwa różne sposoby usuwania izolowanych sklepów.|
|[Instrukcje: Przewidywanie warunków braku miejsca w izolowanym magazynie](how-to-anticipate-out-of-space-conditions-with-isolated-storage.md)|Opis sposobu mierzenia ilości pozostałego miejsca w izolowanym magazynie.|
|[Instrukcje: Tworzenie plików i katalogów w izolowanym magazynie](how-to-create-files-and-directories-in-isolated-storage.md)|Przykłady tworzenia plików i katalogów w izolowanym magazynie.|
|[Instrukcje: Wyszukiwanie istniejących plików i katalogów w izolowanym magazynie](how-to-find-existing-files-and-directories-in-isolated-storage.md)|Opis sposobu odczytywania struktury katalogów i plików w wydzielonej pamięci masowej.|
|[Instrukcje: Odczyt i zapis w plikach w izolowanym magazynie](how-to-read-and-write-to-files-in-isolated-storage.md)|Przykład zapisywania ciągu w pliku w wydzielonej pamięci masowej i odczytywania go z powrotem.|
|[Instrukcje: Usuwanie plików i katalogów w izolowanym magazynie](how-to-delete-files-and-directories-in-isolated-storage.md)|Opis sposobu usuwania plików i katalogów wydzielonej pamięci masowej.|
|[We/wy plików i strumieni](index.md)|Opis sposobu synchronicznego i asynchronicznego uzyskiwania dostępu do pliku i strumienia danych.|

<a name="reference"></a>

## <a name="reference"></a>Tematy pomocy

- <xref:System.IO.IsolatedStorage.IsolatedStorage?displayProperty=nameWithType>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream?displayProperty=nameWithType>

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope?displayProperty=nameWithType>
