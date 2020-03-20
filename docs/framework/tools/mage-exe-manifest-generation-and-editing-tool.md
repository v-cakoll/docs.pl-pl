---
title: Mage.exe (Narzędzie generowania manifestu i edytowania)
ms.date: 12/06/2018
helpviewer_keywords:
- Manifest Generation and Editing tool
- Mage.exe
ms.assetid: 77dfe576-2962-407e-af13-82255df725a1
ms.openlocfilehash: b04fda81ae51462d9e686585de1477b4c9af4b26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180390"
---
# <a name="mageexe-manifest-generation-and-editing-tool"></a>Mage.exe (Narzędzie generowania manifestu i edytowania)

Narzędzie do generowania i edytowania manifestów *(Mage.exe)* to narzędzie wiersza polecenia, które obsługuje tworzenie i edytowanie manifestów aplikacji i wdrażania. Jako narzędzie wiersza polecenia *mage.exe* można uruchamiać zarówno ze skryptów wsadowych, jak i innych aplikacji opartych na systemie Windows, w tym ASP.NET aplikacji.

Możesz również użyć *MageUI.exe*, aplikacji graficznej, zamiast *Mage.exe*. Aby uzyskać więcej informacji, zobacz [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).

Dwie wersje *mage.exe* i *MageUI.exe* są dołączone do programu Visual Studio. Aby wyświetlić informacje o wersji, uruchom *plik MageUI.exe*, wybierz **pozycję Pomoc**i wybierz pozycję **Informacje**. Niniejsza dokumentacja opisuje wersję 4.0.x.x *mage.exe* i *MageUI.exe*.

## <a name="syntax"></a>Składnia

```console
Mage [commands] [commandOptions]
```

## <a name="parameters"></a>Parametry

