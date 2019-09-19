---
title: Mage.exe (Narzędzie generowania manifestu i edytowania)
ms.date: 12/06/2018
helpviewer_keywords:
- Manifest Generation and Editing tool
- Mage.exe
ms.assetid: 77dfe576-2962-407e-af13-82255df725a1
ms.openlocfilehash: 13a22cd15da3d4cf7eb26359c692389d27d377c0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044507"
---
# <a name="mageexe-manifest-generation-and-editing-tool"></a>Mage.exe (Narzędzie generowania manifestu i edytowania)

Narzędzie tworzenia i edycji manifestów (*Mage. exe*) to narzędzie wiersza polecenia, które obsługuje tworzenie i edytowanie manifestów aplikacji i wdrażania. Narzędzie wiersza polecenia *Mage. exe* może być uruchamiane zarówno ze skryptów wsadowych, jak i innych aplikacji opartych na systemie Windows, w tym aplikacji ASP.NET.

Możesz również użyć *MageUI. exe*, aplikacji graficznej zamiast programu *Mage. exe*. Aby uzyskać więcej informacji, zobacz [MageUI. exe (narzędzie tworzenia i edycji manifestów, klient graficzny)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio. Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).

Dwie wersje programu *Mage. exe* i *MageUI. exe* są dołączone do programu Visual Studio. Aby wyświetlić informacje o wersji, uruchom program *MageUI. exe*, wybierz pozycję **Pomoc**, a następnie wybierz pozycję **About (informacje**). W tej dokumentacji opisano wersję 4.0. x. x programu *Mage. exe* i *MageUI. exe*.

## <a name="syntax"></a>Składnia

```console
Mage [commands] [commandOptions]
```

## <a name="parameters"></a>Parametry

