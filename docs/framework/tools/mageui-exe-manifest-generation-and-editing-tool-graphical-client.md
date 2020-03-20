---
title: MageUI.exe (Narzędzie generowania i edytowania manifestu, klient grafiki)
ms.date: 03/30/2017
helpviewer_keywords:
- Manifest Generation and Editing tool
- MageUI.exe
ms.assetid: f9e130a6-8117-49c4-839c-c988f641dc14
ms.openlocfilehash: 7d09e1283be8ec75df89957e91f0d8411c125b3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74714459"
---
# <a name="mageuiexe-manifest-generation-and-editing-tool-graphical-client"></a>MageUI.exe (Narzędzie generowania i edytowania manifestu, klient grafiki)

MageUI.exe obsługuje takie same funkcje jak narzędzie wiersza polecenia Mage.exe, ale z interfejsem użytkownika systemu Windows (UI). Za pomocą tego narzędzia można tworzyć, edytować i podpisywać manifesty wdrażania i aplikacji. Nowe manifesty, które są tworzone za pomocą mageUI.exe docelowe .NET Framework 4 profil klienta. Poprzednie wersje MageUI.exe stosuje się do poprzednich wersji .NET Framework. Podczas dodawania lub usuwania zestawów z manifestu lub ponownego podpisywania istniejących manifestów program MageUI.exe nie aktualizuje manifestu do docelowego profilu klienta programu .NET Framework 4. Aby uzyskać więcej informacji, zobacz [Mage.exe (Manifest Generation and Editing Tool)](mage-exe-manifest-generation-and-editing-tool.md).

 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).

 Dwie wersje mage.exe i MageUI.exe są zawarte jako składnik programu Visual Studio. Aby wyświetlić informacje o wersji, uruchom plik MageUI.exe, wybierz **pozycję Pomoc**i wybierz pozycję **Informacje**. W tej dokumentacji opisano wersję 4.0.x.x programów Mage.exe i MageUI.exe.

> [!NOTE]
> Program MageUI.exe nie obsługuje elementu [compatibleFrameworks](/visualstudio/deployment/compatibleframeworks-element-clickonce-deployment) podczas zapisywania manifestu aplikacji, który został już podpisany certyfikatem przy użyciu pliku MageUI.exe. Zamiast tego należy użyć [mage.exe](mage-exe-manifest-generation-and-editing-tool.md).  
  
## <a name="uielement-list"></a>Lista elementów UI  
 W następującej tabeli wymieniono elementy menu i paski narzędzi, które są dostępne.  
  
|Polecenie|Menu|Skrót|Opis|  
|-------------|----------|--------------|-----------------|  
|**Manifest aplikacji**|**Plik, Nowy**||Tworzy nowy manifest aplikacji.|  
|**Manifest wdrażania**|**Plik, Nowy**||Tworzy nowy manifest wdrożenia.|  
|**Otwórz**|**Plik**|CTRL+O|Otwiera do edycji istniejący manifest wdrażania, manifest aplikacji lub licencję zaufania.|  
|**Zamknij**|**Plik**|CTRL+F4|Zamyka otwarty plik.<br /><br /> Jeśli modyfikujesz plik przed jego zamknięciem, MageUI.exe monituje o ponowne podpisywanie pliku kluczem publicznym, parą kluczy lub przechowywanym certyfikatem.|  
|**Zapisz**|**Plik**|CTRL+S|Zapisuje na dysku dokument, który aktualnie ma fokus wprowadzania użytkownika.|  
|**Zapisz jako**|**Plik**||Zapisuje plik na dysku, umożliwiając podanie nowej nazwy pliku i/lub lokalizacji.|  
|**Zapisz wszystko**|**Plik**||Zapisuje zmiany wprowadzone do wszystkich plików aktualnie otwartych w MageUI.exe.|  
|**Preferencje**|**Plik**||Otwiera okno **dialogowe Preferencje.** Aby uzyskać więcej informacji, zobacz następującą sekcję.|  
|**Wyjścia**|**Plik**|ALT+F4|Zamyka program MageUI.exe.|  
|**Cut**|**Edytuj**|CTRL+X|Usuwa zaznaczony tekst z aplikacji i przenosi je do Schowka systemu Windows.|  
|**Kopii**|**Edytuj**|CTRL+C|Kopiuje zaznaczony tekst do Schowka systemu Windows.|  
|**Wklej**|**Edytuj**|CTRL+V|Wkleja tekst ze Schowka systemu Windows do aktywnego elementu tekstu.|  
|**Usuwanie**|**Edytuj**||Usuwa element aktualnie zaznaczony na liście, taki jak licencja zaufania na karcie **Manifest wdrożenia.**|  
|**Zamknij wszystkie**|**Okno**||Zamyka wszystkie pliki otwarte w MageUI.exe. Jeżeli jeden lub więcej plików wymagają zapisania, MageUI.exe wyświetli monit o zapisanie ich. MageUI.exe również wyświetla monit o wybranie klucza podpisywania dla każdego niepodpisanego lub zmienionego pliku.|  
|**Informacje**|**Pomoc**||Wyświetla informacje o wersji i prawach autorskich dotyczące MageUI.exe.|  
  