W poniższej tabeli przedstawiono polecenia obsługiwane przez *mage.exe*. Aby uzyskać więcej informacji na temat opcji obsługiwanych przez te polecenia, zobacz [Nowe i aktualizuj opcje polecenia](#new-and-update-command-options) oraz Opcje polecenia [Podpisz](#sign-command-options).

|Polecenie|Opis|
|-------------|-----------------|
|**-cc, ClearApplicationCache**|Czyści pamięć podręczną pobranych aplikacji ze wszystkich aplikacji działających tylko w trybie online.|
|**-n, -Nowy** *plikType [newOptions]*|Tworzy nowy plik danego typu. Prawidłowymi typami są:<br /><br /> -   `Deployment`: Tworzy nowy manifest wdrożenia.<br />-   `Application`: Tworzy nowy manifest aplikacji.<br /><br /> Jeśli nie określono żadnych dodatkowych parametrów dla tego polecenia, zostanie utworzony plik odpowiedniego typu, z odpowiednimi domyślnymi tagami oraz wartościami atrybutów.<br /><br /> Użyj opcji **-ToFile** (zobacz w poniższej tabeli), aby określić nazwę pliku i ścieżkę nowego pliku.<br /><br /> Użyj **opcji -FromDirectory** (zobacz w poniższej tabeli), aby utworzyć manifest aplikacji ze \<wszystkimi zestawami dla aplikacji dodanej do sekcji zależności> manifestu.|
|**-u, -Update** *[filePath] [updateOptions]*|Wprowadza co najmniej jedną zmianę w pliku manifestu. Nie trzeba określać typu edytowanego pliku. Program Mage.exe zbada plik za pomocą zestawu algorytmów heurystycznych i ustali, czy jest to manifest wdrożenia, czy aplikacji.<br /><br /> Jeśli plik został już podpisany z certyfikatem, **-Update** usunie blok podpisu klucza. Dzieje się tak dlatego, że podpis klucza zawiera skrót pliku i modyfikacja pliku spowoduje, że skrót będzie nieprawidłowy.<br /><br /> Użyj opcji **-ToFile** (zobacz w poniższej tabeli), aby określić nową nazwę pliku i ścieżkę zamiast zastępowania istniejącego pliku.|
|**-s, -Znak**`[signOptions]`|Używa pary kluczy lub certyfikatu X509 w celu podpisania pliku. Podpisy są wstawiane jako elementy XML wewnątrz plików.<br /><br /> Podczas podpisywania manifestu określającego wartość **-TimestampUri** musi być nawiązywać połączenie z Internetem.|
|**-ver, -Verify** *[nazwa pliku manifestu]*|Sprawdza, czy manifest jest podpisany poprawnie. Nie można łączyć z innymi poleceniami. <br/><br/>**Dostępne w wersji .NET Framework 4.7 i nowszych.**|
|**-h, -?, -Help** *[pełne]*|Opisuje wszystkie z dostępnych poleceń i ich opcji. Określ, `verbose` aby uzyskać szczegółową pomoc.|

## <a name="new-and-update-command-options"></a>Opcje polecenia Nowe i aktualizuj

W poniższej tabeli przedstawiono `-New` `-Update` opcje obsługiwane przez polecenia i:

|Opcje|Wartość domyślna|Dotyczy:|Opis|
|-------------|-------------------|----------------|-----------------|
|**-a, -Algorytm**|sha1RSA|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Określa algorytm, za pomocą którego zostaną wygenerowane skróty zależności. Wartością musi być „sha256RSA” lub „sha1RSA”.<br /><br /> Należy używać z opcją „-Update”. Ta opcja jest ignorowana, gdy używana jest opcja „-Sign”.|
|**-appc, -AppCodeBase**`manifestReference`||Manifesty wdrożenia.|Wstawia odwołanie do adresu URL lub ścieżki pliku do pliku manifestu aplikacji. Ta wartość musi być pełną ścieżką do manifestu aplikacji.|
|**-appm, -AppManifest**`manifestPath`||Manifesty wdrożenia.|Wstawia do manifestu wdrożenia odwołanie do manifestu wdrażanej aplikacji.<br /><br /> Plik wskazany `manifestPath` przez musi istnieć lub *Mage.exe* wyemituje błąd. Jeśli plik, do `manifestPath` którego odwołuje się nie jest manifest aplikacji, *Mage.exe wyemituje* błąd.|
|**-cf, -CertFile**`filePath`||Wszystkie typy plików.|Określa lokalizację certyfikatu cyfrowego X509 do podpisywania manifestu lub pliku licencji. Tej opcji można używać w połączeniu z opcją **-Password,** jeśli certyfikat wymaga hasła do plików wymiany informacji osobistych (PFX). Począwszy od .NET Framework 4.7, jeśli plik nie zawiera klucza prywatnego, wymagana jest kombinacja opcji **-CryptoProvider** i **-KeyContainer.**<br/><br/>Począwszy od programu .NET Framework 4.6.2, *znaki Mage.exe* manifestuje się z certyfikatami CNG, a także certyfikatami CAPI.|
|**-ch, -CertHash**`hashSignature`||Wszystkie typy plików.|Skrót certyfikatu cyfrowego przechowywanego w osobistym magazynie certyfikatów na komputerze klienta. Odpowiada on ciągowi odcisku palca certyfikatu cyfrowego wyświetlanego w konsoli certyfikatów systemu Windows.<br /><br /> `hashSignature`mogą być wielkie lub małe i mogą być dostarczane jako pojedynczy ciąg lub z każdym oktetem odcisku palca oddzielonym spacjami i całym odciskiem palca ujętym w cudzysłów.|
|**-csp, -CryptoProvider**`provider-name`||Wszystkie typy plików.|Określa nazwę dostawcy usług kryptograficznych (CSP), który zawiera kontener klucza prywatnego. Ta opcja wymaga opcji **-KeyContainer.**<br/><br/>Ta opcja jest dostępna począwszy od programu .NET Framework 4.7.|
|**-fd, -FromDirectory**`directoryPath`||Manifesty aplikacji.|Wypełnia manifest aplikacji opisami wszystkich zestawów i plików `directoryPath`znalezionych w , w `directoryPath` tym wszystkich podkatalogach, gdzie znajduje się katalog zawierający aplikację, którą chcesz wdrożyć. Dla każdego pliku w katalogu *Mage.exe* decyduje, czy plik jest plikiem złożenia, czy plikiem statycznym. Jeśli jest to zestaw, `<dependency>` dodaje `installFrom` tag i atrybut do aplikacji o nazwie zestawu, kod podstawowy i wersja. Jeśli jest to plik statyczny, `<file>` dodaje znacznik. *Mage.exe* będzie również korzystać z prostego zestawu heurystyki do wykrywania głównego pliku wykonywalnego dla aplikacji, i oznaczy go jako clickonce aplikacji punkt wejścia w manifeście.<br /><br /> *Mage.exe* nigdy nie oznaczy automatycznie pliku jako pliku "danych". Tę czynność należy wykonać ręcznie. Aby uzyskać więcej informacji, zobacz [Jak: Dołączanie pliku danych do aplikacji ClickOnce](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application).<br /><br /> *Mage.exe* generuje również skrót dla każdego pliku na podstawie jego rozmiaru. Technologia ClickOnce używa tych skrótów, aby zagwarantować, że nikt nie ingerował w pliki wdrożenia od czasu utworzenia manifestu. Jeśli którykolwiek z plików we wdrożeniu ulegnie zmianie, można uruchomić *program Mage.exe* za pomocą polecenia **-Update** i opcji **-FromDirectory,** a także zaktualizować skróty i wersje zestawów wszystkich plików, do których istnieją odwołania.<br /><br /> **-FromDirectory** będzie zawierać wszystkie pliki we wszystkich `directoryPath`podkatalogach znalezionych w .<br /><br /> Jeśli używasz **-FromDirectory** z **poleceniem -Update,** *Mage.exe* usunie wszystkie pliki w manifeście aplikacji, które już nie istnieją w katalogu.|
|**-if, -IconFile**  `filePath`||Manifesty aplikacji.|Określa pełną ścieżkę do pliku ikony ICO. Ta ikona pojawia się obok nazwy aplikacji w menu Start oraz we wpisie w aplecie Dodaj lub usuń programy. Jeśli nie zostanie dostarczona ikona, będzie używana ikona domyślna.|
|**-ip, -IncludeProviderURL**  `url`|true|Manifesty wdrożenia.|Wskazuje, czy manifest wdrożenia zawiera wartość lokalizacji aktualizacji ustawioną przez **-ProviderURL**.|
|**-i, -Zainstaluj**`willInstall`|true|Manifesty wdrożenia.|Wskazuje, czy aplikacja ClickOnce ma zostać zainstalowana na komputerze lokalnym, czy ma być uruchamiana z sieci Web. Zainstalowanie aplikacji daje tej aplikacji obecność w menu **Start** systemu Windows. Prawidłowymi wartościami są „true” lub „t” oraz „false” lub „f”.<br /><br /> Jeśli określisz **opcję -MinVersion,** a użytkownik ma zainstalowaną wersję mniejszą niż **-MinVersion,** wymusi to zainstalowanie aplikacji, niezależnie od wartości, która zostanie przegłosowana do **-Install**.<br /><br /> Tej opcji nie można używać z opcją **-BrowserHosted.** Próba określenia obu tych opcji dla jednego manifestu spowoduje błąd.|
|**-kc, -KeyContainer**`name`||Wszystkie typy plików.|Określa kontener kluczy zawierający nazwę klucza prywatnego. Ta opcja wymaga opcji **CryptoProvider.**<br/><br/>Ta opcja jest dostępna począwszy od programu .NET Framework 4.7.|
|**-mv, -MinVersion**  `[version]`|Wersja wymieniona w manifeście wdrażania ClickOnce, jak określono w **-Version** flagi.|Manifesty wdrożenia.|Minimalna wersja aplikacji, jaką może uruchomić użytkownik. Ta flaga powoduje, że nazwana wersja aplikacji staje się wymaganą aktualizacją. Jeśli zostanie wydana wersja produktu z aktualizacją dotyczącą ważnej zmiany lub krytycznej wady zabezpieczeń, można użyć tej flagi, aby określić, że ta aktualizacja musi zostać zainstalowana, a użytkownik nie może kontynuować używania wcześniejszych wersji.<br /><br /> `version`ma taką samą semantycę jak argument do **-Version** flagi.|
|**-n, -Nazwa**`nameString`|Wdrożenie|Wszystkie typy plików.|Nazwa, która jest używana do identyfikacji aplikacji. ClickOnce użyje tej nazwy do identyfikowania aplikacji w menu **Start** (jeśli aplikacja jest skonfigurowana do instalowania się) i w oknach dialogowych Podniesienie uprawnień. **Uwaga:**  Jeśli aktualizujesz istniejący manifest i nie określisz nazwy wydawcy za pomocą tej opcji, *program Mage.exe aktualizuje* manifest nazwą organizacji zdefiniowaną na komputerze. Aby użyć innej nazwy, należy użyć tej opcji i określić odpowiednią nazwę wydawcy.|
|**-pwd, -Hasło**`passwd`||Wszystkie typy plików.|Hasło używane do podpisywania manifestu za pomocą certyfikatu cyfrowego. Musi być używany w połączeniu z opcją **-CertFile.**|
|**-p, Procesor**`processorValue`|Msil|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Architektura mikroprocesora, na której będzie uruchomiona dystrybucja. Ta wartość jest wymagana, jeśli jest przygotowywanych kilka instalacji, których zestawy są wstępnie kompilowane dla określonego mikroprocesora. Prawidłowe `msil`wartości `x86` `ia64`obejmują `amd64`, , i . `msil`jest językiem pośrednim firmy Microsoft, co oznacza, że wszystkie zestawy są niezależne od platformy, a środowisko uruchomieniowe języka wspólnego (CLR) będzie po prostu w czasie skompilować je, gdy aplikacja jest uruchamiana po raz pierwszy.|
|**-pu,** **-ProviderURL**`url`||Manifesty wdrożenia.|Określa adres URL, pod którym technologia ClickOnce będzie szukać aktualizacji aplikacji.|
|**-pub, -Wydawca**`publisherName`||Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Dodaje nazwę wydawcy do opisu elementu manifestu wdrożenia lub aplikacji. W przypadku użycia w manifeście aplikacji **-UseManifestForTrust** musi być również określona z wartością "true" lub "t"; w przeciwnym razie ten parametr spowoduje błąd.|
|**-s, -SupportURL**  `url`||Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Określa łącze, które pojawia się w aplecie Dodaj lub usuń programy dla aplikacji ClickOnce.|
|**-ti, -Sygnatura czasowa**`uri`||Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Adres URL usługi cyfrowego oznaczania znacznikami czasu. Oznaczenie manifestu znacznikiem czasu zapobiega konieczności ponownego podpisania manifestu, jeśli certyfikat cyfrowy wygaśnie przed wdrożeniem następnej wersji aplikacji. Aby uzyskać więcej informacji, zobacz [Elementy członkowskie programu certyfikatów głównych systemu Windows](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)).|
|**-t, -ToFile**`filePath`|- Nowy:<br />- Wdrożenie: deploy.application<br />- Zastosowanie: application.exe.manifest<br />- Aktualizacja:<br />- Plik wejściowy.|Wszystkie typy plików.|Określa ścieżkę wyjściową utworzonego lub zmodyfikowanego pliku.<br /><br /> Jeśli **-ToFile** nie jest dostarczany podczas korzystania **z -New**, dane wyjściowe są zapisywane w bieżącym katalogu roboczym. Jeśli **plik -ToFile** nie zostanie dostarczony podczas korzystania z **funkcji -Update**, *mage.exe zapisze* plik z powrotem do pliku wejściowego.|
|**-tr, -TrustLevel**`level`|Wartość określana na podstawie strefy, w której znajduje się adres URL aplikacji.|Manifesty aplikacji.|Poziom zaufania, który zostanie przyznany aplikacji na komputerach klientów. Dostępne wartości to Internet, Intranet i FullTrust.|
|**-um, -UseManifestForTrust**`willUseForTrust`|False|Manifesty aplikacji.|Określa, czy podpis cyfrowy manifestu aplikacji będzie używany do podejmowania decyzji dotyczących zaufania, gdy aplikacja zostanie uruchomiona na komputerze klienckim. Określenie wartości „true” lub „t” wskazuje, że manifest aplikacji zostanie użyty do podejmowania decyzji dotyczących zaufania. Określenie wartości „false” lub „f” wskazuje, że zostanie użyty podpis manifestu wdrożenia.|
|**-v, -Wersja**`versionNumber`|1.0.0.0|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Wersja wdrożenia. Argument musi być prawidłowym ciągiem wersji formatu "*N.N.N.N*", gdzie "*N*" jest niepodpisaną 32-bitową gnilicą całkowitą.|
|**-wpf, -WPFBrowserApp**  `isWPFApp`|false|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Tej flagi należy używać tyko wtedy, gdy aplikacja jest aplikacją programu Windows Presentation Foundation (WPF), która będzie obsługiwana wewnątrz programu Internet Explorer i nie jest autonomicznym plikiem wykonywalnym. Prawidłowymi wartościami są „true” lub „t” oraz „false” lub „f”.<br /><br /> W przypadku manifestów aplikacji `hostInBrowser` wstawia `entryPoint` atrybut w elemencie manifestu aplikacji.<br /><br /> W przypadku manifestów `install` wdrażania ustawia `deployment` atrybut elementu na false i zapisuje manifest wdrożenia z rozszerzeniem .xbap. Określenie tego argumentu wraz z **argumentem -Install** powoduje błąd, ponieważ aplikacja hostowana przez przeglądarkę nie może być zainstalowaną aplikacją w trybie offline.|