W poniższej tabeli przedstawiono polecenia obsługiwane przez program *Mage. exe*. Aby uzyskać więcej informacji na temat opcji obsługiwanych przez te polecenia, zobacz [nowe i aktualizowanie opcji poleceń](#new-and-update-command-options) i [Podpisz opcje polecenia](#sign-command-options).

|Polecenie|Opis|
|-------------|-----------------|
|**-DW, ClearApplicationCache**|Czyści pamięć podręczną pobranych aplikacji ze wszystkich aplikacji działających tylko w trybie online.|
|**-n,-New** *Typ [newOptions]*|Tworzy nowy plik danego typu. Prawidłowymi typami są:<br /><br /> -   `Deployment`: Tworzy nowy manifest wdrożenia.<br />-   `Application`: Tworzy nowy manifest aplikacji.<br /><br /> Jeśli nie określono żadnych dodatkowych parametrów dla tego polecenia, zostanie utworzony plik odpowiedniego typu, z odpowiednimi domyślnymi tagami oraz wartościami atrybutów.<br /><br /> Użyj opcji **-ToFile** (Zobacz w poniższej tabeli), aby określić nazwę pliku i ścieżkę nowego pliku.<br /><br /> Użyj opcji **-FromDirectory** (Zobacz w poniższej tabeli), aby utworzyć manifest aplikacji ze wszystkimi zestawami aplikacji dodawanymi do \<sekcji zależności > w manifeście.|
|**-u,-Update** *[FilePath] [updateOptions]*|Wprowadza co najmniej jedną zmianę w pliku manifestu. Nie trzeba określać typu edytowanego pliku. Program Mage.exe zbada plik za pomocą zestawu algorytmów heurystycznych i ustali, czy jest to manifest wdrożenia, czy aplikacji.<br /><br /> Jeśli plik został już podpisany za pomocą certyfikatu, polecenie **Aktualizuj** spowoduje usunięcie bloku podpisu klucza. Dzieje się tak dlatego, że podpis klucza zawiera skrót pliku i modyfikacja pliku spowoduje, że skrót będzie nieprawidłowy.<br /><br /> Użyj opcji **-ToFile** (Zobacz w poniższej tabeli), aby określić nową nazwę pliku i ścieżkę zamiast zastępowania istniejącego pliku.|
|**-s,-Sign**`[signOptions]`|Używa pary kluczy lub certyfikatu X509 w celu podpisania pliku. Podpisy są wstawiane jako elementy XML wewnątrz plików.<br /><br /> Musisz mieć połączenie z Internetem podczas podpisywania manifestu, który określa wartość **-TimestampUri** .|
|**-ver,-verify** *[manifest-filename]*|Sprawdza, czy manifest jest poprawnie podpisany. Nie można łączyć z innymi poleceniami. <br/><br/>**Dostępne w .NET Framework 4,7 i nowszych wersjach.**|
|**-h,-?,-pomoc** *[verbose]*|Opisuje wszystkie z dostępnych poleceń i ich opcji. Określ `verbose` , aby uzyskać szczegółową pomoc.|

## <a name="new-and-update-command-options"></a>Opcje poleceń New i Update

W poniższej tabeli przedstawiono opcje obsługiwane przez `-New` polecenia i: `-Update`

|Opcje|Wartość domyślna|Dotyczy:|Opis|
|-------------|-------------------|----------------|-----------------|
|**-a,-Algorithm**|sha1RSA|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Określa algorytm, za pomocą którego zostaną wygenerowane skróty zależności. Wartością musi być „sha256RSA” lub „sha1RSA”.<br /><br /> Należy używać z opcją „-Update”. Ta opcja jest ignorowana, gdy używana jest opcja „-Sign”.|
|**-APPC,-AppCodeBase**`manifestReference`||Manifesty wdrożenia.|Wstawia odwołanie do adresu URL lub ścieżki pliku do pliku manifestu aplikacji. Ta wartość musi być pełną ścieżką do manifestu aplikacji.|
|**-APPM,-Appmanifest**`manifestPath`||Manifesty wdrożenia.|Wstawia do manifestu wdrożenia odwołanie do manifestu wdrażanej aplikacji.<br /><br /> Plik wskazywany przez `manifestPath` musi istnieć lub program *Mage. exe* wystawia błąd. Jeśli plik, do którego `manifestPath` istnieje odwołanie, nie jest manifestem aplikacji, program *Mage. exe* wystawia błąd.|
|**-CF,-CERTFILE**`filePath`||Wszystkie typy plików.|Określa lokalizację certyfikatu cyfrowego x509 do podpisywania pliku manifestu lub licencji. Tej opcji można użyć w połączeniu z opcją **-Password** , jeśli certyfikat wymaga hasła dla plików wymiany informacji osobistych (pfx). Począwszy od .NET Framework 4,7, jeśli plik nie zawiera klucza prywatnego, wymagana jest kombinacja opcji **-obiekt CryptoProvider** i **-Key Container** .<br/><br/>Począwszy od .NET Framework 4.6.2, program *Mage. exe* oznakuje manifesty przy użyciu CNG oraz certyfikatów CAPI.|
|**-ch,-CertHash**`hashSignature`||Wszystkie typy plików.|Skrót certyfikatu cyfrowego przechowywanego w osobistym magazynie certyfikatów na komputerze klienta. Odpowiada on ciągowi odcisku palca certyfikatu cyfrowego wyświetlanego w konsoli certyfikatów systemu Windows.<br /><br /> `hashSignature`może być wielką lub małą literą i może być dostarczony jako jeden ciąg lub z każdym oktetem odcisku palca oddzielone spacjami i cały odcisk palca ujęty w cudzysłów.|
|**-CSP,-obiekt CryptoProvider**`provider-name`||Wszystkie typy plików.|Określa nazwę dostawcy usług kryptograficznych (CSP), który zawiera kontener klucza prywatnego. Ta opcja wymaga opcji **-containerer** .<br/><br/>Ta opcja jest dostępna od .NET Framework 4,7.|
|**-fd, -FromDirectory** `directoryPath`||Manifesty aplikacji.|Wypełnia manifest aplikacji opisami wszystkich zestawów i plików znalezionych w systemie, `directoryPath`w tym wszystkich podkatalogów, gdzie `directoryPath` jest katalogiem zawierającym aplikację, którą chcesz wdrożyć. Dla każdego pliku w katalogu Program *Mage. exe* decyduje o tym, czy plik jest zestawem, czy plikiem statycznym. Jeśli jest to zestaw, dodaje `<dependency>` tag i `installFrom` atrybut do aplikacji z nazwą zestawu, bazą kodu i wersją. Jeśli jest to plik statyczny, dodaje `<file>` tag. Program *Mage. exe* również użyje prostego zestawu heurystycznych do wykrycia głównego pliku wykonywalnego dla aplikacji i oznaczy go jako punkt wejścia aplikacji ClickOnce w manifeście.<br /><br /> Program *Mage. exe* nigdy nie automatycznie oznaczy pliku jako pliku "Data". Tę czynność należy wykonać ręcznie. Aby uzyskać więcej informacji, zobacz [jak: Dołącz plik danych do aplikacji](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application)ClickOnce.<br /><br /> Program *Mage. exe* generuje również skrót dla każdego pliku na podstawie jego rozmiaru. Technologia ClickOnce używa tych skrótów, aby zagwarantować, że nikt nie ingerował w pliki wdrożenia od czasu utworzenia manifestu. Jeśli którykolwiek z plików we wdrożeniu ulegnie zmianie, można uruchomić program *Mage. exe* z poleceniem **-Update** i opcją **-FromDirectory** . spowoduje to zaktualizowanie skrótów i wersji zestawu wszystkich plików, do których istnieją odwołania.<br /><br /> **-FromDirectory** będzie zawierać wszystkie pliki we wszystkich podkatalogach, które `directoryPath`znajdują się w.<br /><br /> Jeśli używasz **-FromDirectory** z poleceniem **-Update** , program *Mage. exe* usunie wszystkie pliki w manifeście aplikacji, które nie istnieją już w katalogu.|
|**-If,-IconFile**  `filePath`||Manifesty aplikacji.|Określa pełną ścieżkę do pliku ikony ICO. Ta ikona pojawia się obok nazwy aplikacji w menu Start oraz we wpisie w aplecie Dodaj lub usuń programy. Jeśli nie zostanie dostarczona ikona, będzie używana ikona domyślna.|
|**-IP,-IncludeProviderURL**  `url`|true|Manifesty wdrożenia.|Wskazuje, czy manifest wdrożenia zawiera wartość lokalizacji aktualizacji ustawioną przez **-providerUrl**.|
|**-i,-zainstaluj**`willInstall`|true|Manifesty wdrożenia.|Wskazuje, czy aplikacja ClickOnce ma zostać zainstalowana na komputerze lokalnym, czy ma być uruchamiana z sieci Web. Zainstalowanie aplikacji zapewnia, że aplikacja jest dostępna w menu **Start** systemu Windows. Prawidłowymi wartościami są „true” lub „t” oraz „false” lub „f”.<br /><br /> Jeśli zostanie określona opcja **-MinVersion** , a użytkownik ma zainstalowaną wersję niższą niż **-MinVersion** , wymusi to zainstalowanie aplikacji niezależnie od wartości przekazywanej do **instalacji**.<br /><br /> Tej opcji nie można używać z opcją **-BrowserHosted** . Próba określenia obu tych opcji dla jednego manifestu spowoduje błąd.|
|**-KC,-containerer**`name`||Wszystkie typy plików.|Określa kontener klucza, który zawiera nazwę klucza prywatnego. Ta opcja wymaga opcji **obiekt CryptoProvider** .<br/><br/>Ta opcja jest dostępna od .NET Framework 4,7.|
|**-MV,-MinVersion**  `[version]`|Wersja wymieniona w manifeście wdrażania ClickOnce określona przez flagę **-Version** .|Manifesty wdrożenia.|Minimalna wersja aplikacji, jaką może uruchomić użytkownik. Ta flaga powoduje, że nazwana wersja aplikacji staje się wymaganą aktualizacją. Jeśli zostanie wydana wersja produktu z aktualizacją dotyczącą ważnej zmiany lub krytycznej wady zabezpieczeń, można użyć tej flagi, aby określić, że ta aktualizacja musi zostać zainstalowana, a użytkownik nie może kontynuować używania wcześniejszych wersji.<br /><br /> `version`ma tę samą semantykę jako argument flagi **-Version** .|
|**-n,-Name**`nameString`|Deploy|Wszystkie typy plików.|Nazwa, która jest używana do identyfikacji aplikacji. Technologia ClickOnce będzie używać tej nazwy do identyfikowania aplikacji w menu **Start** (Jeśli aplikacja jest skonfigurowana do samodzielnego instalowania) i w oknach dialogowych podniesienia uprawnień. **Uwaga:**  Jeśli aktualizujesz istniejący manifest i nie określisz nazwy wydawcy z tą opcją, program *Mage. exe* zaktualizuje manifest o nazwie organizacji zdefiniowanej na komputerze. Aby użyć innej nazwy, należy użyć tej opcji i określić odpowiednią nazwę wydawcy.|
|**-PWD,-Password**`passwd`||Wszystkie typy plików.|Hasło używane do podpisywania manifestu za pomocą certyfikatu cyfrowego. Musi być używany w połączeniu z opcją **-CERTFILE** .|
|**-p, procesor**`processorValue`|Msil|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Architektura mikroprocesora, na której będzie uruchomiona dystrybucja. Ta wartość jest wymagana, jeśli jest przygotowywanych kilka instalacji, których zestawy są wstępnie kompilowane dla określonego mikroprocesora. Prawidłowe wartości to `msil`, `x86`, `ia64`, i `amd64`. `msil`jest językiem pośrednim firmy Microsoft, co oznacza, że wszystkie zestawy są niezależne od platformy, a środowisko uruchomieniowe języka wspólnego (CLR) rozpocznie się po raz pierwszy podczas pierwszego uruchomienia aplikacji.|
|**-PU,** **-ProviderUrl**`url`||Manifesty wdrożenia.|Określa adres URL, pod którym technologia ClickOnce będzie szukać aktualizacji aplikacji.|
|**-pub,-Publisher**`publisherName`||Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Dodaje nazwę wydawcy do opisu elementu manifestu wdrożenia lub aplikacji. Gdy jest używany w manifeście **aplikacji, należy** również określić wartość "true" lub "t". w przeciwnym razie ten parametr spowoduje wystąpienie błędu.|
|**-s,-SupportURL**  `url`||Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Określa łącze, które pojawia się w aplecie Dodaj lub usuń programy dla aplikacji ClickOnce.|
|**-TI,-TimestampUri**`uri`||Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Adres URL usługi cyfrowego oznaczania znacznikami czasu. Oznaczenie manifestu znacznikiem czasu zapobiega konieczności ponownego podpisania manifestu, jeśli certyfikat cyfrowy wygaśnie przed wdrożeniem następnej wersji aplikacji. Aby uzyskać więcej informacji, zobacz [Członkowie programu certyfikatów głównych systemu Windows](https://go.microsoft.com/fwlink/?LinkId=159000).|
|**-t,-ToFile**`filePath`|Nowy<br />-Deployment: Deploy. Application<br />-Aplikacja: Application. exe. manifest<br />Aktualizacji<br />-Plik wejściowy.|Wszystkie typy plików.|Określa ścieżkę wyjściową utworzonego lub zmodyfikowanego pliku.<br /><br /> Jeśli polecenie **-ToFile** nie zostanie podane podczas korzystania z polecenia **-New**, dane wyjściowe są zapisywane w bieżącym katalogu roboczym. Jeśli nie podano **ToFile-** **Update**, program *Mage. exe* zapisze plik z powrotem do pliku wejściowego.|
|**-TR,-TrustLevel**`level`|Wartość określana na podstawie strefy, w której znajduje się adres URL aplikacji.|Manifesty aplikacji.|Poziom zaufania, który zostanie przyznany aplikacji na komputerach klientów. Dostępne wartości to Internet, Intranet i FullTrust.|
|**-UM,-UseManifestForTrust**`willUseForTrust`|False|Manifesty aplikacji.|Określa, czy podpis cyfrowy manifestu aplikacji będzie używany do podejmowania decyzji dotyczących zaufania, gdy aplikacja zostanie uruchomiona na komputerze klienckim. Określenie wartości „true” lub „t” wskazuje, że manifest aplikacji zostanie użyty do podejmowania decyzji dotyczących zaufania. Określenie wartości „false” lub „f” wskazuje, że zostanie użyty podpis manifestu wdrożenia.|
|**-v,-Version**`versionNumber`|1.0.0.0|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Wersja wdrożenia. Argument musi być prawidłowym ciągiem wersji o formacie "*n. n. n. n*", gdzie "*n*" jest niepodpisanym 32-bitową liczbą całkowitą.|
|**-WPF,-WPFBrowserApp**  `isWPFApp`|false|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Tej flagi należy używać tyko wtedy, gdy aplikacja jest aplikacją programu Windows Presentation Foundation (WPF), która będzie obsługiwana wewnątrz programu Internet Explorer i nie jest autonomicznym plikiem wykonywalnym. Prawidłowymi wartościami są „true” lub „t” oraz „false” lub „f”.<br /><br /> W przypadku manifestów aplikacji program wstawia `hostInBrowser` atrybut `entryPoint` w obszarze elementu manifestu aplikacji.<br /><br /> W przypadku manifestów wdrożenia ustawia `install` atrybut `deployment` dla elementu na false i zapisuje manifest wdrożenia z rozszerzeniem. XBAP. Określenie tego argumentu wraz z argumentem **-Install** powoduje wystąpienie błędu, ponieważ aplikacja hostowana w przeglądarce nie może być zainstalowaną aplikacją w trybie offline.|

## <a name="sign-command-options"></a>Opcje polecenia podpisywania

W poniższej tabeli przedstawiono opcje obsługiwane przez `-Sign` polecenie, które mają zastosowanie do wszystkich typów plików.

|Opcje|Opis|
|-------------|-----------------|
|**-CF,-CERTFILE**`filePath`|Określa lokalizację certyfikatu cyfrowego używanego do podpisania manifestu. Tej opcji można użyć w połączeniu z opcją **-Password** , jeśli certyfikat wymaga hasła dla plików wymiany informacji osobistych (pfx). Począwszy od .NET Framework 4,7, jeśli plik nie zawiera klucza prywatnego, wymagana jest kombinacja opcji **-obiekt CryptoProvider** i **-Key Container** .<br/><br/>Począwszy od .NET Framework 4.6.2, program *Mage. exe* oznakuje manifesty przy użyciu CNG oraz certyfikatów CAPI.|
|**-ch,-CertHash**`hashSignature`|Skrót certyfikatu cyfrowego przechowywanego w osobistym magazynie certyfikatów na komputerze klienta. Odpowiada właściwości odcisku palca certyfikatu cyfrowego wyświetlanego na konsoli certyfikatów systemu Windows.<br /><br /> `hashSignature`może być pisane wielkimi lub małymi literami i może być dostarczone jako jeden ciąg lub z każdym oktetem odcisku palca oddzielone spacjami i cały odcisk palca ujęty w cudzysłów.|
**-CSP,-obiekt CryptoProvider**`provider-name`|Określa nazwę dostawcy usług kryptograficznych (CSP), który zawiera kontener klucza prywatnego. Ta opcja wymaga opcji **-containerer** .<br/><br/>Ta opcja jest dostępna od .NET Framework 4,7.|
|**-KC,-containerer**`name`|Określa kontener klucza, który zawiera nazwę klucza prywatnego. Ta opcja wymaga opcji **obiekt CryptoProvider** .<br/><br/>Ta opcja jest dostępna od .NET Framework 4,7.|
|**-PWD,-Password**`passwd`|Hasło używane do podpisywania manifestu za pomocą certyfikatu cyfrowego. Musi być używany w połączeniu z opcją **-CERTFILE** .|
|**-t,-ToFile**`filePath`|Określa ścieżkę wyjściową utworzonego lub zmodyfikowanego pliku.|

## <a name="remarks"></a>Uwagi

W przypadku wszystkich argumentów programu *Mage. exe* nie jest rozróżniana wielkość liter. Polecenia i opcje mogą być poprzedzone kreską (-) lub ukośnikiem (/).

Wszystkie argumenty używane z poleceniem **-Sign** można również używać w dowolnym momencie z poleceniami **-New** lub **-Update** . Poniższe polecenia są równoważne.

```console
mage -Sign c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
```

> [!NOTE]
> Od .NET Framework wersji 4.6.2 są również obsługiwane certyfikaty CNG.

 Podpisywanie jest ostatnim zadaniem, które należy wykonać, ponieważ podpisany dokument używa skrótu pliku w celu weryfikacji, czy podpis jest prawidłowy dla dokumentu. W przypadku wprowadzenia jakiejkolwiek zmiany w podpisanym pliku należy podpisać go ponownie. Jeśli podpiszesz wcześniej podpisany dokument, program *Mage. exe* zamieni stary podpis z nowym.

 W przypadku użycia opcji **-Appmanifest** w celu wypełnienia manifestu wdrożenia program *Mage. exe* przyjmie, że manifest aplikacji będzie znajdować się w tym samym katalogu co manifest wdrożenia w podkatalogu o nazwie po bieżącym wdrożeniu. i skonfiguruje odpowiednio manifest wdrożenia. Jeśli manifest aplikacji będzie znajdować się w innym miejscu, użyj opcji **-AppCodeBase** , aby ustawić lokalizację alternatywną.

 Manifesty wdrożenia i aplikacji muszą zostać podpisane przed wdrożeniem aplikacji. Aby uzyskać wskazówki dotyczące podpisywania manifestów, zobacz [Omówienie wdrażania zaufanych aplikacji](/visualstudio/deployment/trusted-application-deployment-overview).

 Opcja **-TrustLevel** manifestów aplikacji zawiera opis zestawu uprawnień wymaganego przez aplikację do uruchomienia na komputerze klienckim. Domyślnie aplikacje są przypisywane na poziomie zaufania na podstawie *strefy* , w której znajduje się adres URL. Aplikacje wdrożone przez sieć firmową są zazwyczaj umieszczane w strefie Intranet, podczas gdy te wdrożone przez Internet umieszczane są w strefie Internet. Obie strefy zabezpieczeń nakładają na aplikację ograniczenia w zakresie dostępu do lokalnych zasobów, przy czym strefa Intranet ma nieco łagodniejsze ograniczenia niż strefa Internet. Strefa FullTrust udziela aplikacji pełnego dostępu do lokalnych zasobów komputera. Jeśli używasz opcji **-TrustLevel** , aby umieścić aplikację w tej strefie, składnik Menedżera zaufania środowiska CLR wyświetli monit użytkownika o decyzję, czy chce udzielić wyższego poziomu zaufania. Jeśli aplikacja jest wdrażana przez sieć firmową, można użyć narzędzia Wdrażanie zaufanych aplikacji, aby podnieść poziom zaufania aplikacji bez monitowania użytkownika.

 Manifesty aplikacji obsługują także niestandardowe sekcje zaufania. Pomaga to aplikacji przestrzegać reguły zabezpieczeń, zgodnie z którą należy żądać jak najniższych uprawnień, ponieważ można skonfigurować manifest do żądania tylko tych określonych uprawnień, których aplikacja wymaga do działania. Program *Mage. exe* nie obsługuje bezpośrednio dodawania niestandardowej sekcji zaufania. Można go dodać przy użyciu edytora tekstu, parsera XML lub narzędzia graficznego *MageUI. exe*. Aby uzyskać więcej informacji o sposobach dodawania niestandardowych sekcji zaufania przy użyciu programu *MageUI. exe* , zobacz [MageUI. exe (narzędzie tworzenia i edycji manifestów, klient graficzny)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

Program Visual Studio 2017 zawiera wersję 4.6.1 programu *Mage. exe*. Manifesty utworzone za pomocą tej wersji programu *Mage. exe* Target .NET Framework 4. Aby określić starsze wersje .NET Framework, użyj starszej wersji programu *Mage. exe*.

Po dodaniu lub usunięciu zestawów z istniejącego manifestu lub ponownym podpisaniu istniejącego manifestu program *Mage. exe* nie aktualizuje manifestu do wartości docelowej .NET Framework 4.

W poniższych tabelach przedstawiono następujące funkcje i ograniczenia:

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

 Program Mage. exe tworzy nowe manifesty, których [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]celem jest. Aplikacje ClickOnce przeznaczone dla programu [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] mogą działać [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] zarówno w pełnej wersji .NET Framework 4. Jeśli aplikacja jest przeznaczona dla pełnej wersji .NET Framework 4 i nie można jej [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]uruchomić w programie, Usuń element Client `<framework>` przy użyciu edytora tekstów i zarejestruj go ponownie.

Poniżej znajduje się przykładowy `<framework>` element, który jest przeznaczony dla: [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]

```xml
<framework targetVersion="4.0" profile="client" supportedRuntime="4.0.20506" />
```

## <a name="examples"></a>Przykłady

Poniższy przykład otwiera interfejs użytkownika dla programu Mage (*MageUI. exe*).

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

Poniższy przykład tworzy manifest aplikacji wypełniony wszystkimi zestawami i plikami zasobów z bieżącego katalogu i znaków.

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

Poniższy przykład podpisuje istniejący manifest wdrożenia przy użyciu certyfikatu cyfrowego i klucza prywatnego w bieżącym katalogu roboczym.

```console
mage -Sign deploy.application -CertFile cert.pfx -KeyContainer keyfile.snk -CryptoProvider "Microsoft Enhanced Cryptographic Provider v1.0"
```

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
- [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Przegląd wdrażania zaufanych aplikacji](/visualstudio/deployment/trusted-application-deployment-overview)
- [MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
