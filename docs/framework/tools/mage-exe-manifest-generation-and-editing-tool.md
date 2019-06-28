---
title: Mage.exe (Narzędzie generowania manifestu i edytowania)
ms.date: 12/06/2018
helpviewer_keywords:
- Manifest Generation and Editing tool
- Mage.exe
ms.assetid: 77dfe576-2962-407e-af13-82255df725a1
ms.openlocfilehash: 549eca835b2161429668a2ee340a71dfae658524
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422356"
---
# <a name="mageexe-manifest-generation-and-editing-tool"></a>Mage.exe (Narzędzie generowania manifestu i edytowania)

Generowanie manifestu i narzędzia do edycji (*Mage.exe*) jest narzędziem wiersza polecenia, który obsługuje tworzenie i edycję manifestów aplikacji i wdrożenia. Narzędzie wiersza polecenia *Mage.exe* może działać zarówno w przypadku skryptów wsadowych, jak i innych aplikacji opartych na Windows, łącznie z aplikacjami ASP.NET.

Można również użyć *MageUI.exe*, graficznego aplikacji, zamiast *Mage.exe*. Aby uzyskać więcej informacji, zobacz [MageUI.exe (Manifest Generation i graficzny klient Editing Tool)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio. Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

Dwie wersje *Mage.exe* i *MageUI.exe* są dołączone do programu Visual Studio. Aby wyświetlić informacje o wersji, uruchom *MageUI.exe*, wybierz opcję **pomocy**i wybierz **o**. W tej dokumentacji opisano wersję 4.0.x.x programów *Mage.exe* i *MageUI.exe*.

## <a name="syntax"></a>Składnia

```console
Mage [commands] [commandOptions]
```

## <a name="parameters"></a>Parametry

W poniższej tabeli przedstawiono polecenia obsługiwane przez *Mage.exe*. Aby uzyskać więcej informacji na temat opcji obsługiwanych przez te polecenia, zobacz [opcje poleceń New i Update](#new-and-update-command-options) i [Podpisz opcje polecenia](#sign-command-options).

|Polecenie|Opis|
|-------------|-----------------|
|**-DW ClearApplicationCache**|Czyści pamięć podręczną pobranych aplikacji ze wszystkich aplikacji działających tylko w trybie online.|
|**-n, - New** *Typ_pliku [newOptions]*|Tworzy nowy plik danego typu. Prawidłowymi typami są:<br /><br /> -   `Deployment`: Tworzy nowy manifest wdrożenia.<br />-   `Application`: Tworzy nowy manifest aplikacji.<br /><br /> Jeśli nie określono żadnych dodatkowych parametrów dla tego polecenia, zostanie utworzony plik odpowiedniego typu, z odpowiednimi domyślnymi tagami oraz wartościami atrybutów.<br /><br /> Użyj **- ToFile** opcji (zobacz w poniższej tabeli) aby określić nazwę pliku i ścieżkę nowego pliku.<br /><br /> Użyj **- FromDirectory** opcji (zobacz w poniższej tabeli), aby utworzyć manifest aplikacji ze wszystkimi zestawami aplikacji dodanymi do \<zależności > sekcji manifestu.|
|**-u,-Update** *[ścieżka] [updateOptions]*|Wprowadza co najmniej jedną zmianę w pliku manifestu. Nie trzeba określać typu edytowanego pliku. Program Mage.exe zbada plik za pomocą zestawu algorytmów heurystycznych i ustali, czy jest to manifest wdrożenia, czy aplikacji.<br /><br /> Jeśli został już podpisany plik za pomocą certyfikatu **— aktualizacja** usunie blok podpisu klucza. Dzieje się tak dlatego, że podpis klucza zawiera skrót pliku i modyfikacja pliku spowoduje, że skrót będzie nieprawidłowy.<br /><br /> Użyj **- ToFile** opcji (zobacz w poniższej tabeli) aby określić nową nazwę pliku i ścieżkę, zamiast nadpisywać istniejący plik.|
|**-s, — logowanie** `[signOptions]`|Używa pary kluczy lub certyfikatu X509 w celu podpisania pliku. Podpisy są wstawiane jako elementy XML wewnątrz plików.<br /><br /> Użytkownik musi być połączony z Internetem podczas podpisywania manifestu określającego **- TimestampUri** wartość.|
|**-ver — Sprawdź** *[nazwa pliku manifestu]*|Sprawdza poprawność podpisu manifestu. Nie można łączyć z innymi poleceniami. <br/><br/>**Dostępne w programie .NET Framework 4.7 i nowszych wersjach.**|
|**-h,-? — Pomoc** *[pełne]*|Opisuje wszystkie z dostępnych poleceń i ich opcji. Określ `verbose` umożliwia uzyskanie szczegółowej Pomocy.|

## <a name="new-and-update-command-options"></a>Nowe i zaktualizuj opcje polecenia

W poniższej tabeli przedstawiono opcje obsługiwane przez `-New` i `-Update` poleceń:

|Opcje|Wartość domyślna|Dotyczy:|Opis|
|-------------|-------------------|----------------|-----------------|
|**-, — algorytm**|sha1RSA|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Określa algorytm, za pomocą którego zostaną wygenerowane skróty zależności. Wartością musi być „sha256RSA” lub „sha1RSA”.<br /><br /> Należy używać z opcją „-Update”. Ta opcja jest ignorowana, gdy używana jest opcja „-Sign”.|
|**-appc, -AppCodeBase** `manifestReference`||Manifesty wdrożenia.|Wstawia odwołanie do adresu URL lub ścieżki pliku do pliku manifestu aplikacji. Ta wartość musi być pełną ścieżką do manifestu aplikacji.|
|**-appm, -AppManifest** `manifestPath`||Manifesty wdrożenia.|Wstawia do manifestu wdrożenia odwołanie do manifestu wdrażanej aplikacji.<br /><br /> Plik wskazywany przez `manifestPath` musi istnieć lub *Mage.exe* zgłosi błąd. Jeśli plik wskazywany przez `manifestPath` manifestu aplikacji nie jest *Mage.exe* zgłosi błąd.|
|**-cf, -CertFile** `filePath`||Wszystkie typy plików.|Określa lokalizację X509 certyfikatu cyfrowego używanego do podpisywania pliku manifestu lub licencji. Ta opcja może służyć w połączeniu z **-hasło** opcję, jeśli certyfikat wymaga hasła dla plików wymiany informacji osobistych (PFX). Począwszy od programu .NET Framework 4.7, jeśli plik nie zawiera klucza prywatnego z kombinacją **- CryptoProvider** i **- KeyContainer** opcje jest wymagana.<br/><br/>Począwszy od .NET Framework 4.6.2, *Mage.exe* podpisuje manifesty CNG, jak również CAPI certyfikatów.|
|**-ch, -CertHash** `hashSignature`||Wszystkie typy plików.|Skrót certyfikatu cyfrowego przechowywanego w osobistym magazynie certyfikatów na komputerze klienta. Odpowiada on ciągowi odcisku palca certyfikatu cyfrowego wyświetlanego w konsoli certyfikatów systemu Windows.<br /><br /> `hashSignature` może to być albo wielkie lub małe i można go dostarczyć w postaci pojedynczego ciągu lub z oktetami odcisku palca rozdzielonymi spacjami i całość odcisku palca ujęta w znaki cudzysłowu.|
|**-csp, -CryptoProvider** `provider-name`||Wszystkie typy plików.|Określa nazwę dostawcy usług kryptograficznych (CSP), który zawiera kontener klucza prywatnego. Ta opcja wymaga **- KeyContainer** opcji.<br/><br/>Ta opcja jest dostępna, począwszy od programu .NET Framework 4.7.|
|**-fd, -FromDirectory** `directoryPath`||Manifesty aplikacji.|Wypełnia manifest aplikacji opisami wszystkich zestawów i plików znalezionych w `directoryPath`, w tym wszystkie podkatalogi, gdzie `directoryPath` jest katalogiem, który zawiera aplikację, którą chcesz wdrożyć. Dla każdego pliku w katalogu *Mage.exe* decyduje, czy plik jest zestawem, czy plikiem statycznym. Jeśli jest to zespół, dodaje `<dependency>` tagu i `installFrom` atrybutu do aplikacji z nazwą, baza kodu i wersją zestawu. Jeśli jest to plik statyczny, dodaje `<file>` tagu. *Mage.exe* będzie również używać prostego zestawu algorytmów heurystycznych w celu wykrycia głównego pliku wykonywalnego aplikacji i oznaczy go jako punkt wejścia aplikacji ClickOnce w manifeście.<br /><br /> *Mage.exe* nigdy nie automatycznie przywróci Oznacz plik jako plik "dane". Tę czynność należy wykonać ręcznie. Aby uzyskać więcej informacji, zobacz [jak: Uwzględnianie pliku danych w aplikacji ClickOnce](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application).<br /><br /> *Mage.exe* generuje również skrót dla każdego pliku na podstawie jego rozmiaru. Technologia ClickOnce używa tych skrótów, aby zagwarantować, że nikt nie ingerował w pliki wdrożenia od czasu utworzenia manifestu. W przypadku zmiany plików w danym wdrożeniu, możesz uruchomić *Mage.exe* z **— aktualizowanie** polecenia i **- FromDirectory** opcja która spowoduje zaktualizowanie skróty i zestawu wersje wszystkich plików.<br /><br /> **-FromDirectory** dołączy wszystkie pliki w podkatalogach znalezionych wewnątrz katalogu wszystkich `directoryPath`.<br /><br /> Jeśli używasz **- FromDirectory** z **— aktualizacja** polecenia *Mage.exe* spowoduje usunięcie wszystkich plików w manifeście aplikacji, które nie istnieją już w katalogu.|
|**-Jeśli - IconFile**  `filePath`||Manifesty aplikacji.|Określa pełną ścieżkę do pliku ikony ICO. Ta ikona pojawia się obok nazwy aplikacji w menu Start oraz we wpisie w aplecie Dodaj lub usuń programy. Jeśli nie zostanie dostarczona ikona, będzie używana ikona domyślna.|
|**-adres ip, - IncludeProviderURL**  `url`|true|Manifesty wdrożenia.|Wskazuje, czy manifest wdrożenia zawiera wartość lokalizacji aktualizacji ustawioną **- ProviderURL**.|
|**-i,-zainstaluj** `willInstall`|true|Manifesty wdrożenia.|Wskazuje, czy aplikacja ClickOnce ma zostać zainstalowana na komputerze lokalnym, czy ma być uruchamiana z sieci Web. Instalowanie aplikacji spowoduje, że będzie ona widoczna w Windows **Start** menu. Prawidłowymi wartościami są „true” lub „t” oraz „false” lub „f”.<br /><br /> Jeśli określisz **- MinVersion** opcji, a użytkownik ma wersję mniej niż **- MinVersion** zainstalowany, wymusi to instalację aplikacji, niezależnie od wartości, który jest przekazywany do **- Zainstaluj**.<br /><br /> Tej opcji nie można używać z **- BrowserHosted** opcji. Próba określenia obu tych opcji dla jednego manifestu spowoduje błąd.|
|**-kc, -KeyContainer** `name`||Wszystkie typy plików.|Określa kontener klucza, który zawiera nazwę klucza prywatnego. Ta opcja wymaga **CryptoProvider** opcji.<br/><br/>Ta opcja jest dostępna, począwszy od programu .NET Framework 4.7.|
|**-mv, - MinVersion**  `[version]`|Wersja wymieniona w manifeście wdrożenia ClickOnce, określony przez **— wersja** flagi.|Manifesty wdrożenia.|Minimalna wersja aplikacji, jaką może uruchomić użytkownik. Ta flaga powoduje, że nazwana wersja aplikacji staje się wymaganą aktualizacją. Jeśli zostanie wydana wersja produktu z aktualizacją dotyczącą ważnej zmiany lub krytycznej wady zabezpieczeń, można użyć tej flagi, aby określić, że ta aktualizacja musi zostać zainstalowana, a użytkownik nie może kontynuować używania wcześniejszych wersji.<br /><br /> `version` ma tą samą semantyką jako argument **— wersja** flagi.|
|**-n, — nazwa** `nameString`|Deploy|Wszystkie typy plików.|Nazwa, która jest używana do identyfikacji aplikacji. Technologia ClickOnce będzie używała tej nazwy, aby identyfikować aplikację w **Start** menu (Jeśli aplikacja jest skonfigurowana do instalowania się) i w oknach dialogowych podnoszenia poziomu uprawnień. **Uwaga:**  Jeśli aktualizujesz istniejący manifest, a nie określisz nazwy wydawcy z tą opcją *Mage.exe* zaktualizuje manifest przy użyciu nazwy organizacji zdefiniowanej na komputerze. Aby użyć innej nazwy, należy użyć tej opcji i określić odpowiednią nazwę wydawcy.|
|**-pwd, — hasło** `passwd`||Wszystkie typy plików.|Hasło używane do podpisywania manifestu za pomocą certyfikatu cyfrowego. Należy używać w połączeniu z **- CertFile** opcji.|
|**Procesor -p** `processorValue`|Msil|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Architektura mikroprocesora, na której będzie uruchomiona dystrybucja. Ta wartość jest wymagana, jeśli jest przygotowywanych kilka instalacji, których zestawy są wstępnie kompilowane dla określonego mikroprocesora. Prawidłowe wartości to `msil`, `x86`, `ia64`, i `amd64`. `msil` to Microsoft język pośredni, co oznacza, że wszystkie Twoje zestawy są niezależne od platformy i środowisko uruchomieniowe języka wspólnego (CLR) będzie just-in-time skompilować je, gdy aplikacja jest pierwszym uruchomieniu.|
|**-pu,** **-ProviderURL** `url`||Manifesty wdrożenia.|Określa adres URL, pod którym technologia ClickOnce będzie szukać aktualizacji aplikacji.|
|**-pub,-wydawcy** `publisherName`||Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Dodaje nazwę wydawcy do opisu elementu manifestu wdrożenia lub aplikacji. Gdy jest używana w manifeście aplikacji **- UseManifestForTrust** musi być także określona wartość "true" lub "t"; w przeciwnym razie ten parametr zgłosi błąd.|
|**-s, - SupportURL**  `url`||Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Określa łącze, które pojawia się w aplecie Dodaj lub usuń programy dla aplikacji ClickOnce.|
|**-oś, - TimestampUri** `uri`||Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Adres URL usługi cyfrowego oznaczania znacznikami czasu. Oznaczenie manifestu znacznikiem czasu zapobiega konieczności ponownego podpisania manifestu, jeśli certyfikat cyfrowy wygaśnie przed wdrożeniem następnej wersji aplikacji. Aby uzyskać więcej informacji, zobacz [Windows członkowie programu głównych certyfikatów](https://go.microsoft.com/fwlink/?LinkId=159000).|
|**-t, - ToFile** `filePath`|-New:<br />-Wdrożenie: odpowiednio deploy.application<br />-Aplikacji: application.exe.manifest<br />-Aktualizacja:<br />-Plik wejściowy.|Wszystkie typy plików.|Określa ścieżkę wyjściową utworzonego lub zmodyfikowanego pliku.<br /><br /> Jeśli **- ToFile** nie jest podany, gdy używasz **— nowe**, plik wyjściowy zostanie zapisany w bieżącym katalogu roboczym. Jeśli **- ToFile** nie jest podany, gdy używasz **— aktualizacja**, *Mage.exe* zapisze ten plik ponownie do pliku wejściowego.|
|**-tr, -TrustLevel** `level`|Wartość określana na podstawie strefy, w której znajduje się adres URL aplikacji.|Manifesty aplikacji.|Poziom zaufania, który zostanie przyznany aplikacji na komputerach klientów. Dostępne wartości to Internet, Intranet i FullTrust.|
|**-um, - UseManifestForTrust** `willUseForTrust`|False|Manifesty aplikacji.|Określa, czy podpis cyfrowy manifestu aplikacji będzie używany do podejmowania decyzji dotyczących zaufania, gdy aplikacja zostanie uruchomiona na komputerze klienckim. Określenie wartości „true” lub „t” wskazuje, że manifest aplikacji zostanie użyty do podejmowania decyzji dotyczących zaufania. Określenie wartości „false” lub „f” wskazuje, że zostanie użyty podpis manifestu wdrożenia.|
|**-v,-wersja** `versionNumber`|1.0.0.0|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Wersja wdrożenia. Argument musi być prawidłowym ciągiem wersji w formacie "*N.N.N.N*", gdzie"*N*" jest liczbą całkowitą bez znaku 32-bitowych.|
|**-wpf, - WPFBrowserApp**  `isWPFApp`|false|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Tej flagi należy używać tyko wtedy, gdy aplikacja jest aplikacją programu Windows Presentation Foundation (WPF), która będzie obsługiwana wewnątrz programu Internet Explorer i nie jest autonomicznym plikiem wykonywalnym. Prawidłowymi wartościami są „true” lub „t” oraz „false” lub „f”.<br /><br /> Dla manifestów aplikacji wstawia `hostInBrowser` atrybutu w ramach `entryPoint` elementu w manifeście aplikacji.<br /><br /> Przypadku manifestów wdrożenia ustawia `install` atrybutu na `deployment` elementu wartość false i zapisuje manifest wdrożenia z rozszerzeniem XBAP. Określenie tego argumentu wraz z **-Zainstaluj** spowoduje błąd, ponieważ aplikacja obsługiwana w przeglądarce nie jest zainstalowaną aplikacją offline.|

## <a name="sign-command-options"></a>Opcje polecenia sign

W poniższej tabeli przedstawiono opcje obsługiwane przez `-Sign` polecenia, które mają zastosowanie do wszystkich typów plików.

|Opcje|Opis|
|-------------|-----------------|
|**-cf, -CertFile** `filePath`|Określa lokalizację certyfikatu cyfrowego używanego do podpisania manifestu. Ta opcja może służyć w połączeniu z **-hasło** opcję, jeśli certyfikat wymaga hasła dla plików wymiany informacji osobistych (PFX). Począwszy od programu .NET Framework 4.7, jeśli plik nie zawiera klucza prywatnego z kombinacją **- CryptoProvider** i **- KeyContainer** opcje jest wymagana.<br/><br/>Począwszy od .NET Framework 4.6.2, *Mage.exe* podpisuje manifesty CNG, jak również CAPI certyfikatów.|
|**-ch, -CertHash** `hashSignature`|Skrót certyfikatu cyfrowego przechowywanego w osobistym magazynie certyfikatów na komputerze klienta. Odpowiada właściwości odcisku palca certyfikatu cyfrowego wyświetlanego na konsoli certyfikatów systemu Windows.<br /><br /> `hashSignature` może to być albo wielkie lub małe litery i może być dostarczone w postaci pojedynczego ciągu lub ciągu z oktetami odcisku palca rozdzielonymi spacjami i całość odcisku palca ujęta w znaki cudzysłowu.|
**-csp, -CryptoProvider** `provider-name`|Określa nazwę dostawcy usług kryptograficznych (CSP), który zawiera kontener klucza prywatnego. Ta opcja wymaga **- KeyContainer** opcji.<br/><br/>Ta opcja jest dostępna, począwszy od programu .NET Framework 4.7.|
|**-kc, -KeyContainer** `name`|Określa kontener klucza, który zawiera nazwę klucza prywatnego. Ta opcja wymaga **CryptoProvider** opcji.<br/><br/>Ta opcja jest dostępna, począwszy od programu .NET Framework 4.7.|
|**-pwd, — hasło** `passwd`|Hasło używane do podpisywania manifestu za pomocą certyfikatu cyfrowego. Należy używać w połączeniu z **- CertFile** opcji.|
|**-t, - ToFile** `filePath`|Określa ścieżkę wyjściową utworzonego lub zmodyfikowanego pliku.|

## <a name="remarks"></a>Uwagi

Wszystkie argumenty *Mage.exe* jest rozróżniana wielkość liter. Polecenia i opcje mogą być poprzedzone kreską (-) lub ukośnikiem (/).

Wszystkie argumenty używane z **-logowania** można w dowolnym momencie za pomocą polecenia **— nowe** lub **— aktualizacja** także polecenia. Poniższe polecenia są równoważne.

```console
mage -Sign c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
```

> [!NOTE]
> Począwszy od .NET Framework w wersji 4.6.2 certyfikatów CNG są również obsługiwane.

 Podpisywanie jest ostatnim zadaniem, które należy wykonać, ponieważ podpisany dokument używa skrótu pliku w celu weryfikacji, czy podpis jest prawidłowy dla dokumentu. W przypadku wprowadzenia jakiejkolwiek zmiany w podpisanym pliku należy podpisać go ponownie. Jeśli rejestrujesz dokumentów, który był wcześniej podpisany *Mage.exe* zastąpi stary podpis nowym.

 Kiedy używasz **- AppManifest** opcja wypełnienia manifestu wdrożenia, *Mage.exe* założy, że manifest aplikacji będą znajdować się w tym samym katalogu co wdrożenia manifestu w podkatalog o nazwie po bieżąca wersja wdrożenia i odpowiednio skonfiguruje manifest wdrożenia. Jeśli manifest aplikacji zostaną umieszczone w innym miejscu, użyj **- AppCodeBase** opcję, aby ustawić alternatywną lokalizację.

 Manifesty wdrożenia i aplikacji muszą zostać podpisane przed wdrożeniem aplikacji. Aby uzyskać wskazówki dotyczące podpisywania manifestów, zobacz [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview).

 **- TrustLevel** opcja dla manifestów aplikacji opisuje zestaw uprawnień, aplikacja wymaga do uruchomienia na komputerze klienckim. Domyślnie aplikacjom jest przypisywany poziom zaufania, na podstawie *strefy* , w której umieszczony ich adres URL. Aplikacje wdrożone przez sieć firmową są zazwyczaj umieszczane w strefie Intranet, podczas gdy te wdrożone przez Internet umieszczane są w strefie Internet. Obie strefy zabezpieczeń nakładają na aplikację ograniczenia w zakresie dostępu do lokalnych zasobów, przy czym strefa Intranet ma nieco łagodniejsze ograniczenia niż strefa Internet. Strefa FullTrust udziela aplikacji pełnego dostępu do lokalnych zasobów komputera. Jeśli używasz **- TrustLevel** opcji do umieszczenia aplikacji w tej strefie, składnik Menedżer zaufania środowiska CLR będzie monitować użytkownika o decyzję, czy użytkownik chce udzielić tego wyższego poziomu zaufania. Jeśli aplikacja jest wdrażana przez sieć firmową, można użyć narzędzia Wdrażanie zaufanych aplikacji, aby podnieść poziom zaufania aplikacji bez monitowania użytkownika.

 Manifesty aplikacji obsługują także niestandardowe sekcje zaufania. Pomaga to aplikacji przestrzegać reguły zabezpieczeń, zgodnie z którą należy żądać jak najniższych uprawnień, ponieważ można skonfigurować manifest do żądania tylko tych określonych uprawnień, których aplikacja wymaga do działania. *Mage.exe* nie obsługuje bezpośrednio dodawania niestandardowej sekcji zaufania. Można to zrobić za pomocą edytora tekstów, analizatora XML lub graficznego narzędzia *MageUI.exe*. Aby uzyskać więcej informacji o sposobie używania *MageUI.exe* do dodawania niestandardowych sekcji zaufania, zobacz [MageUI.exe (Manifest Generation i graficzny klient Editing Tool)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

Visual Studio 2017 zawiera wersji 4.6.1 *Mage.exe*. Manifesty utworzone za pomocą tej wersji *Mage.exe* platformą docelową jest program .NET Framework 4. Pod kątem starsze wersje programu .NET Framework, należy użyć wcześniejszej wersji *Mage.exe*.

Gdy dodawanie lub usuwanie zestawów z istniejącego manifestu lub ponownego podpisywania istniejącego manifestu *Mage.exe* nie aktualizuje manifestu do obiektu docelowego .NET Framework 4.

W poniższej tabeli przedstawiono te funkcje i ograniczenia:

|Wersja manifestu|Operacja|Mage w wersji 2.0|Mage w wersji 4.0|
|----------------------|---------------|---------------|---------------|
|Manifest dla aplikacji, których platforma docelowa to wersja 2.0 lub 3.x programu .NET Framework|Otwarcie|OK|OK|
||Zamknięcie|OK|OK|
||Zapisanie|OK|OK|
||Ponowne podpisane|OK|OK|
||New|OK|Nieobsługiwane|
||Aktualizacja (zobacz poniżej)|OK|OK|
|Manifest dla aplikacji, których platforma docelowa to wersja 4 programu .NET Framework|Otwarcie|OK|OK|
||Zamknięcie|OK|OK|
||Zapisanie|OK|OK|
||Ponowne podpisane|OK|OK|
||New|Nieobsługiwane|OK|
||Aktualizacja (zobacz poniżej)|Nieobsługiwane|OK|

|Wersja manifestu|Szczegóły operacji aktualizacji|Mage w wersji 2.0|Mage w wersji 4.0|
|----------------------|------------------------------|---------------|---------------|
|Manifest dla aplikacji, których platforma docelowa to wersja 2.0 lub 3.x programu .NET Framework|Modyfikacja zestawu|OK|OK|
||Dodanie zestawu|OK|OK|
||Usunięcie zestawu|OK|OK|
|Manifest dla aplikacji, których platforma docelowa to wersja 4 programu .NET Framework|Modyfikacja zestawu|Nieobsługiwane|OK|
||Dodanie zestawu|Nieobsługiwane|OK|
||Usunięcie zestawu|Nieobsługiwane|OK|

 Mage.exe tworzy nowe manifesty, których platformą docelową [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Aplikacje ClickOnce, których platformą docelową [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] mogą być uruchamiane zarówno [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] i w pełnej wersji programu .NET Framework 4. Jeśli aplikacja jest przeznaczony dla pełnej wersji programu .NET Framework 4 i nie można uruchomić na [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)], usunąć klienta `<framework>` elementu za pomocą edytora tekstów i ponownie podpisać manifest.

Poniżej przedstawiono przykładowe `<framework>` element, który jest przeznaczony dla [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]:

```xml
<framework targetVersion="4.0" profile="client" supportedRuntime="4.0.20506" />
```

## <a name="examples"></a>Przykłady

W poniższym przykładzie otwierany interfejs użytkownika programu Mage (*MageUI.exe*).

```console
mage
```

W poniższym przykładzie są tworzone domyślne manifesty wdrożenia i aplikacji. Wszystkie te pliki są tworzone w bieżącym katalogu roboczym i są nazwane odpowiednio deploy.application i application.exe.manifest.

```console
mage -New Deployment
mage -New Application
```

Poniższy przykład tworzy manifest aplikacji wypełniony wszystkimi zestawami i plikami zasobów z bieżącego katalogu.

```console
mage -New Application -FromDirectory . -Version 1.0.0.0
```

W poniższym przykładzie jest kontynuowany poprzedni przykład i jest określana nazwa wdrożenia oraz docelowy mikroprocesor. Określany jest także adres URL, pod którym technologia ClickOnce będzie sprawdzać dostępność aktualizacji.

```console
mage -New Application -FromDirectory . -Name "Hello, World! Application" -Version 1.0.0.0 -Processor "x86" -ProviderUrl http://internalserver/HelloWorld/
```

W poniższym przykładzie pokazano sposób tworzenia pary manifestów dla wdrożenia aplikacji programu WPF, która będzie obsługiwana w programie Internet Explorer.

```console
mage -New Application -FromDirectory . -Version 1.0.0.0 -WPFBrowserApp true
mage -New Deployment -AppManifest 1.0.0.0\application.manifest -WPFBrowserApp true
```

Poniższy przykład tworzy manifest aplikacji wypełniony wszystkimi zestawami i plikami zasobów z bieżącego katalogu i loguje się.

```console
mage -New Application -FromDirectory . -Version 1.0.0.0 -KeyContainer keypair.snk -CryptoProvider "Microsoft Enhanced Cryptographic Provider v1.0"
```

W poniższym przykładzie manifest wdrożenia jest aktualizowany informacjami z manifestu aplikacji, a także jest ustawiana podstawa kodu dla lokalizacji manifestu aplikacji.

```console
mage -Update HelloWorld.deploy -AppManifest 1.0.0.0\application.manifest -AppCodeBase http://internalserver/HelloWorld.deploy
```

W poniższym przykładzie manifest wdrożenia jest edytowany w celu wymuszenia aktualizacji zainstalowanej wersji użytkownika.

```console
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -MinVersion 1.1.0.0
```

W poniższym przykładzie manifest wdrożenia otrzymuje instrukcję pobrania manifestu aplikacji z innego katalogu.

```console
mage -Update HelloWorld.deploy -AppCodeBase http://anotherserver/HelloWorld/1.1.0.0/
```

W poniższym przykładzie istniejący manifest wdrożenia jest podpisywany przy użyciu certyfikatu cyfrowego w bieżącym katalogu roboczym.

```console
mage -Sign deploy.application -CertFile cert.pfx -Password <passwd>
```

Poniższy przykład podpisuje istniejący manifest wdrożenia za pomocą certyfikatu cyfrowego i klucza prywatnego w bieżącym katalogu roboczym.

```console
mage -Sign deploy.application -CertFile cert.pfx -KeyContainer keyfile.snk -CryptoProvider "Microsoft Enhanced Cryptographic Provider v1.0"
```

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
- [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Przegląd wdrażania zaufanych aplikacji](/visualstudio/deployment/trusted-application-deployment-overview)
- [MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
- [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