## <a name="sign-command-options"></a>Opcje polecenia Podpisz

W poniższej tabeli przedstawiono `-Sign` opcje obsługiwane przez polecenie, które mają zastosowanie do wszystkich typów plików.

|Opcje|Opis|
|-------------|-----------------|
|**-cf, -CertFile**`filePath`|Określa lokalizację certyfikatu cyfrowego używanego do podpisania manifestu. Tej opcji można używać w połączeniu z opcją **-Password,** jeśli certyfikat wymaga hasła do plików wymiany informacji osobistych (PFX). Począwszy od .NET Framework 4.7, jeśli plik nie zawiera klucza prywatnego, wymagana jest kombinacja opcji **-CryptoProvider** i **-KeyContainer.**<br/><br/>Począwszy od programu .NET Framework 4.6.2, *znaki Mage.exe* manifestuje się z certyfikatami CNG, a także certyfikatami CAPI.|
|**-ch, -CertHash**`hashSignature`|Skrót certyfikatu cyfrowego przechowywanego w osobistym magazynie certyfikatów na komputerze klienta. Odpowiada właściwości odcisku palca certyfikatu cyfrowego wyświetlanego na konsoli certyfikatów systemu Windows.<br /><br /> `hashSignature`mogą być wielkie lub małe i mogą być dostarczane jako pojedynczy ciąg lub z każdym oktetem odcisku palca oddzielonym spacjami i całym odciskiem palca ujętym w cudzysłów.|
**-csp, -CryptoProvider**`provider-name`|Określa nazwę dostawcy usług kryptograficznych (CSP), który zawiera kontener klucza prywatnego. Ta opcja wymaga opcji **-KeyContainer.**<br/><br/>Ta opcja jest dostępna począwszy od programu .NET Framework 4.7.|
|**-kc, -KeyContainer**`name`|Określa kontener kluczy zawierający nazwę klucza prywatnego. Ta opcja wymaga opcji **CryptoProvider.**<br/><br/>Ta opcja jest dostępna począwszy od programu .NET Framework 4.7.|
|**-pwd, -Hasło**`passwd`|Hasło używane do podpisywania manifestu za pomocą certyfikatu cyfrowego. Musi być używany w połączeniu z opcją **-CertFile.**|
|**-t, -ToFile**`filePath`|Określa ścieżkę wyjściową utworzonego lub zmodyfikowanego pliku.|

