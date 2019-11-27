---
title: MageUI.exe (Narzędzie generowania i edytowania manifestu, klient grafiki)
ms.date: 03/30/2017
helpviewer_keywords:
- Manifest Generation and Editing tool
- MageUI.exe
ms.assetid: f9e130a6-8117-49c4-839c-c988f641dc14
ms.openlocfilehash: 99f522181232d16b9913ba3c55f34274b75d8966
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449414"
---
# <a name="mageuiexe-manifest-generation-and-editing-tool-graphical-client"></a>MageUI.exe (Narzędzie generowania i edytowania manifestu, klient grafiki)

MageUI.exe obsługuje takie same funkcje jak narzędzie wiersza polecenia Mage.exe, ale z interfejsem użytkownika systemu Windows (UI). Za pomocą tego narzędzia można tworzyć, edytować i podpisywać manifesty wdrażania i aplikacji. Nowe manifesty, które są tworzone za pomocą MageUI. exe, są przeznaczone dla [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Poprzednie wersje MageUI.exe stosuje się do poprzednich wersji .NET Framework. W przypadku dodawania lub usuwania zestawów z manifestu lub ponownego podpisywania istniejących manifestów MageUI. exe nie aktualizuje manifestu do celu [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Aby uzyskać więcej informacji, zobacz [plik Mage. exe (narzędzie tworzenia i edycji manifestów)](mage-exe-manifest-generation-and-editing-tool.md).

 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).

 Dwie wersje programu Mage. exe i MageUI. exe są dołączone jako składnik programu Visual Studio. Aby wyświetlić informacje o wersji, uruchom program MageUI. exe, wybierz pozycję **Pomoc**, a następnie wybierz pozycję **About (informacje**). W tej dokumentacji opisano wersję 4.0.x.x programów Mage.exe i MageUI.exe.

> [!NOTE]
> MageUI. exe nie obsługuje elementu [compatibleFrameworks](/visualstudio/deployment/compatibleframeworks-element-clickonce-deployment) podczas zapisywania manifestu aplikacji, który został już podpisany za pomocą certyfikatu przy użyciu MageUI. exe. Zamiast tego należy użyć programu [Mage. exe](mage-exe-manifest-generation-and-editing-tool.md).  
  
## <a name="uielement-list"></a>Lista elementów interfejsu  
 W następującej tabeli wymieniono elementy menu i paski narzędzi, które są dostępne.  
  
|Polecenie|Menu|Skrót|Opis|  
|-------------|----------|--------------|-----------------|  
|**Manifest aplikacji**|**Plik, nowy**||Tworzy nowy manifest aplikacji.|  
|**Manifest wdrożenia**|**Plik, nowy**||Tworzy nowy manifest wdrożenia.|  
|**Otwórz**|**Rozszerzeniem**|CTRL+O|Otwiera do edycji istniejący manifest wdrażania, manifest aplikacji lub licencję zaufania.|  
|**Ściśle**|**Rozszerzeniem**|CTRL+F4|Zamyka otwarty plik.<br /><br /> Jeśli modyfikujesz plik przed jego zamknięciem, MageUI.exe monituje o ponowne podpisywanie pliku kluczem publicznym, parą kluczy lub przechowywanym certyfikatem.|  
|**Pisał**|**Rozszerzeniem**|CTRL+S|Zapisuje na dysku dokument, który aktualnie ma fokus wprowadzania użytkownika.|  
|**Zapisz jako**|**Rozszerzeniem**||Zapisuje plik na dysku, umożliwiając podanie nowej nazwy pliku i/lub lokalizacji.|  
|**Zapisz wszystko**|**Rozszerzeniem**||Zapisuje zmiany wprowadzone do wszystkich plików aktualnie otwartych w MageUI.exe.|  
|**Preferencje**|**Rozszerzeniem**||Otwiera okno dialogowe **Preferencje** . Aby uzyskać więcej informacji, zobacz następującą sekcję.|  
|**Zakończ**|**Rozszerzeniem**|ALT+F4|Zamyka program MageUI.exe.|  
|**Wklejony**|**Edytowanie**|CTRL+X|Usuwa zaznaczony tekst z aplikacji i przenosi je do Schowka systemu Windows.|  
|**Kopiuj**|**Edytowanie**|CTRL+C|Kopiuje zaznaczony tekst do Schowka systemu Windows.|  
|**Wklej**|**Edytowanie**|CTRL+V|Wkleja tekst ze Schowka systemu Windows do aktywnego elementu tekstu.|  
|**Usuwanie**|**Edytowanie**||Usuwa element aktualnie wybrany na liście, na przykład licencji zaufania na karcie **manifest wdrożenia** .|  
|**Zamknij wszystko**|**Dział**||Zamyka wszystkie pliki otwarte w MageUI.exe. Jeżeli jeden lub więcej plików wymagają zapisania, MageUI.exe wyświetli monit o zapisanie ich. MageUI.exe również wyświetla monit o wybranie klucza podpisywania dla każdego niepodpisanego lub zmienionego pliku.|  
|**O**|**Pomoc**||Wyświetla informacje o wersji i prawach autorskich dotyczące MageUI.exe.|  
  
## <a name="preferences-dialog-box"></a>Okno dialogowe Preferencje  
 Okno dialogowe **Preferencje** zawiera następujące elementy.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Zapisz przy zapisywaniu**|Monituje o podpisanie pliku przy każdym zapisie modyfikacji.|  
|**Użyj domyślnego certyfikatu podpisywania**|Używa klucza wprowadzonego w polu tekstowym **plik certyfikatu** do podpisywania wszystkich plików. Eliminuje to monit podpisywania, który zwykle pojawia się po zapisaniu pliku i wybraniu polecenia **Zaloguj przy zapisywaniu** . Użyj przycisku wielokropka ( **...** ) obok pola tekstowego **plik certyfikatu** , aby wybrać plik klucza.|  
|Algorytm porządkowania|Określa algorytm, za pomocą którego zostaną wygenerowane skróty zależności. Wartością musi być „sha256RSA” lub „sha1RSA”. Domyślną wartością jest SHA1. Używana zarówno w manifestach aplikacji, jak i wdrażania. Jeśli użytkownik poda certyfikat podczas zapisywania manifestu, używane są algorytmy w certyfikacie do wygenerowania rozkładów zależności.|  
  
## <a name="signing-options-dialog-box"></a>Okno dialogowe Opcje podpisywania  
 Okno dialogowe **Opcje podpisywania** pojawia się, gdy po raz pierwszy zapisujesz manifest lub licencję zaufania, lub jeśli zmienisz manifest lub licencję zaufania. Pojawia się tylko wtedy, gdy zaznaczono opcję **Zaloguj się przy zapisywaniu** w oknie dialogowym **Preferencje** . Musisz mieć połączenie z Internetem podczas podpisywania manifestu, który określa wartość w polu tekstowym **Identyfikator URI sygnatury czasowej** .  
  
 To okno dialogowe zawiera następujące elementy.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Podpisz przy użyciu pliku certyfikatu**|Podpisuje manifest certyfikatem cyfrowym przechowywanym w systemie plików.|  
|**Rozszerzeniem**|Zapewnia miejsce do wpisania ścieżki do pliku pfx reprezentującego certyfikat.|  
|**...**|Otwiera okno dialogowe **Wybierz plik** , w którym można wybrać istniejący plik PFX.|  
|**Nowy**|Generuje nowy pfx niesprawdzalny przez urząd certyfikacji (CA). Aby uzyskać więcej informacji na temat typów certyfikatów używanych do podpisywania wdrożeń ClickOnce, zobacz [Omówienie wdrażania zaufanych aplikacji](/visualstudio/deployment/trusted-application-deployment-overview).|  
|**Hasło**|Miejsce na wpisanie hasła używanego do podpisywania tym certyfikatem. Jeśli nie ma to zastosowania, może być puste.|  
|**Podpisz z zapisanym certyfikatem**|Wyświetla listę wyboru certyfikatów cyfrowych przechowywanych w magazynie certyfikatów na komputerze.|  
|**Identyfikator URI sygnatury czasowej**|Wyświetla identyfikator URI usługi sygnatur cyfrowych. Przypisanie do manifestu znacznika czasu zapobiega konieczności ponownego podpisania manifestu, jeśli certyfikat cyfrowy wygaśnie przed wdrożeniem następnej wersji aplikacji. Aby uzyskać więcej informacji, zobacz [Członkowie programu certyfikatów głównych systemu Windows](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) oraz [ClickOnce i Authenticode](/visualstudio/deployment/clickonce-and-authenticode).|  
|**Nie pisz**|Umożliwia zapisanie manifestu bez dodawania podpisu z certyfikatu cyfrowego.|  
  
## <a name="tab-and-panel-descriptions"></a>Opisy karta i panelu  
 Po otwarciu w programie MageUI.exe dokument pojawia się w obrębie własnej strony karty. Każda karta zawiera zestaw paneli właściwości. Panele zawierają zgrupowane podzbiory danych dokumentu.  
  
### <a name="application-manifest-tab"></a>Karta manifest aplikacji  
 Na karcie **manifest aplikacji** jest wyświetlana zawartość manifestu aplikacji. Manifest aplikacji opisuje wszystkie pliki dołączone do wdrożenia oraz uprawnienia wymagane do uruchomienia aplikacji na kliencie programu.  
  
 Karta **manifest aplikacji** zawiera następujące karty.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Określa identyfikację informacji o tym wdrożeniu.|  
|**Opis**|Określa informacje o wydawcy, produkcie i pomocy technicznej.|  
|**Opcje aplikacji**|Określa, czy jest to aplikacja przeglądarki i czy ten manifest jest źródłem informacji zaufania.|  
|**Pliki**|Określa wszystkie pliki stanowiące to wdrożenie.|  
|**Wymagane uprawnienia**|Określa minimalny zestaw uprawnień wymagany przez aplikację do uruchomienia na kliencie.|  
  
### <a name="name-tab"></a>Nazwa — karta  
 Karta **Nazwa** jest wyświetlana podczas pierwszej tworzenia lub otwierania manifestu aplikacji. Jednoznacznie identyfikuje wdrożenie i opcjonalnie określa prawidłową platformę docelową.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Wymagana. Nazwa manifestu aplikacji. Zwykle taka sama jak nazwa pliku.|  
|**Wersja**|Wymagana. Numer wersji wdrożenia w postaci *N. n. n. n*. Wymagany jest tylko pierwszy główny numer kompilacji. Na przykład w przypadku wersji 1,0 aplikacji prawidłowe wartości mogą obejmować `1`, `1.0`, `1.0.0`i `1.0.0.0`.|  
|**Extreme**|Opcjonalna. Architektura komputera, na którym można uruchomić to wdrożenie. Wartość domyślna to `msil`lub języka pośredniego firmy Microsoft, który jest domyślnym formatem wszystkich zestawów zarządzanych. Zmień to pole, jeśli wstępnie skompilowano zestawy w aplikacji dla określonej architektury. Aby uzyskać więcej informacji na temat wstępnej kompilacji, zobacz [Ngen. exe (Generator obrazu natywnego)](ngen-exe-native-image-generator.md).|  
|**Dziedzinie**|Opcjonalna. Dwuczęściowy kod kraju i regionu ISO, w którym działa ta aplikacja. Wartość domyślna to `neutral`.|  
|**Token klucza publicznego**|Opcjonalna. Klucz publiczny, z którym jest podpisany ten manifest aplikacji. Jeśli jest to nowy lub niepodpisany manifest, to pole będzie wyświetlane jako `Unsigned`.|  
  
### <a name="description-tab"></a>Karta opis  
 Te informacje są zwykle dostępne w manifeście wdrożenia. Te pola można modyfikować tylko wtedy, gdy na karcie **Opcje aplikacji** jest zaznaczone pole wyboru **Użyj informacji o zaufaniu manifestu aplikacji** .  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Dawc**|Nazwisko osoby lub organizacji odpowiedzialnej za aplikację. Ta wartość jest używana jako nazwa folderu menu Start.|  
|**Iloczyn**|Pełna nazwa produktu. Jeśli wybrano opcję **Zainstaluj lokalnie** dla **elementu Typ aplikacji** na karcie **Opcje wdrożenia** w manifeście wdrożenia, ta nazwa będzie wyświetlana w linku menu **Start** i w **aplecie Dodaj lub usuń programy** dla tej aplikacji.|  
|**Lokalizacja obsługi**|Adres URL, z którego klienci mogą uzyskać pomoc i obsługę aplikacji.|  
  
### <a name="application-options-tab"></a>Karta Opcje aplikacji  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Aplikacja przeglądarki Windows Presentation Foundation**|Określa, czy jest to aplikacja WPF działająca w przeglądarce jako aplikacja przeglądarki XAML (XBAP).|  
|**Użyj informacji o zaufaniu manifestu aplikacji**|Określa, czy ten manifest zawiera informacje zaufania.|  
  
### <a name="files-tab"></a>Karta Pliki  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Katalog aplikacji**|Katalog, w którym znajdują się pliki aplikacji. Użyj przycisku wielokropka ( **...** ), aby wybrać katalog.|  
|**Wypełniono**|Dodaje wszystkie pliki w katalogu aplikacji i podkatalogach do manifestu aplikacji. Jeśli MageUI. exe odnajdzie pojedynczy plik wykonywalny w katalogu, automatycznie oznacza to jako punkt wejścia, który jest pierwszy wykonywany, gdy aplikacja ClickOnce zostanie uruchomiona na kliencie.|  
|**Pliki aplikacji**|Wyświetla listę wszystkich plików w aplikacji. Każdy plik ma trzy atrybuty edytowalne opisane poniżej.|  
|**Typ pliku**|Typ pliku może być jedną z czterech wartości:<br /><br /> Dawaj.<br />-   Entry Point. Podstawowy plik wykonywalny aplikacji. Tylko jeden plik wykonywalny może być oznaczony jako punkt wejścia.<br />— Plik danych. Plik, taki jak plik XML, który dostarcza dane do aplikacji.<br />— Plik ikony. Ikona aplikacji, na przykład pojawia się na pulpicie lub w rogu okna aplikacji.|  
|**Optional**|Pliki oznaczone jako opcjonalne nie są pobierane podczas początkowej instalacji lub aktualizacji, ale mogą być pobierane w czasie wykonywania za pomocą interfejsu API System. Deployment na żądanie. Aby uzyskać więcej informacji, zobacz [Przewodnik: pobieranie zestawów na żądanie za pomocą interfejsu API wdrażania ClickOnce przy użyciu narzędzia Projektant](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer).|  
|**Group**|Etykieta zestawu opcjonalnych plików. Możesz zastosować etykietę grupy do zestawu plików i użyć interfejsu API na żądanie, aby pobrać partię plików z pojedynczym wywołaniem interfejsu API.|  
  
### <a name="permissions-required-tab"></a>Karta wymagane uprawnienia  
 Użyj karty **wymagane uprawnienia** , jeśli chcesz udzielić aplikacji więcej dostępu do komputera lokalnego, niż jest on domyślnie przyznany. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie aplikacji ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Typ zestawu uprawnień**|Minimalny zestaw uprawnień wymagany przez tę aplikację do uruchomienia na kliencie. Aby uzyskać opis tych zestawów uprawnień i uprawnień, które wykonują lub nie wymagają żądania, zobacz [nazwane zestawy uprawnień](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).|  
|**Uzyskać**|KOD XML utworzony dla manifestu aplikacji reprezentujący zestaw uprawnień. Jeśli nie znasz dobrego formatu XML manifestu aplikacji, nie należy edytować tego kodu XML ręcznie. Aby uzyskać więcej informacji, zobacz [manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest).|  
  
### <a name="deployment-manifest-tab"></a>Karta manifest wdrożenia  
 Karta **manifest wdrożenia** zawiera następujące karty.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Określa identyfikację informacji o tym wdrożeniu.|  
|**Opis**|Określa informacje o wydawcy, produkcie i pomocy technicznej.|  
|**Opcje wdrażania**|Określa dodatkowe informacje dotyczące wdrożenia, na przykład typ aplikacji i lokalizację początkową.|  
|**Opcje aktualizacji**|Określa, jak często ClickOnce powinna sprawdzać dostępność aktualizacji aplikacji.|  
|**Odwołanie do aplikacji**|Określa manifest aplikacji dla tego wdrożenia.|  
  
### <a name="name-tab"></a>Nazwa — karta  
 Karta **Nazwa** jest wyświetlana podczas pierwszego tworzenia lub otwierania manifestu wdrożenia. Jednoznacznie identyfikuje wdrożenie i opcjonalnie określa prawidłową platformę docelową.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Wymagana. Nazwa manifestu wdrożenia. Zwykle taka sama jak nazwa pliku.|  
|**Wersja**|Wymagana. Numer wersji wdrożenia w postaci *N. n. n. n*. Wymagany jest tylko pierwszy główny numer kompilacji. Na przykład w przypadku wersji 1,0 aplikacji prawidłowe wartości mogą obejmować `1`, `1.0`, `1.0.0`i `1.0.0.0`.|  
|**Extreme**|Opcjonalna. Architektura komputera, na którym można uruchomić to wdrożenie. Wartość domyślna to `msil`lub języka pośredniego firmy Microsoft, domyślnego formatu wszystkich zarządzanych zestawów. Zmień to pole, jeśli zestawy w aplikacji zostały skompilowane dla określonej architektury.|  
|**Dziedzinie**|Opcjonalna. Dwuczęściowy kod kraju/regionu ISO, w którym działa ta aplikacja. Wartość domyślna to `neutral`.|  
|**Token klucza publicznego**|Opcjonalna. Klucz publiczny, z którym został podpisany ten manifest wdrożenia. Jeśli jest to nowy lub niepodpisany manifest, to pole będzie wyświetlane jako `Unsigned`.|  
  
### <a name="description-tab"></a>Karta opis  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Dawc**|Wymagana. Nazwisko osoby lub organizacji odpowiedzialnej za aplikację. Ta wartość jest używana jako nazwa folderu menu Start.|  
|**Iloczyn**|Wymagana. Pełna nazwa produktu. Jeśli wybrano opcję **Zainstaluj lokalnie** dla **elementu Typ aplikacji** na karcie **Opcje wdrożenia** , ta nazwa będzie wyświetlana w linku menu **Start** i w **aplecie Dodaj lub usuń programy** dla tej aplikacji.|  
|**Lokalizacja obsługi**|Opcjonalna. Adres URL, z którego klienci mogą uzyskać pomoc i obsługę aplikacji.|  
  
### <a name="deployment-options-tab"></a>Karta opcje wdrożenia  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Typ aplikacji**|Opcjonalna. Określa, czy ta aplikacja jest instalowana na komputerze klienckim (**Instalacja lokalna**), działa w trybie online (**tylko w trybie online**), czy też jest aplikacją WPF działającą w przeglądarce (**Aplikacja przeglądarki WPF**). Wartość domyślna to **Instaluj lokalnie**.|  
|**Lokalizacja początkowa**|Opcjonalna. Adres URL, z którego aplikacja ma zostać faktycznie uruchomiona. Przydatne podczas wdrażania aplikacji z dysku CD, który powinien zostać zaktualizowany z sieci Web.|  
|**Uwzględnij lokalizację początkową (ProviderURL) w manifeście**|Opcjonalna. Określa adres URL, pod którym technologia ClickOnce będzie szukać aktualizacji aplikacji.|  
|**Automatycznie uruchamiaj aplikację po zainstalowaniu**|Wymagana. Określa, że aplikacja ClickOnce powinna być uruchamiana natychmiast po początkowej instalacji z adresu URL. Wartość domyślna to pole wyboru jest zaznaczone.|  
|**Zezwalaj na przekazywanie parametrów adresu URL do aplikacji**|Wymagana. Zezwala na przesyłanie danych parametrów do aplikacji ClickOnce za pomocą ciągu zapytania dołączonego do adresu URL manifestu wdrożenia. Wartość domyślna to pole wyboru jest wyczyszczone.|  
|**Użyj rozszerzenia pliku. deploy**|Wymagana. Po wybraniu tej opcję wszystkie pliki w manifeście aplikacji muszą mieć rozszerzenie. deploy. Wartość domyślna to pole wyboru jest wyczyszczone.|  
  
### <a name="update-options-tab"></a>Karta Opcje aktualizacji  
 Karta **Opcje aktualizacji** zawiera opcje wymienione tutaj, gdy pole wyboru **Typ aplikacji** na karcie **Nazwa** jest ustawione na **Instaluj lokalnie**.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Ta aplikacja powinna sprawdzać dostępność aktualizacji**|Określa, czy technologia ClickOnce ma sprawdzać dostępność aktualizacji aplikacji. Jeśli to pole wyboru nie jest zaznaczone, aplikacja nie będzie sprawdzać dostępności aktualizacji, o ile nie zostanie ona zaktualizowana programowo przy użyciu interfejsów API w przestrzeni nazw <xref:System.Deployment.Application>.|  
|**Wybierz, kiedy aplikacja ma sprawdzać dostępność aktualizacji**|Program udostępnia dwie opcje sprawdzania aktualizacji:<br /><br /> -   **przed uruchomieniem aplikacji**. Sprawdzanie aktualizacji jest przeprowadzane przed wykonaniem aplikacji.<br />-   **po uruchomieniu aplikacji**. Sprawdzanie aktualizacji rozpocznie się po zainicjowaniu głównej formy aplikacji i zostanie uruchomione przy następnym uruchomieniu aplikacji.|  
|**Częstotliwość sprawdzania aktualizacji**|Określa, jak często ClickOnce powinna sprawdzać dostępność aktualizacji:<br /><br /> -   **sprawdzaj przy każdym uruchomieniu aplikacji**. Technologia ClickOnce będzie przeprowadzać sprawdzanie aktualizacji za każdym razem, gdy użytkownik otworzy aplikację.<br />-   **Sprawdzaj co**: Wybierz przedział czasu i jednostkę (godziny, dni lub tygodnie), które muszą upłynąć przed sprawdzeniem dostępności aktualizacji.|  
|**Określ minimalną wersję wymaganą dla tej aplikacji**|Opcjonalna. Określa, że określona wersja aplikacji jest wymaganą instalacją, uniemożliwiając użytkownikom pracę z wcześniejszą wersją.|  
|**Wersja**|Wymagane, jeśli pole wyboru **Określ minimalną wymaganą wersję dla tej aplikacji** jest zaznaczone. Podany numer wersji musi mieć postać *N. n. n*. n. Wymagany jest tylko pierwszy główny numer kompilacji. Na przykład w przypadku wersji 1,0 aplikacji prawidłowe wartości mogą obejmować `1`, `1.0`, `1.0.0`i `1.0.0.0`.|  
  
### <a name="application-reference-tab"></a>Karta odwołanie do aplikacji  
 Karta **odwołanie do aplikacji** zawiera te same pola co karta **Nazwa** opisana wcześniej w tym temacie. Jedynym wyjątkiem jest następujące pole.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Wybierz manifest**|Umożliwia wybranie manifestu aplikacji. Wszystkie inne pola na tej stronie będą wypełniane po wybraniu manifestu aplikacji.|  
  
## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
- [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Mage.exe (narzędzie generowania manifestu i edytowania)](mage-exe-manifest-generation-and-editing-tool.md)