## <a name="preferences-dialog-box"></a>Okno dialogowe Preferencje  
 Okno dialogowe **Preferencje** zawiera następujące elementy.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Zaloguj się zapisz**|Monituje o podpisanie pliku przy każdym zapisie modyfikacji.|  
|**Używanie domyślnego certyfikatu podpisywania**|Używa klucza wprowadzonego w polu **tekstowym Plik certyfikatu** do podpisywania wszystkich plików. Eliminuje to monit o podpisywanie, który zazwyczaj pojawia się po zapisaniu pliku i wybraniu opcji **Zapisz zaloguj.** Użyj przycisku wielokropek (**...**) obok pola tekstowego **Plik certyfikatu,** aby wybrać plik klucza.|  
|Algorytm porządkowania|Określa algorytm, za pomocą którego zostaną wygenerowane skróty zależności. Wartością musi być „sha256RSA” lub „sha1RSA”. Domyślną wartością jest SHA1. Używana zarówno w manifestach aplikacji, jak i wdrażania. Jeśli użytkownik poda certyfikat podczas zapisywania manifestu, używane są algorytmy w certyfikacie do wygenerowania rozkładów zależności.|  
  
## <a name="signing-options-dialog-box"></a>Okno dialogowe Opcje podpisywania  
 Okno dialogowe **Opcje podpisywania** jest wyświetlane po zapisaniu licencji manifestu lub zaufania po raz pierwszy lub po zmianie licencji manifestu lub zaufania. Jest on wyświetlany tylko wtedy, gdy w oknie dialogowym Preferencje jest **zaznaczona** opcja **Podpisywanie** na wartości. Podczas podpisywania manifestu określającego wartość w polu tekstowym **URI sygnatury czasowej** musi być nawiązywanie połączenia z Internetem.  
  
 To okno dialogowe zawiera następujące elementy.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Podpisz za pomocą pliku certyfikatu**|Podpisuje manifest certyfikatem cyfrowym przechowywanym w systemie plików.|  
|**Plik**|Zapewnia miejsce do wpisania ścieżki do pliku pfx reprezentującego certyfikat.|  
|**...**|Otwiera okno dialogowe **Wybieranie pliku** w celu wybrania istniejącego pliku pfx.|  
|**Nowy**|Generuje nowy pfx niesprawdzalny przez urząd certyfikacji (CA). Aby uzyskać więcej informacji na temat typów certyfikatów używanych do podpisywania wdrożeń ClickOnce, zobacz [Omówienie wdrażania zaufanych aplikacji](/visualstudio/deployment/trusted-application-deployment-overview).|  
|**Hasło**|Miejsce na wpisanie hasła używanego do podpisywania tym certyfikatem. Jeśli nie ma to zastosowania, może być puste.|  
|**Podpisz za pomocą zapisanego certyfikatu**|Wyświetla listę wyboru certyfikatów cyfrowych przechowywanych w magazynie certyfikatów na komputerze.|  
|**Identyfikator URI sygnatury czasowych**|Wyświetla identyfikator URI usługi sygnatur cyfrowych. Przypisanie do manifestu znacznika czasu zapobiega konieczności ponownego podpisania manifestu, jeśli certyfikat cyfrowy wygaśnie przed wdrożeniem następnej wersji aplikacji. Aby uzyskać więcej informacji, zobacz [Elementy członkowskie programu certyfikatów głównych systemu Windows](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) oraz [ClickOnce i Authenticode](/visualstudio/deployment/clickonce-and-authenticode).|  
|**Nie podpisuj**|Umożliwia zapisanie manifestu bez dodawania podpisu z certyfikatu cyfrowego.|  
  