## <a name="remarks"></a>Uwagi

Wszystkie argumenty *mage.exe* są bez uwzględniania wielkości liter. Polecenia i opcje mogą być poprzedzone kreską (-) lub ukośnikiem (/).

Wszystkie argumenty używane za pomocą polecenia **-Sign** mogą być używane w dowolnym momencie z **poleceniami -New** lub **-Update.** Poniższe polecenia są równoważne.

```console
mage -Sign c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
```

> [!NOTE]
> Począwszy od programu .NET Framework w wersji 4.6.2, certyfikaty CNG są również obsługiwane.

 Podpisywanie jest ostatnim zadaniem, które należy wykonać, ponieważ podpisany dokument używa skrótu pliku w celu weryfikacji, czy podpis jest prawidłowy dla dokumentu. W przypadku wprowadzenia jakiejkolwiek zmiany w podpisanym pliku należy podpisać go ponownie. Jeśli podpiszesz dokument, który został wcześniej podpisany, *program Mage.exe* zastąpi stary podpis nowym.

 Korzystając z opcji **-AppManifest** do wypełniania manifestu wdrożenia, *mage.exe* zakłada, że manifest aplikacji będzie rezydować w tym samym katalogu co manifest wdrożenia w podkatalogu nazwany po bieżącej wersji wdrożenia i odpowiednio skonfiguruje manifest wdrożenia. Jeśli manifest aplikacji będzie rezydować w innym miejscu, użyj opcji **-AppCodeBase,** aby ustawić alternatywną lokalizację.

 Manifesty wdrożenia i aplikacji muszą zostać podpisane przed wdrożeniem aplikacji. Aby uzyskać wskazówki dotyczące podpisywania manifestów, zobacz [Omówienie wdrażania zaufanych aplikacji](/visualstudio/deployment/trusted-application-deployment-overview).

 **Opcja -TrustLevel** dla manifestów aplikacji opisuje zestaw uprawnień, który aplikacja wymaga do uruchomienia na komputerze klienckim. Domyślnie aplikacjom jest przypisywany poziom zaufania na podstawie *strefy,* w której znajduje się ich adres URL. Aplikacje wdrożone przez sieć firmową są zazwyczaj umieszczane w strefie Intranet, podczas gdy te wdrożone przez Internet umieszczane są w strefie Internet. Obie strefy zabezpieczeń nakładają na aplikację ograniczenia w zakresie dostępu do lokalnych zasobów, przy czym strefa Intranet ma nieco łagodniejsze ograniczenia niż strefa Internet. Strefa FullTrust udziela aplikacji pełnego dostępu do lokalnych zasobów komputera. Jeśli używasz **opcji -TrustLevel,** aby umieścić aplikację w tej strefie, składnik Menedżera zaufania programu CLR poprosi użytkownika o podjęcie decyzji, czy chce udzielić tego wyższego poziomu zaufania. Jeśli aplikacja jest wdrażana przez sieć firmową, można użyć narzędzia Wdrażanie zaufanych aplikacji, aby podnieść poziom zaufania aplikacji bez monitowania użytkownika.

 Manifesty aplikacji obsługują także niestandardowe sekcje zaufania. Pomaga to aplikacji przestrzegać reguły zabezpieczeń, zgodnie z którą należy żądać jak najniższych uprawnień, ponieważ można skonfigurować manifest do żądania tylko tych określonych uprawnień, których aplikacja wymaga do działania. *Mage.exe* nie obsługuje bezpośrednio dodawanie sekcji zaufania niestandardowego. Można dodać jeden za pomocą edytora tekstu, analizatora XML lub narzędzia graficznego *MageUI.exe*. Aby uzyskać więcej informacji na temat sposobu dodawania niestandardowych sekcji zaufania za pomocą *programu MageUI.exe,* zobacz [MageUI.exe (Narzędzie do generowania manifestu i edycji, Klient graficzny).](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)

