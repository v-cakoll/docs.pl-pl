---
title: "MageUI.exe (Narzędzie generowania i edytowania manifestu, klient grafiki)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Manifest Generation and Editing tool
- MageUI.exe
ms.assetid: f9e130a6-8117-49c4-839c-c988f641dc14
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1450acd6c4b68be79ad769106dfebc7d89484525
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mageuiexe-manifest-generation-and-editing-tool-graphical-client"></a>MageUI.exe (Narzędzie generowania i edytowania manifestu, klient grafiki)
MageUI.exe obsługuje takie same funkcje jak narzędzie wiersza polecenia Mage.exe, ale z interfejsem użytkownika systemu Windows (UI). Za pomocą tego narzędzia można tworzyć, edytować i podpisywać manifesty wdrażania i aplikacji. Nowe manifestów, które są tworzone z elementem docelowym MageUI.exe [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Poprzednie wersje MageUI.exe stosuje się do poprzednich wersji .NET Framework. Dodawanie lub usuwanie zestawów z manifestu lub ponownego podpisania manifestów istniejących, MageUI.exe nie zaktualizował manifest docelowej [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Aby uzyskać więcej informacji, zobacz [Mage.exe (Generowanie manifestu i edytowania narzędzie)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Dwie wersje Mage.exe i MageUI.exe są dołączone jako część [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] Instalatora. Aby wyświetlić informacje o wersji, uruchom MageUI.exe wybierz **pomocy**i wybierz **o**. W tej dokumentacji opisano wersję 4.0.x.x programów Mage.exe i MageUI.exe.  
  
> [!NOTE]
>  MageUI.exe nie obsługuje [compatibleFrameworks](/visualstudio/deployment/compatibleframeworks-element-clickonce-deployment) elementu podczas zapisywania manifest aplikacji, która została już podpisana przy użyciu certyfikatu przy użyciu MageUI.exe. Zamiast tego należy użyć [Mage.exe](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
## <a name="uielement-list"></a>Lista elementów UI  
 W następującej tabeli wymieniono elementy menu i paski narzędzi, które są dostępne.  
  
|Polecenie|Menu|Skrót|Opis|  
|-------------|----------|--------------|-----------------|  
|**Manifest aplikacji**|**Plik, nowy**||Tworzy nowy manifest aplikacji.|  
|**Manifest rozmieszczenia**|**Plik, nowy**||Tworzy nowy manifest wdrożenia.|  
|**Otwórz**|**Plik**|CTRL+O|Otwiera do edycji istniejący manifest wdrażania, manifest aplikacji lub licencję zaufania.|  
|**Zamknij**|**Plik**|CTRL+F4|Zamyka otwarty plik.<br /><br /> Jeśli modyfikujesz plik przed jego zamknięciem, MageUI.exe monituje o ponowne podpisywanie pliku kluczem publicznym, parą kluczy lub przechowywanym certyfikatem.|  
|**Zapisz**|**Plik**|CTRL+S|Zapisuje na dysku dokument, który aktualnie ma fokus wprowadzania użytkownika.|  
|**Zapisz jako**|**Plik**||Zapisuje plik na dysku, umożliwiając podanie nowej nazwy pliku i/lub lokalizacji.|  
|**Zapisz wszystkie**|**Plik**||Zapisuje zmiany wprowadzone do wszystkich plików aktualnie otwartych w MageUI.exe.|  
|**Preferencje**|**Plik**||Otwiera **preferencje** okno dialogowe. Aby uzyskać więcej informacji, zobacz następującą sekcję.|  
|**Zakończ**|**Plik**|ALT+F4|Zamyka program MageUI.exe.|  
|**Wytnij**|**Edytowanie**|CTRL+X|Usuwa zaznaczony tekst z aplikacji i przenosi je do Schowka systemu Windows.|  
|**Kopiuj**|**Edytowanie**|CTRL+C|Kopiuje zaznaczony tekst do Schowka systemu Windows.|  
|**Wklej**|**Edytowanie**|CTRL+V|Wkleja tekst ze Schowka systemu Windows do aktywnego elementu tekstu.|  
|**Usuwanie**|**Edytowanie**||Usuwa element aktualnie wybrane na liście, takie jak licencji zaufania na **Manifest wdrażania** kartę.|  
|**Zamknij wszystkie**|**Okno**||Zamyka wszystkie pliki otwarte w MageUI.exe. Jeżeli jeden lub więcej plików wymagają zapisania, MageUI.exe wyświetli monit o zapisanie ich. MageUI.exe również wyświetla monit o wybranie klucza podpisywania dla każdego niepodpisanego lub zmienionego pliku.|  
|**— Informacje**|**Pomoc**||Wyświetla informacje o wersji i prawach autorskich dotyczące MageUI.exe.|  
  
## <a name="preferences-dialog-box"></a>Okno dialogowe Preferencje  
 **Preferencje** okno dialogowe zawiera następujące elementy.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Zaloguj się przy zapisie**|Monituje o podpisanie pliku przy każdym zapisie modyfikacji.|  
|**Użyj domyślnego certyfikatu podpisywania**|Używa klucza w **plik certyfikatu** pole tekstowe służące do podpisywania wszystkich plików. Eliminuje to podpisania monit zwykle wyświetlany podczas zapisywania pliku i **Zaloguj się przy zapisie** jest zaznaczone. Użyj wielokropka (**...** ) znajdujący się obok **plik certyfikatu** pole tekstowe, aby wybrać plik klucza.|  
|Algorytm porządkowania|Określa algorytm, za pomocą którego zostaną wygenerowane skróty zależności. Wartością musi być „sha256RSA” lub „sha1RSA”. Domyślną wartością jest SHA1. Używana zarówno w manifestach aplikacji, jak i wdrażania. Jeśli użytkownik poda certyfikat podczas zapisywania manifestu, używane są algorytmy w certyfikacie do wygenerowania rozkładów zależności.|  
  
## <a name="signing-options-dialog-box"></a>Okno dialogowe Opcje podpisywania  
 **Opcje podpisywania** zostanie wyświetlone okno dialogowe po zapisaniu licencji manifestu lub relacji zaufania po raz pierwszy lub po zmianie licencji manifestu lub relacji zaufania. Pojawia się tylko jeśli **Zaloguj się przy zapisie** opcji **preferencje** okno dialogowe jest zaznaczone. Musisz mieć połączenie z Internetem podczas podpisywania manifestu, który określa wartość w **TimeStamping URI** pola tekstowego.  
  
 To okno dialogowe zawiera następujące elementy.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Podpisać plik certyfikatu**|Podpisuje manifest certyfikatem cyfrowym przechowywanym w systemie plików.|  
|**Plik**|Zapewnia miejsce do wpisania ścieżki do pliku pfx reprezentującego certyfikat.|  
|**...**|Otwiera **wybierz plik** okno dialogowe Wybieranie istniejącego pliku pfx.|  
|**Nowy**|Generuje nowy pfx niesprawdzalny przez urząd certyfikacji (CA). Aby uzyskać więcej informacji na temat typów używany do podpisywania certyfikatów [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] wdrożenia, zobacz [zaufane Omówienie wdrożenia aplikacji](/visualstudio/deployment/trusted-application-deployment-overview).|  
|**Hasło**|Miejsce na wpisanie hasła używanego do podpisywania tym certyfikatem. Jeśli nie ma to zastosowania, może być puste.|  
|**Podpisać przechowywanego certyfikatu**|Wyświetla listę wyboru certyfikatów cyfrowych przechowywanych w magazynie certyfikatów na komputerze.|  
|**Identyfikator URI sygnatur**|Wyświetla identyfikator URI usługi sygnatur cyfrowych. Przypisanie do manifestu znacznika czasu zapobiega konieczności ponownego podpisania manifestu, jeśli certyfikat cyfrowy wygaśnie przed wdrożeniem następnej wersji aplikacji. Aby uzyskać więcej informacji, zobacz [Windows root członkowie programu certyfikatów](http://go.microsoft.com/fwlink/?LinkId=159000) i [ClickOnce i podpis Authenticode](/visualstudio/deployment/clickonce-and-authenticode).|  
|**Nie loguj się**|Umożliwia zapisanie manifestu bez dodawania podpisu z certyfikatu cyfrowego.|  
  
## <a name="tab-and-panel-descriptions"></a>Opisy karta i panelu  
 Po otwarciu w programie MageUI.exe dokument pojawia się w obrębie własnej strony karty. Każda karta zawiera zestaw paneli właściwości. Panele zawierają zgrupowane podzbiory danych dokumentu.  
  
### <a name="application-manifest-tab"></a>Karta manifestu aplikacji  
 **Manifest aplikacji** kartę Wyświetla zawartość manifestu aplikacji. Manifest aplikacji zawiera opis wszystkich plików dołączonych do wdrożenia i uprawnień wymaganych do uruchomienia na kliencie aplikacji.  
  
 **Manifest aplikacji** karta zawiera następujące karty.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Określa informacje identyfikacyjne dotyczące tego wdrożenia.|  
|**Opis**|Określa wydawcy, produktu i pomocy technicznej informacji.|  
|**Opcje aplikacji**|Określa, czy to jest aplikacją przeglądarki oraz czy tym manifestu jest źródło informacji zaufania.|  
|**Pliki**|Określa wszystkich plików wchodzących w skład tego wdrożenia.|  
|**Wymagane uprawnienia**|Określa zestaw minimalne uprawnienia wymagane przez aplikację do uruchomienia na komputerze klienckim.|  
  
### <a name="name-tab"></a>Karta nazw  
 **Nazwa** karta jest wyświetlana, gdy najpierw utworzyć lub otworzyć manifest aplikacji. Identyfikuje wdrożenia i opcjonalnie określa platformę prawidłowego elementu docelowego.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Wymagany. Nazwa manifestu aplikacji. Zazwyczaj takie same jak nazwa pliku.|  
|**Wersja**|Wymagany. Numer wersji wdrożenia w formie *N.N.N.N*. Wymagany jest tylko pierwszy numer kompilacji głównych. Na przykład dla aplikacji w wersji 1.0, prawidłowe wartości to `1`, `1.0`, `1.0.0`, i `1.0.0.0`.|  
|**Procesor**|Opcjonalny. Architektura komputera, na którym można uruchomić tego wdrożenia. Wartość domyślna to `msil`, lub języka pośredniego firmy Microsoft, który jest domyślny format wszystkich zestawów zarządzanych. Zmień to pole, jeśli zestawy ma wstępnie skompilowany w aplikacji dla określonej architektury. Aby uzyskać więcej informacji o wstępnej kompilacji, zobacz [Ngen.exe (Generator obrazu natywnego)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|  
|**Kultury**|Opcjonalny. Dwuczęściową krajów, regionów kod ISO w którym ta aplikacja działa. Wartość domyślna to `neutral`.|  
|**Token klucza publicznego**|Opcjonalny. Klucz publiczny, z którego został podpisany w manifeście aplikacji. Jeśli jest to nowe lub unsigned manifestu, w tym polu pojawi się `Unsigned`.|  
  
### <a name="description-tab"></a>Opis elementu kartę  
 Te informacje zazwyczaj znajduje się w manifeście rozmieszczenia. Te pola można modyfikować tylko w przypadku **manifestu zaufania informacje o aplikacji użyj** zostało zaznaczone pole wyboru **Opcje aplikacji** kartę.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Wydawcy**|Nazwa osoby lub organizacja odpowiadające dla aplikacji. Ta wartość jest używana jako nazwa folderu menu Start.|  
|**Produktu**|Pełna nazwa produktu. W przypadku wybrania **zainstalować lokalnie** dla **typu aplikacji** elementu na **opcje wdrażania** karta manifestu rozmieszczenia, ta nazwa będzie, co jest wyświetlana w **Start** łącze menu i **Dodaj lub usuń programy** dla tej aplikacji.|  
|**Obsługa lokalizacji**|Adres URL, z którego klienci mogą uzyskać pomoc i obsługę techniczną dla aplikacji.|  
  
### <a name="application-options-tab"></a>Karta Opcje aplikacji  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Windows Presentation Foundation przeglądarki aplikacji**|Określa, czy jest uruchamiana w przeglądarce jako aplikacja przeglądarki XAML (XBAP) aplikacji WPF.|  
|**Użyj informacji zaufania manifestu aplikacji**|Określa, czy tego manifestu zawiera informacje o zaufania.|  
  
### <a name="files-tab"></a>Karta pliki  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Katalog aplikacji**|Katalog, w którym znajdują się pliki aplikacji. Użyj wielokropek (**...** ) przycisk, aby wybrać katalog.|  
|**Wypełnij**|Dodaje do manifestu aplikacji wszystkie pliki w katalogu aplikacji i jego podkatalogach. Jeśli MageUI.exe znajduje pojedynczy plik wykonywalny w katalogu, automatycznie oznacza to jako punkt wejścia, który jest wykonywany jako pierwszy, po uruchomieniu aplikacji ClickOnce na kliencie pliku.|  
|**Pliki aplikacji**|Wyświetla listę wszystkich plików w aplikacji. Każdy plik ma trzy edytowalne atrybuty omówiony poniżej.|  
|**Typ pliku**|Typ pliku może być jedna z cztery wartości:<br /><br /> -Brak.<br />— Punkt wejścia. Podstawowy plik wykonywalny aplikacji. Tylko jeden plik wykonywalny może być oznaczony jako punkt wejścia.<br />-Dane plików. Plik, takich jak plik XML, który dostarcza dane do aplikacji.<br />— Plik ikona. Na pulpicie lub w rogu okna aplikacji takich jak pojawi się ikona aplikacji.|  
|**Optional**|Pliki oznaczone jako opcjonalne nie zostaną pobrane na początkowej instalacji lub aktualizacji, ale może zostać pobrana w czasie wykonywania za pomocą interfejsu API System.Deployment na żądanie. Aby uzyskać więcej informacji, zobacz [wskazówki: Pobieranie zestawów na żądanie z ClickOnce wdrażania interfejsu API przy użyciu narzędzia Projektant](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer).|  
|**Grupy**|Etykieta dla zestawu plików opcjonalne. Można zastosować Etykieta grupy do zestawu plików i pobieranie plików przy użyciu jednego wywołania interfejsu API partii za pomocą interfejsu API na żądanie.|  
  
### <a name="permissions-required-tab"></a>Na karcie wymagane uprawnienia  
 Użyj **uprawnienia wymagane** karcie, aby oferować szerszy dostęp do komputera lokalnego, niż jest domyślnie przyznawane aplikacji. Aby uzyskać więcej informacji, zobacz [zabezpieczanie aplikacji ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Typ zestawu uprawnień**|Zestaw minimalne uprawnienia wymagane przez tę aplikację do uruchamiania na kliencie. Aby uzyskać opis tych zestawów uprawnień i uprawnienia, które ani nie wymagać, zobacz [NIB: ustawia uprawnienia o nazwie](http://msdn.microsoft.com/en-us/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).|  
|**Szczegóły**|Wartość XML utworzony dla manifest aplikacji do reprezentowania uprawnienia. Jeśli nie masz dobrą znajomość manifest aplikacji w formacie XML, nie należy edytować plik XML ręcznie. Aby uzyskać więcej informacji, zobacz [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest).|  
  
### <a name="deployment-manifest-tab"></a>Karta manifestu wdrożenia  
 **Manifest wdrażania** karta zawiera następujące karty.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Określa informacje identyfikacyjne dotyczące tego wdrożenia.|  
|**Opis**|Określa wydawcy, produktu i pomocy technicznej informacji.|  
|**Opcje wdrażania**|Określa dodatkowe informacje na temat wdrażania, takie jak typ aplikacji i lokalizacja początkowa.|  
|**Opcje aktualizacji**|Określa, jak często [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] ma sprawdzać dostępność aktualizacji aplikacji.|  
|**Odwołanie do aplikacji**|Określa manifest aplikacji dla tego wdrożenia.|  
  
### <a name="name-tab"></a>Karta nazw  
 **Nazwa** karta jest wyświetlana, gdy najpierw utworzyć lub otworzyć manifest wdrażania. Identyfikuje wdrożenia i opcjonalnie określa platformę prawidłowego elementu docelowego.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Wymagany. Nazwa manifestu rozmieszczenia. Zazwyczaj takie same jak nazwa pliku.|  
|**Wersja**|Wymagany. Numer wersji wdrożenia w formie *N.N.N.N*. Wymagany jest tylko pierwszy numer kompilacji głównych. Na przykład dla aplikacji w wersji 1.0, prawidłowe wartości to `1`, `1.0`, `1.0.0`, i `1.0.0.0`.|  
|**Procesor**|Opcjonalny. Architektura komputera, na którym można uruchomić tego wdrożenia. Wartość domyślna to `msil`, lub Microsoft język pośredni, domyślny format wszystkich zestawów zarządzanych. Zmień to pole, jeśli zostały skompilowane zestawy w aplikacji dla określonej architektury.|  
|**Kultury**|Opcjonalny. Kod kraju/regionu ISO dwuczęściową w którym ta aplikacja działa. Wartość domyślna to `neutral`.|  
|**Token klucza publicznego**|Opcjonalny. Klucz publiczny, z którą została podpisana tego manifestu wdrożenia. Jeśli jest to nowe lub unsigned manifestu, w tym polu pojawi się `Unsigned`.|  
  
### <a name="description-tab"></a>Opis elementu kartę  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Wydawcy**|Wymagany. Nazwa osoby lub organizacja odpowiadające dla aplikacji. Ta wartość jest używana jako nazwa folderu menu Start.|  
|**Produktu**|Wymagany. Pełna nazwa produktu. W przypadku wybrania **zainstalować lokalnie** dla **typu aplikacji** elementu na **opcje wdrażania** kartę, ta nazwa będzie wyświetlaną **Start** łącze menu i **Dodaj lub usuń programy** dla tej aplikacji.|  
|**Obsługa lokalizacji**|Opcjonalny. Adres URL, z którego klienci mogą uzyskać pomoc i obsługę techniczną dla aplikacji.|  
  
### <a name="deployment-options-tab"></a>Karta Opcje wdrażania  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Typ aplikacji**|Opcjonalny. Określa, czy ta aplikacja instaluje się na komputerze klienckim (**zainstalować lokalnie**), działa w trybie online (**Online tylko**), lub jest uruchamiana w przeglądarce aplikacji WPF (**przeglądarce WPF Aplikacja**). Wartość domyślna to **zainstalować lokalnie**.|  
|**Lokalizacja początkowa**|Opcjonalny. Adres URL, z którego powinien rzeczywiście uruchomienia aplikacji. Przydatne w przypadku wdrażania aplikacji z dysku CD, który należy zaktualizować się z sieci Web.|  
|**Należą: Lokalizacja Start (ProviderURL) w manifeście**|Opcjonalny. Określa adres URL, który [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] zbada aktualizacji aplikacji.|  
|**Automatycznie uruchamiania aplikacji po zainstalowaniu**|Wymagany. Określa, że [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] uruchamiania aplikacji natychmiast po wstępnej instalacji z adresu URL. Wartość domyślna to, że zaznaczone jest pole wyboru.|  
|**Zezwalaj na adres URL parametry do przekazania do aplikacji**|Wymagany. Umożliwia przekazanie danych parametru do [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] aplikacji za pomocą ciągu zapytania dołączone do adresu URL w manifeście rozmieszczenia. Wartość domyślna to, że pole wyboru jest wyczyszczone.|  
|**Użyj rozszerzenia pliku .deploy**|Wymagany. Po wybraniu wszystkich plików w manifeście aplikacji musi mieć rozszerzenie .deploy. Wartość domyślna to, że pole wyboru jest wyczyszczone.|  
  
### <a name="update-options-tab"></a>Karta Opcje aktualizacji  
 **Opcje aktualizacji** karta zawiera tylko opcje wymienione w tym miejscu po **typu aplikacji** pola wyboru na **nazwa** karta ma ustawioną wartość **zainstalowania lokalnie** .  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Ta aplikacja ma sprawdzać dostępność aktualizacji**|Określa, czy [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] ma sprawdzać dostępność aktualizacji aplikacji. Jeśli to pole wyboru nie jest zaznaczone, aplikacja nie będzie sprawdzać dostępność aktualizacji, jeśli nie można zaktualizować programowo przy użyciu interfejsów API w <xref:System.Deployment.Application> przestrzeni nazw.|  
|**Wybierz, kiedy aplikacja ma sprawdzać dostępność aktualizacji**|Udostępnia dwie opcje sprawdzania aktualizacji:<br /><br /> -   **Przed uruchomieniem aplikacji**. Sprawdzanie aktualizacji jest wykonywane przed wykonywania aplikacji.<br />-   **Po uruchomieniu aplikacji**. Sprawdzenie dostępności aktualizacji rozpoczyna się po formularz główny aplikacji został zainicjowany i zostanie uruchomiona przy następnym uruchomieniu aplikacji.|  
|**Częstotliwość sprawdzania aktualizacji**|Określa, jak często [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] ma sprawdzać dostępność aktualizacji:<br /><br /> -   **Sprawdź za każdym razem, gdy aplikacja zostanie uruchomiona**. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]zostanie przeprowadzone sprawdzanie aktualizacji, za każdym razem, gdy użytkownik otwiera aplikację.<br />-   **Sprawdź, co**: Wybierz przedział czasu i jednostka (godziny, dni lub tygodni), który musi upłynąć przed sprawdzania aktualizacji.|  
|**Określ minimalną wersję wymaganą dla tej aplikacji**|Opcjonalny. Określa, że określonej wersji aplikacji jest to Instalacja wymagana uniemożliwia użytkownikom pracy przy użyciu starszej wersji.|  
|**Wersja**|Jeśli wymagane **określ minimalną wersję wymaganą dla tej aplikacji** pole wyboru jest zaznaczone. Podany numer wersji musi mieć postać *N.N.N.N*. Wymagany jest tylko pierwszy numer kompilacji głównych. Na przykład dla aplikacji w wersji 1.0, prawidłowe wartości to `1`, `1.0`, `1.0.0`, i `1.0.0.0`.|  
  
### <a name="application-reference-tab"></a>Karta odwołania aplikacji  
 **Odwołania aplikacji** karta zawiera te same pola jako **nazwa** kartę opisem we wcześniejszej części tego tematu. Jedynym wyjątkiem jest następujące pole.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Wybierz manifestu**|Umożliwia wybór manifest aplikacji. Wszystkie pola na tej stronie są powielane po wybraniu manifest aplikacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)  
 [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)  
 [Mage.exe (narzędzie generowania manifestu i edytowania)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)