## <a name="tab-and-panel-descriptions"></a>Opisy karta i panelu  
 Po otwarciu w programie MageUI.exe dokument pojawia się w obrębie własnej strony karty. Każda karta zawiera zestaw paneli właściwości. Panele zawierają zgrupowane podzbiory danych dokumentu.  
  
### <a name="application-manifest-tab"></a>Karta Manifest aplikacji  
 Karta **Manifest aplikacji** wyświetla zawartość manifestu aplikacji. Manifest aplikacji opisuje wszystkie pliki dołączone do wdrożenia i uprawnienia wymagane do uruchomienia aplikacji na kliencie.  
  
 Karta **Manifest aplikacji** zawiera następujące karty.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Określa informacje identyfikujące to wdrożenie.|  
|**Opis**|Określa informacje o wydawcy, produkcie i pomocy technicznej.|  
|**Opcje aplikacji**|Określa, czy jest to aplikacja przeglądarki i czy ten manifest jest źródłem informacji o zaufaniu.|  
|**Pliki**|Określa wszystkie pliki, które stanowią to wdrożenie.|  
|**Wymagane uprawnienia**|Określa minimalny zestaw uprawnień wymaganych przez aplikację do uruchamiania na kliencie.|  
  
### <a name="name-tab"></a>Karta Nazwa  
 Karta **Nazwa** jest wyświetlana podczas pierwszego tworzenia lub otwierania manifestu aplikacji. Jednoznacznie identyfikuje wdrożenie i opcjonalnie określa prawidłową platformę docelową.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Wymagany. Nazwa manifestu aplikacji. Zwykle taka sama jak nazwa pliku.|  
|**Wersja**|Wymagany. Numer wersji wdrożenia w formularzu *N.N.N.N*. Wymagany jest tylko pierwszy numer kompilacji głównej. Na przykład dla wersji 1.0 aplikacji prawidłowe `1` `1.0`wartości `1.0.0`będą `1.0.0.0`zawierać , , i .|  
|**Procesor**|Element opcjonalny. Architektura komputera, na którym można uruchomić to wdrożenie. Wartością `msil`domyślną jest język pośredni firmy Microsoft lub Microsoft Intermediate Language, który jest domyślnym formatem wszystkich zestawów zarządzanych. Zmień to pole, jeśli zestawy w aplikacji zostały wstępnie skompilowane dla określonej architektury. Aby uzyskać więcej informacji na temat wstępnej kompilacji, zobacz [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md).|  
|**Kultury**|Element opcjonalny. Dwuczęściowy kod kraju i regionu ISO, w którym działa ta aplikacja. Wartość domyślna to `neutral`.|  
|**Token klucza publicznego**|Element opcjonalny. Klucz publiczny, z którym ten manifest aplikacji został podpisany. Jeśli jest to nowy lub niepodpisany manifest, to pole będzie wyświetlane jako `Unsigned`.|  
  
### <a name="description-tab"></a>Karta Opis  
 Te informacje są zwykle dostarczane w manifeście wdrażania. Te pola można zmodyfikować tylko wtedy, gdy pole wyboru **Użyj informacji zaufania manifestu aplikacji** jest zaznaczone na karcie Opcje **aplikacji.**  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Wydawca**|Imię i nazwisko osoby lub organizacji odpowiedzialnej za aplikację. Ta wartość jest używana jako nazwa folderu menu Start.|  