Visual Studio 2017 zawiera wersję 4.6.1 *programu Mage.exe*. Manifesty utworzone przy tej wersji *mage.exe* target .NET Framework 4. Aby kierować reklamy na starsze wersje programu .NET Framework, należy użyć wcześniejszej wersji *programu Mage.exe*.

Po dodaniu lub usunięciu zestawów z istniejącego manifestu lub ponownym podpisaniu istniejącego manifestu *mage.exe* nie aktualizuje manifestu do obiektu docelowego .NET Framework 4.

W poniższych tabelach przedstawiono następujące funkcje i ograniczenia:

|Wersja manifestu|Operacja|Mage w wersji 2.0|Mage w wersji 4.0|
|----------------------|---------------|---------------|---------------|
|Manifest dla aplikacji, których platforma docelowa to wersja 2.0 lub 3.x programu .NET Framework|Otwarcie|OK|OK|
||Zamykanie|OK|OK|
||Zapisz|OK|OK|
||Ponowne podpisane|OK|OK|
||Nowa|OK|Nieobsługiwane|
||Aktualizacja (zobacz poniżej)|OK|OK|
|Manifest dla aplikacji, których platforma docelowa to wersja 4 programu .NET Framework|Otwarcie|OK|OK|
||Zamykanie|OK|OK|
||Zapisz|OK|OK|
||Ponowne podpisane|OK|OK|
||Nowa|Nieobsługiwane|OK|
||Aktualizacja (zobacz poniżej)|Nieobsługiwane|OK|

