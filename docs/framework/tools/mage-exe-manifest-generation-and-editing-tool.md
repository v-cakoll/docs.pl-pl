---
title: Mage.exe (Narzędzie generowania manifestu i edytowania)
ms.date: 03/30/2017
helpviewer_keywords:
- Manifest Generation and Editing tool
- Mage.exe
ms.assetid: 77dfe576-2962-407e-af13-82255df725a1
ms.openlocfilehash: 8144e82f55522f65de96c120f42c50702b80fa16
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208460"
---
# <a name="mageexe-manifest-generation-and-editing-tool"></a>Mage.exe (Narzędzie generowania manifestu i edytowania)
Generowanie manifestu i narzędzia do edycji (*Mage.exe*) to narzędzie wiersza polecenia, które obsługuje tworzenia i edycji manifestów aplikacji i wdrażania. Jako narzędzie wiersza polecenia *Mage.exe* mogą być uruchamiane z partii, skrypty i inne aplikacje systemu Windows, w tym [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikacji.  
  
 Można również użyć *MageUI.exe*, graficznego aplikacji, zamiast *Mage.exe*. Aby uzyskać więcej informacji, zobacz [MageUI.exe (Generowanie manifestu i edytowania narzędzia graficzne klienta)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Dwie wersje *Mage.exe* i *MageUI.exe* są dołączone jako część [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] Instalatora. Aby wyświetlić informacje o wersji, uruchom *MageUI.exe*, wybierz pozycję **pomocy**i wybierz **o**. W tej dokumentacji opisano wersję 4.0.x.x z *Mage.exe* i *MageUI.exe*.  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
Mage [commands] [commandOptions]  
```  
  
#### <a name="parameters"></a>Parametry  
 W poniższej tabeli przedstawiono polecenia obsługiwane przez *Mage.exe*. Aby uzyskać więcej informacji na temat opcji obsługiwane przez te polecenia, zobacz [nowy i opcje polecenia aktualizacji](#NewUpdate) i [opcji polecenia znak](#Sign).  
  
|Polecenie|Opis|  
|-------------|-----------------|  
|**-DW ClearApplicationCache**|Czyści pamięć podręczną pobranych aplikacji ze wszystkich aplikacji działających tylko w trybie online.|  
|**-n, - nowego** *fileType [newOptions]*|Tworzy nowy plik danego typu. Prawidłowymi typami są:<br /><br /> -   `Deployment`: Tworzy nowy manifest wdrażania.<br />-   `Application`: Tworzy nowy manifest aplikacji.<br /><br /> Jeśli nie określono żadnych dodatkowych parametrów dla tego polecenia, zostanie utworzony plik odpowiedniego typu, z odpowiednimi domyślnymi tagami oraz wartościami atrybutów.<br /><br /> Użyj **- ToFile** opcji (zobacz poniższą tabelą) aby określić nazwę pliku i ścieżkę nowego pliku.<br /><br /> Użyj **- FromDirectory** opcji (zobacz poniższą tabelą) do utworzenia manifest aplikacji z wszystkich zestawów dla aplikacji, który został dodany do \<zależności > sekcji manifestu.|  
|**-u,-aktualizacji** *[ścieżka] [updateOptions]*|Wprowadza co najmniej jedną zmianę w pliku manifestu. Nie trzeba określać typu edytowanego pliku. Program Mage.exe zbada plik za pomocą zestawu algorytmów heurystycznych i ustali, czy jest to manifest wdrożenia, czy aplikacji.<br /><br /> Jeśli jesteś już zarejestrowanym pliku przy użyciu certyfikatu **— aktualizacja** spowoduje usunięcie blok podpisu klucza. Dzieje się tak dlatego, że podpis klucza zawiera skrót pliku i modyfikacja pliku spowoduje, że skrót będzie nieprawidłowy.<br /><br /> Użyj **- ToFile** opcji (zobacz w poniższej tabeli), aby określić nową nazwę pliku i ścieżkę zamiast zastępowanie istniejącego pliku.|  
|**-s,-znak** `[signOptions]`|Używa pary kluczy lub certyfikatu X509 w celu podpisania pliku. Podpisy są wstawiane jako elementy XML wewnątrz plików.<br /><br /> Musisz mieć połączenie z Internetem podczas podpisywania manifestu, który określa **- TimestampUri** wartość.|  
|**-h,-?, - pomocy** *[verbose]*|Opisuje wszystkie z dostępnych poleceń i ich opcji. Określ `verbose` uzyskać szczegółową pomoc.|  
  
<a name="NewUpdate"></a>   
## <a name="new-and-update-command-options"></a>Opcje poleceń New i Update  

W poniższej tabeli przedstawiono opcje obsługiwane przez `-New` i `-Update` polecenia:  
  
|Opcje|Wartość domyślna|Dotyczy:|Opis|  
|-------------|-------------------|----------------|-----------------|  
|**-, — algorytm**|sha1RSA|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Określa algorytm, za pomocą którego zostaną wygenerowane skróty zależności. Wartością musi być „sha256RSA” lub „sha1RSA”.<br /><br /> Należy używać z opcją „-Update”. Ta opcja jest ignorowana, gdy używana jest opcja „-Sign”.|  
|**-appc, - AppCodeBase** `manifestReference`||Manifesty wdrożenia.|Wstawia odwołanie do adresu URL lub ścieżki pliku do pliku manifestu aplikacji. Ta wartość musi być pełną ścieżką do manifestu aplikacji.|  
|**-appm, - AppManifest** `manifestPath`||Manifesty wdrożenia.|Wstawia do manifestu wdrożenia odwołanie do manifestu wdrażanej aplikacji.<br /><br /> Wskazuje plik `manifestPath` musi istnieć lub *Mage.exe* zgłosi błąd. Jeśli odwołuje się plik `manifestPath` manifest aplikacji nie jest *Mage.exe* zgłosi błąd.|  
|**-cf, - Plik_certyfikatu** `filePath`||Wszystkie typy plików.|Określa lokalizację cyfrowego certyfikatu X509 używanego do podpisania manifestu. Tej opcji można używać w połączeniu z **-hasło** opcji w przypadku, gdy certyfikatu wymaga hasła.<br/><br/>Począwszy od zestawu SDK .NET Framework 4.6.2, który jest dostarczany z programem Visual Studio, zestaw Windows SDK i .NET Framework 4.6.2 z dodatkiem Developer Pack, *Mage.exe* znaki manifesty CNG, jak również CAPI certyfikatów.|  
|**-ch, — skrót certyfikatu** `hashSignature`||Wszystkie typy plików.|Skrót certyfikatu cyfrowego przechowywanego w osobistym magazynie certyfikatów na komputerze klienta. Odpowiada on ciągowi odcisku palca certyfikatu cyfrowego wyświetlanego w konsoli certyfikatów systemu Windows.<br /><br /> `hashSignature` może to być albo wielkie lub małe litery i mogą być dostarczane jako pojedynczy ciąg lub z każdym octet odcisk palca oddzielone spacjami i odcisk palca całego ujęta w znaki cudzysłowu.|  
|**-fd, - FromDirectory** `directoryPath`||Manifesty aplikacji.|Wypełnia manifest aplikacji z opisami wszystkich zestawów i pliki znajdujące się w `directoryPath`, w tym wszystkie podkatalogi, gdzie `directoryPath` jest katalog, który zawiera aplikację, którą chcesz wdrożyć. Dla każdego pliku w katalogu *Mage.exe* decyduje o tym, czy plik jest zestawem lub plików statycznych. Jeśli jest zestawem, dodaje `<dependency>` tagu i `installFrom` atrybutu z nazwą zestawu, ścieżki bazowej kodu i wersją aplikacji. Jeśli jest to plik statyczny, dodaje `<file>` tagu. *Mage.exe* będą też używać prostym zestawem algorytmów heurystycznych wykryć główny plik wykonywalny dla aplikacji i oznacz ją jako punkt wejścia aplikacji ClickOnce w manifeście.<br /><br /> *Mage.exe* nigdy nie automatycznie przywróci znacznik pliku w formacie "dane". Tę czynność należy wykonać ręcznie. Aby uzyskać więcej informacji, zobacz [porady: uwzględnianie pliku danych w aplikacji ClickOnce](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application).<br /><br /> *Mage.exe* również generuje skrót dla każdego pliku na podstawie jego rozmiaru. Technologia ClickOnce używa tych skrótów, aby zagwarantować, że nikt nie ingerował w pliki wdrożenia od czasu utworzenia manifestu. Zmienić dowolny plik w danym wdrożeniu, można uruchomić *Mage.exe* z **— aktualizacja** polecenia i **- FromDirectory** opcja która spowoduje zaktualizowanie wartości skrótu i zestawu wersje wszystkich plików.<br /><br /> **-FromDirectory** będzie zawierać wszystkie pliki w podkatalogach znaleziony w `directoryPath`.<br /><br /> Jeśli używasz **- FromDirectory** z **— aktualizacja** polecenia *Mage.exe* usunie wszystkie pliki w manifeście aplikacji, która już istnieje w katalogu.|  
|**— Jeśli, - IconFile**  `filePath`||Manifesty aplikacji.|Określa pełną ścieżkę do pliku ikony ICO. Ta ikona pojawia się obok nazwy aplikacji w menu Start oraz we wpisie w aplecie Dodaj lub usuń programy. Jeśli nie zostanie dostarczona ikona, będzie używana ikona domyślna.|  
|**-ip, - IncludeProviderURL**  `url`|true|Manifesty wdrożenia.|Wskazuje, czy manifest rozmieszczenia nie zawiera wartości lokalizacji aktualizacji **- ProviderURL**.|  
|**-i,-zainstaluj** `willInstall`|true|Manifesty wdrożenia.|Wskazuje, czy aplikacja ClickOnce ma zostać zainstalowana na komputerze lokalnym, czy ma być uruchamiana z sieci Web. Instalowanie aplikacji daje aplikację obecności w systemie Windows **Start** menu. Prawidłowymi wartościami są „true” lub „t” oraz „false” lub „f”.<br /><br /> Jeśli określisz **- MinVersion** opcji, a użytkownik ma wersję mniej niż **- MinVersion** zainstalowany, zostanie wymuszone aplikację do zainstalowania, niezależnie od wartości, które można przekazać do **- Zainstaluj**.<br /><br /> Nie można użyć tej opcji z **- BrowserHosted** opcji. Próba określenia obu tych opcji dla jednego manifestu spowoduje błąd.|  
|**-mv, - MinVersion**  `[version]`|Wersja podana w manifest wdrażania ClickOnce, określony przez **— wersja** flagi.|Manifesty wdrożenia.|Minimalna wersja aplikacji, jaką może uruchomić użytkownik. Ta flaga powoduje, że nazwana wersja aplikacji staje się wymaganą aktualizacją. Jeśli zostanie wydana wersja produktu z aktualizacją dotyczącą ważnej zmiany lub krytycznej wady zabezpieczeń, można użyć tej flagi, aby określić, że ta aktualizacja musi zostać zainstalowana, a użytkownik nie może kontynuować używania wcześniejszych wersji.<br /><br /> `version` ma tej samej semantyki jako argument **— wersja** flagi.|  
|**-n, — nazwa** `nameString`|Deploy|Wszystkie typy plików.|Nazwa, która jest używana do identyfikacji aplikacji. ClickOnce będzie użyć tej nazwy, aby zidentyfikować tę aplikację w **Start** menu (Jeśli aplikacja jest skonfigurowana do instalacji) i okien dialogowych podniesienia uprawnień. **Uwaga:** aktualizowania istniejących manifestu, jeśli nie określisz nazwy wydawcy z tą opcją *Mage.exe* aktualizuje plik manifestu z nazwą organizacji, zdefiniowanych na komputerze. Aby użyć innej nazwy, należy użyć tej opcji i określić odpowiednią nazwę wydawcy.|  
|**-pwd, — hasło** `passwd`||Wszystkie typy plików.|Hasło używane do podpisywania manifestu za pomocą certyfikatu cyfrowego. Należy używać w połączeniu z **- Plik_certyfikatu** opcji.|  
|**Procesor -p,** `processorValue`|Msil|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Architektura mikroprocesora, na której będzie uruchomiona dystrybucja. Ta wartość jest wymagana, jeśli jest przygotowywanych kilka instalacji, których zestawy są wstępnie kompilowane dla określonego mikroprocesora. Prawidłowe wartości to `msil`, `x86`, `ia64`, i `amd64`. `msil` Firma Microsoft język pośredni, co oznacza, że wszystkie Twoje zestawy są niezależne od platformy i środowisko uruchomieniowe języka wspólnego (CLR) zostanie w czasie kompilowania ich, gdy aplikacja jest pierwszym uruchomieniu.|  
|**-pu,** **- ProviderURL** `url`||Manifesty wdrożenia.|Określa adres URL, pod którym technologia ClickOnce będzie szukać aktualizacji aplikacji.|  
|**-pub,-wydawcy** `publisherName`||Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Dodaje nazwę wydawcy do opisu elementu manifestu wdrożenia lub aplikacji. Jeśli używany w manifeście aplikacji **- UseManifestForTrust** musi być także określona wartość "true" lub "t"; w przeciwnym razie wartość tego parametru zgłosi błąd.|  
|**-s, - SupportURL**  `url`||Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Określa łącze, które pojawia się w aplecie Dodaj lub usuń programy dla aplikacji ClickOnce.|  
|**-analizy czasowej, - TimestampUri** `uri`||Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Adres URL usługi cyfrowego oznaczania znacznikami czasu. Oznaczenie manifestu znacznikiem czasu zapobiega konieczności ponownego podpisania manifestu, jeśli certyfikat cyfrowy wygaśnie przed wdrożeniem następnej wersji aplikacji. Aby uzyskać więcej informacji, zobacz [Windows root członkowie programu certyfikatów](http://go.microsoft.com/fwlink/?LinkId=159000).|  
|**-t, - ToFile** `filePath`|-Nowe:<br />-Wdrożenie: deploy.application<br />-Aplikacji: application.exe.manifest<br />-Aktualizacja:<br />-Pliku wejściowego.|Wszystkie typy plików.|Określa ścieżkę wyjściową utworzonego lub zmodyfikowanego pliku.<br /><br /> Jeśli **- ToFile** nie jest podany, korzystając z **— nowy**, dane wyjściowe są zapisywane do bieżącego katalogu roboczego. Jeśli **- ToFile** nie jest podany, korzystając z **— aktualizacja**, *Mage.exe* zapisze plik powrót do pliku wejściowego.|  
|**-tr, - TrustLevel** `level`|Wartość określana na podstawie strefy, w której znajduje się adres URL aplikacji.|Manifesty aplikacji.|Poziom zaufania, który zostanie przyznany aplikacji na komputerach klientów. Dostępne wartości to Internet, Intranet i FullTrust.|  
|**-um, - UseManifestForTrust** `willUseForTrust`|False|Manifesty aplikacji.|Określa, czy podpis cyfrowy manifestu aplikacji będzie używany do podejmowania decyzji dotyczących zaufania, gdy aplikacja zostanie uruchomiona na komputerze klienckim. Określenie wartości „true” lub „t” wskazuje, że manifest aplikacji zostanie użyty do podejmowania decyzji dotyczących zaufania. Określenie wartości „false” lub „f” wskazuje, że zostanie użyty podpis manifestu wdrożenia.|  
|**-v,-wersja** `versionNumber`|1.0.0.0|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Wersja wdrożenia. Argument musi być prawidłowym ciągiem wersji formatu "*N.N.N.N*", gdzie"*N*" jest liczbą całkowitą bez znaku 32-bitowych.|  
|**-wpf, - WPFBrowserApp**  `isWPFApp`|false|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Tej flagi należy używać tyko wtedy, gdy aplikacja jest aplikacją programu Windows Presentation Foundation (WPF), która będzie obsługiwana wewnątrz programu Internet Explorer i nie jest autonomicznym plikiem wykonywalnym. Prawidłowymi wartościami są „true” lub „t” oraz „false” lub „f”.<br /><br /> Manifesty aplikacji można wstawia `hostInBrowser` atrybutu w obszarze `entryPoint` element manifestu aplikacji.<br /><br /> Manifesty wdrożenia Określa `install` atrybutu `deployment` elementu na wartość FAŁSZ i zapisuje wdrożenia manifestu z rozszerzeniem .xbap. Użycie tego argumentu wraz z **-Zainstaluj** argument powoduje błąd, ponieważ aplikacja oparta na przeglądarce nie może zostać zainstalowana aplikacja w trybie offline.|  
  
<a name="Sign"></a>   
## <a name="sign-command-options"></a>Opcje polecenia Sign  
 W poniższej tabeli przedstawiono opcje obsługiwane przez `-Sign` polecenia, które mają zastosowanie do wszystkich typów plików.  
  
|Opcje|Opis|  
|-------------|-----------------|  
|**-cf, - Plik_certyfikatu** `filePath`|Określa lokalizację certyfikatu cyfrowego używanego do podpisania manifestu. Tej opcji można używać w połączeniu z **-hasło** opcji.|  
|**-ch, — skrót certyfikatu** `hashSignature`|Skrót certyfikatu cyfrowego przechowywanego w osobistym magazynie certyfikatów na komputerze klienta. Odpowiada właściwości odcisku palca certyfikatu cyfrowego wyświetlanego na konsoli certyfikatów systemu Windows.<br /><br /> `hashSignature` może to być albo wielkie lub małe litery i mogą być dostarczane za pomocą jednego ciągu lub za każdy oktet odcisk palca oddzielone spacjami i odcisk palca całego ujęta w znaki cudzysłowu.|  
|**-pwd, — hasło** `passwd`|Hasło używane do podpisywania manifestu za pomocą certyfikatu cyfrowego. Należy używać w połączeniu z **- Plik_certyfikatu** opcji.|  
|**-t, - ToFile** `filePath`|Określa ścieżkę wyjściową utworzonego lub zmodyfikowanego pliku.|  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie argumenty do *Mage.exe* jest rozróżniana wielkość liter. Polecenia i opcje mogą być poprzedzone kreską (-) lub ukośnikiem (/).  
  
 Wszystkie argumenty używane z **-znak** polecenia można użyć w dowolnym momencie bez **— nowy** lub **-aktualizacji** również polecenia. Poniższe polecenia są równoważne.  
  
```  
mage -Sign c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx  
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx  
```  
  
> [!NOTE]
>  Od programu .NET Framework w wersji 4.6.2, CNG certyfikatów również są obsługiwane.  
  
 Podpisywanie jest ostatnim zadaniem, które należy wykonać, ponieważ podpisany dokument używa skrótu pliku w celu weryfikacji, czy podpis jest prawidłowy dla dokumentu. W przypadku wprowadzenia jakiejkolwiek zmiany w podpisanym pliku należy podpisać go ponownie. Jeśli zarejestrujesz dokument, który został wcześniej zarejestrowane, *Mage.exe* spowoduje zastąpienie starych podpisu z nowym.  
  
 Jeśli używasz **- AppManifest** opcję, aby wypełnić manifest wdrażania, *Mage.exe* przyjmie założenie, że manifest aplikacji będą znajdować się w tym samym katalogu co wdrożenie manifestu w podkatalog o nazwie po bieżącej wersji wdrożenia i odpowiednio skonfigurować manifeście wdrażania. Jeśli manifest aplikacji będą znajdować się w innym miejscu, należy użyć **- AppCodeBase** możliwość ustawienia lokalizacji alternatywnej.  
  
 Manifesty wdrożenia i aplikacji muszą zostać podpisane przed wdrożeniem aplikacji. Aby uzyskać wskazówki dotyczące podpisywania manifestów, zobacz [zaufane Omówienie wdrożenia aplikacji](/visualstudio/deployment/trusted-application-deployment-overview).  
  
 **- TrustLevel** opcję manifesty aplikacji opisuje zestaw uprawnień aplikacji wymaga do uruchomienia na komputerze klienckim. Domyślnie aplikacje są przypisane poziom zaufania, na podstawie *strefy* , w którym znajduje się ich adresu URL. Aplikacje wdrożone przez sieć firmową są zazwyczaj umieszczane w strefie Intranet, podczas gdy te wdrożone przez Internet umieszczane są w strefie Internet. Obie strefy zabezpieczeń nakładają na aplikację ograniczenia w zakresie dostępu do lokalnych zasobów, przy czym strefa Intranet ma nieco łagodniejsze ograniczenia niż strefa Internet. Strefa FullTrust udziela aplikacji pełnego dostępu do lokalnych zasobów komputera. Jeśli używasz **- TrustLevel** opcji w celu umieszczenia aplikacji w tej strefie, składnika menedżera zaufania środowiska CLR pojawi się monit zdecydować, czy użytkownik chce zezwolić na wyższy poziom zaufania. Jeśli aplikacja jest wdrażana przez sieć firmową, można użyć narzędzia Wdrażanie zaufanych aplikacji, aby podnieść poziom zaufania aplikacji bez monitowania użytkownika.  
  
 Manifesty aplikacji obsługują także niestandardowe sekcje zaufania. Pomaga to aplikacji przestrzegać reguły zabezpieczeń, zgodnie z którą należy żądać jak najniższych uprawnień, ponieważ można skonfigurować manifest do żądania tylko tych określonych uprawnień, których aplikacja wymaga do działania. *Mage.exe* nie obsługuje bezpośrednio dodanie sekcji niestandardowych zaufania. Można to zrobić za pomocą edytora tekstu, analizatora składni XML lub narzędzia graficzne *MageUI.exe*. Aby uzyskać więcej informacji o sposobie używania *MageUI.exe* do dodania zaufania niestandardowe sekcje, zobacz [MageUI.exe (Generowanie manifestu i edytowania narzędzia graficzne klienta)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
 Nowe manifestów, które są tworzone w wersji 4 z *Mage.exe*, która jest dostarczana z [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], docelowy [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Aby skierować je do wcześniejszych wersji programu .NET Framework, należy użyć starszej wersji programu *Mage.exe*. Dodawanie lub usuwanie zestawów z istniejących manifestu lub ponownie podpisać manifest istniejących *Mage.exe* nie zaktualizować manifestu do docelowego [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. W poniższej tabeli przedstawiono te funkcje i ograniczenia.  
  
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
  
 Mage.exe tworzy nowy manifestów kierowanych [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. ClickOnce — aplikacje przeznaczone [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] można uruchamiać na obu [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] i pełną wersję programu [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Jeśli aplikacja jest przeznaczony dla pełną wersję programu [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] i nie można uruchomić na [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)], Usuń klienta `<framework>` elementu za pomocą edytora tekstu i ponowne podpisywanie manifestu. Poniżej przedstawiono przykładowe `<framework>` elementu, którego celem jest [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)].  
  
```xml  
<framework targetVersion="4.0" profile="client" supportedRuntime="4.0.20506" />  
```  
  
## <a name="examples"></a>Przykłady  
 Poniższy przykład powoduje otwarcie interfejsu użytkownika dla obraz (*MageUI.exe*).  
  
```  
mage  
```  
  
 W poniższym przykładzie są tworzone domyślne manifesty wdrożenia i aplikacji. Wszystkie te pliki są tworzone w bieżącym katalogu roboczym i są nazwane odpowiednio deploy.application i application.exe.manifest.  
  
```  
mage -New Deployment  
mage -New Application  
```  
  
 Poniższy przykład tworzy wypełniane przy użyciu wszystkich zestawów i zasobów plików z katalogu thecurrent manifestu aplikacji.  
  
```  
mage -New Application -FromDirectory . -Version 1.0.0.0  
```  
  
 W poniższym przykładzie jest kontynuowany poprzedni przykład i jest określana nazwa wdrożenia oraz docelowy mikroprocesor. Określany jest także adres URL, pod którym technologia ClickOnce będzie sprawdzać dostępność aktualizacji.  
  
```  
mage -New Application -FromDirectory . -Name "Hello, World! Application" -Version 1.0.0.0 -Processor "x86" -ProviderUrl http://internalserver/HelloWorld/  
```  
  
 W poniższym przykładzie pokazano sposób tworzenia pary manifestów dla wdrożenia aplikacji programu WPF, która będzie obsługiwana w programie Internet Explorer.  
  
```  
mage -New Application -FromDirectory . -Version 1.0.0.0 -WPFBrowserApp true  
mage -New Deployment -AppManifest 1.0.0.0\application.manifest -WPFBrowserApp true  
```  
  
 W poniższym przykładzie manifest wdrożenia jest aktualizowany informacjami z manifestu aplikacji, a także jest ustawiana podstawa kodu dla lokalizacji manifestu aplikacji.  
  
```  
mage -Update HelloWorld.deploy -AppManifest 1.0.0.0\application.manifest -AppCodeBase http://internalserver/HelloWorld.deploy  
```  
  
 W poniższym przykładzie manifest wdrożenia jest edytowany w celu wymuszenia aktualizacji zainstalowanej wersji użytkownika.  
  
```  
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -MinVersion 1.1.0.0  
```  
  
 W poniższym przykładzie manifest wdrożenia otrzymuje instrukcję pobrania manifestu aplikacji z innego katalogu.  
  
```  
mage -Update HelloWorld.deploy -AppCodeBase http://anotherserver/HelloWorld/1.1.0.0/  
```  
  
 W poniższym przykładzie istniejący manifest wdrożenia jest podpisywany przy użyciu certyfikatu cyfrowego w bieżącym katalogu roboczym.  
  
```  
mage -Sign deploy.application -CertFile cert.pfx -Password <passwd>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)  
 [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)  
 [Przegląd wdrażania zaufanych aplikacji](/visualstudio/deployment/trusted-application-deployment-overview)  
 [MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