|**Product (Produkt)**|Pełna nazwa produktu. Jeśli na karcie Opcje wdrażania wybrano opcję **Zainstaluj lokalnie** dla elementu **Typ aplikacji** na karcie **Opcje wdrażania** manifestu wdrażania, będzie to nazwa wyświetlana w łączu menu **Start** oraz w obszarze Dodaj lub **usuń programy** dla tej aplikacji.|  
|**Lokalizacja pomocy technicznej**|Adres URL, z którego klienci mogą uzyskać pomoc i obsługę aplikacji.|  
  
### <a name="application-options-tab"></a>Karta Opcje aplikacji  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Aplikacja przeglądarki Fundacji prezentacji systemu Windows**|Określa, czy jest to aplikacja WPF, która działa w przeglądarce jako aplikacja przeglądarki XAML (XBAP).|  
|**Korzystanie z informacji o zaufaniu manifestu aplikacji**|Określa, czy ten manifest zawiera informacje o zaufaniu.|  
  
### <a name="files-tab"></a>Karta Pliki  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Katalog aplikacji**|Katalog, w którym znajdują się pliki aplikacji. Użyj przycisku elipsy (**...**), aby wybrać katalog.|  
|**Wypełnić**|Dodaje wszystkie pliki w katalogu aplikacji i podkatalogach do manifestu aplikacji. Jeśli program MageUI.exe znajdzie pojedynczy plik wykonywalny w katalogu, automatycznie oznaczy to jako punkt wejścia, który jest plikiem po raz pierwszy wykonanym po uruchomieniu aplikacji ClickOnce na kliencie.|  
|**Pliki aplikacji**|Wyświetla listę wszystkich plików w aplikacji. Każdy plik ma trzy edytowalne atrybuty, omówione poniżej.|  
|**Typ pliku**|Typ pliku może być jedną z czterech wartości:<br /><br /> - Brak.<br />- Punkt wejścia. Podstawowy plik wykonywalny aplikacji. Jako punkt wejścia można oznaczyć tylko jeden plik wykonywalny.<br />- Plik danych. Plik, taki jak plik XML, który dostarcza dane do aplikacji.<br />- Plik ikony. Ikona aplikacji, na przykład, pojawia się na pulpicie lub w rogu okna aplikacji.|  
|**Opcjonalne**|Pliki oznaczone jako opcjonalne nie są pobierane podczas wstępnej instalacji lub aktualizacji, ale mogą zostać pobrane w czasie wykonywania za pomocą interfejsu API System.Deployment On-Demand. Aby uzyskać więcej informacji, zobacz [Przewodnik: Pobieranie zestawów na żądanie za pomocą interfejsu API wdrażania ClickOnce przy użyciu projektanta](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer).|  
|**Grupa**|Etykieta dla zestawu plików opcjonalnych. Etykietę grupy można zastosować do zestawu plików i użyć interfejsu API na żądanie, aby pobrać partię plików za pomocą jednego wywołania interfejsu API.|  
  
### <a name="permissions-required-tab"></a>Karta Wymagane uprawnienia  
 Użyj **uprawnienia wymagane** kartę, jeśli trzeba udzielić aplikacji większy dostęp do komputera lokalnego niż jest przyznawana domyślnie. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie aplikacji ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Typ zestawu uprawnień**|Minimalny zestaw uprawnień wymaganych przez tę aplikację do uruchomienia na kliencie. Aby uzyskać opis tych zestawów uprawnień i uprawnienia, które robią lub nie wymagają, zobacz [Nazwane zestawy uprawnień](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).|  
|**Szczegóły**|XML utworzony dla manifestu aplikacji do reprezentowania zestawu uprawnień. Jeśli nie masz dobrego zrozumienia formatu XML manifestu aplikacji, nie należy edytować tego xml ręcznie. Aby uzyskać więcej informacji, zobacz [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest).|  
  