|Wersja manifestu|Szczegóły operacji aktualizacji|Mage w wersji 2.0|Mage w wersji 4.0|
|----------------------|------------------------------|---------------|---------------|
|Manifest dla aplikacji, których platforma docelowa to wersja 2.0 lub 3.x programu .NET Framework|Modyfikacja zestawu|OK|OK|
||Dodanie zestawu|OK|OK|
||Usunięcie zestawu|OK|OK|
|Manifest dla aplikacji, których platforma docelowa to wersja 4 programu .NET Framework|Modyfikacja zestawu|Nieobsługiwane|OK|
||Dodanie zestawu|Nieobsługiwane|OK|
||Usunięcie zestawu|Nieobsługiwane|OK|

 Program Mage.exe tworzy nowe manifesty ukierunkowane na profil klienta programu .NET Framework 4. ClickOnce aplikacje, które są przeznaczone na profil klienta .NET Framework 4 można uruchomić zarówno na profilu klienta .NET Framework 4 i pełnej wersji programu .NET Framework 4. Jeśli aplikacja jest przeznaczona dla pełnej wersji programu .NET Framework 4 i nie `<framework>` można uruchomić w profilu klienta programu .NET Framework 4, usuń element klienta za pomocą edytora tekstu i ponownie podpisz manifest.

Poniżej przedstawiono `<framework>` przykładowy element, który jest przeznaczony dla profilu klienta programu .NET Framework 4:

```xml
<framework targetVersion="4.0" profile="client" supportedRuntime="4.0.20506" />
```

## <a name="examples"></a>Przykłady

Poniższy przykład otwiera interfejs użytkownika maga (*MageUI.exe*).

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

## <a name="see-also"></a>Zobacz też

- [Kliknijonce zabezpieczenia i wdrażanie](/visualstudio/deployment/clickonce-security-and-deployment)
- [Wskazówki: ręczne wdrażanie aplikacji ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Przegląd wdrażania zaufanych aplikacji](/visualstudio/deployment/trusted-application-deployment-overview)
- [MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