### <a name="deployment-manifest-tab"></a>Karta Manifest wdrożenia  
 Karta **Manifest wdrażania** zawiera następujące karty.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Określa informacje identyfikujące to wdrożenie.|  
|**Opis**|Określa informacje o wydawcy, produkcie i pomocy technicznej.|  
|**Opcje wdrażania**|Określa dodatkowe informacje o wdrożeniu, takie jak typ aplikacji i lokalizacja początkowa.|  
|**Opcje aktualizacji**|Określa, jak często ClickOnce należy sprawdzić dostępność aktualizacji aplikacji.|  
|**Odwołanie do aplikacji**|Określa manifest aplikacji dla tego wdrożenia.|  
  
### <a name="name-tab"></a>Karta Nazwa  
 Karta **Nazwa** jest wyświetlana podczas pierwszego tworzenia lub otwierania manifestu wdrożenia. Jednoznacznie identyfikuje wdrożenie i opcjonalnie określa prawidłową platformę docelową.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Wymagany. Nazwa manifestu wdrażania. Zwykle taka sama jak nazwa pliku.|  
|**Wersja**|Wymagany. Numer wersji wdrożenia w formularzu *N.N.N.N*. Wymagany jest tylko pierwszy numer kompilacji głównej. Na przykład dla wersji 1.0 aplikacji prawidłowe `1` `1.0`wartości `1.0.0`będą `1.0.0.0`zawierać , , i .|  
|**Procesor**|Element opcjonalny. Architektura komputera, na którym można uruchomić to wdrożenie. Wartość domyślna to `msil`, lub Microsoft Intermediate Language, domyślny format wszystkich zarządzanych zestawów. Zmień to pole, jeśli skompilowano zestawy w aplikacji dla określonej architektury.|  
|**Kultury**|Element opcjonalny. Dwuczęściowy kod kraju/regionu ISO, w którym działa ta aplikacja. Wartość domyślna to `neutral`.|  
|**Token klucza publicznego**|Element opcjonalny. Klucz publiczny, z którym ten manifest wdrożenia został podpisany. Jeśli jest to nowy lub niepodpisany manifest, to pole będzie wyświetlane jako `Unsigned`.|  
  
### <a name="description-tab"></a>Karta Opis  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Wydawca**|Wymagany. Imię i nazwisko osoby lub organizacji odpowiedzialnej za aplikację. Ta wartość jest używana jako nazwa folderu menu Start.|  
|**Product (Produkt)**|Wymagany. Pełna nazwa produktu. Jeśli na karcie **Opcje wdrażania** **wybrano** opcję Zainstaluj lokalnie dla elementu Typ **aplikacji,** będzie to nazwa wyświetlana w łączu menu **Start** oraz w obszarze Dodaj lub **usuń programy** dla tej aplikacji.|  
|**Lokalizacja pomocy technicznej**|Element opcjonalny. Adres URL, z którego klienci mogą uzyskać pomoc i obsługę aplikacji.|  
  
### <a name="deployment-options-tab"></a>Karta Opcje wdrażania  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Typ aplikacji**|Element opcjonalny. Określa, czy ta aplikacja instaluje się na komputerze klienckim **(Zainstaluj lokalnie),** działa w trybie online **(Tylko w trybie online),** czy jest aplikacją WPF, która działa w przeglądarce (**WPF Browser Application**). Wartość domyślna to **Zainstaluj lokalnie**.|  
|**Lokalizacja początkowa**|Element opcjonalny. Adres URL, z którego aplikacja powinna być faktycznie uruchomiona. Przydatne podczas wdrażania aplikacji z dysku CD, który powinien aktualizować się z sieci Web.|  
|**Uwzględnij lokalizację początkową (ProviderURL) w manifeście**|Element opcjonalny. Określa adres URL, pod którym technologia ClickOnce będzie szukać aktualizacji aplikacji.|  
|**Automatyczne uruchamianie aplikacji po zainstalowaniu**|Wymagany. Określa, że aplikacja ClickOnce powinna być uruchamiana natychmiast po początkowej instalacji z adresu URL. Domyślnie zaznaczone jest pole wyboru.|  
|**Zezwalaj na przekazywanie parametrów adresu URL do aplikacji**|Wymagany. Umożliwia przesyłanie danych parametrów do aplikacji ClickOnce za pośrednictwem ciągu zapytania dołączonego do adresu URL manifestu wdrożenia. Domyślnie pole wyboru jest wyczyszczone.|  
|**Używanie rozszerzenia pliku .deploy**|Wymagany. Po wybraniu tej opcji wszystkie pliki w manifeście aplikacji muszą mieć rozszerzenie .deploy. Domyślnie pole wyboru jest wyczyszczone.|  
  
### <a name="update-options-tab"></a>Karta Opcje aktualizacji  
 Karta **Opcje aktualizacji** zawiera tylko opcje wymienione w tym miejscu, gdy pole wyboru Typ **aplikacji** na karcie **Nazwa** jest ustawione na **Instalowanie lokalnie**.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Ta aplikacja powinna sprawdzić dostępność aktualizacji**|Określa, czy ClickOnce powinien sprawdzać dostępność aktualizacji aplikacji. Jeśli to pole wyboru nie jest zaznaczone, aplikacja nie będzie sprawdzać dostępności aktualizacji, <xref:System.Deployment.Application> chyba że zaktualizujesz go programowo przy użyciu interfejsów API w obszarze nazw.|  
|**Wybierz, kiedy aplikacja powinna sprawdzić dostępność aktualizacji**|Udostępnia dwie opcje sprawdzania aktualizacji:<br /><br /> -   **Przed uruchomieniem aplikacji**. Sprawdzanie aktualizacji jest wykonywane przed wykonaniem aplikacji.<br />-   **Po uruchomieniu aplikacji**. Sprawdzanie aktualizacji rozpoczyna się po zainicjowaniu głównego formularza aplikacji i zostanie uruchomione przy następnym uruchomieniu aplikacji.|  
|**Częstotliwość sprawdzania aktualizacji**|Określa, jak często ClickOnce należy sprawdzić dostępność aktualizacji:<br /><br /> -   **Sprawdzaj za każdym razem, gdy aplikacja jest uruchamiana**. ClickOnce wykona sprawdzanie aktualizacji za każdym razem, gdy użytkownik otworzy aplikację.<br />-   **Sprawdź co**: Wybierz przedział czasu i jednostkę (godziny, dni lub tygodnie), które muszą uginieć się przed sprawdzeniem dostępności aktualizacji.|  
|**Określ minimalną wymaganą wersję dla tej aplikacji**|Element opcjonalny. Określa, że określona wersja aplikacji jest wymaganą instalacją, uniemożliwiając użytkownikom pracę z wcześniejszą wersją.|  
|**Wersja**|Wymagane, **jeśli zaznaczono pole wyboru Określ minimalną wymaganą wersję dla tej aplikacji.** The version number supplied must be of the form *N.N.N.N*. Wymagany jest tylko pierwszy numer kompilacji głównej. Na przykład dla wersji 1.0 aplikacji prawidłowe `1` `1.0`wartości `1.0.0`będą `1.0.0.0`zawierać , , i .|  
  
### <a name="application-reference-tab"></a>Karta Odwołanie do aplikacji  
 Karta **Odwołanie do aplikacji** zawiera te same pola, co karta **Nazwa** opisana wcześniej w tym temacie. Jedynym wyjątkiem jest następujące pole.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Wybierz manifest**|Umożliwia wybranie manifestu aplikacji. Wszystkie inne pola na tej stronie zostaną wypełnione po wybraniu manifestu aplikacji.|  
  
## <a name="see-also"></a>Zobacz też

- [Kliknijonce zabezpieczenia i wdrażanie](/visualstudio/deployment/clickonce-security-and-deployment)
- [Wskazówki: ręczne wdrażanie aplikacji ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Mage.exe (narzędzie generowania manifestu i edytowania)](mage-exe-manifest-generation-and-editing-tool.md)
