---
title: MageUI.exe (Narzędzie generowania i edytowania manifestu, klient grafiki)
ms.date: 03/30/2017
helpviewer_keywords:
- Manifest Generation and Editing tool
- MageUI.exe
ms.assetid: f9e130a6-8117-49c4-839c-c988f641dc14
ms.openlocfilehash: 3f303583b1cff785ab0020e616fee58ef02a1c58
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487041"
---
# <a name="mageuiexe-manifest-generation-and-editing-tool-graphical-client"></a>MageUI.exe (Narzędzie generowania i edytowania manifestu, klient grafiki)

MageUI.exe obsługuje takie same funkcje jak narzędzie wiersza polecenia Mage.exe, ale z interfejsem użytkownika systemu Windows (UI). Za pomocą tego narzędzia można tworzyć, edytować i podpisywać manifesty wdrażania i aplikacji. Nowe manifesty utworzone za pomocą MageUI.exe docelowej [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Poprzednie wersje MageUI.exe stosuje się do poprzednich wersji .NET Framework. Podczas dodawania lub usuwania zestawów z manifestu lub ponownego podpisywania istniejącego, MageUI.exe nie aktualizuje manifestu do obiektu docelowego [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Aby uzyskać więcej informacji, zobacz [Mage.exe (Manifest Generation i narzędzia do edytowania)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).

 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio (lub wiersza polecenia programu Visual Studio Windows 7). Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

 Dołączone jako składnik programu Visual Studio są dwie wersje programu — Mage.exe i MageUI.exe. Aby wyświetlić informacje o wersji, uruchom program MageUI.exe, wybierz **pomocy**i wybierz **o**. W tej dokumentacji opisano wersję 4.0.x.x programów Mage.exe i MageUI.exe.

> [!NOTE]
> MageUI.exe nie obsługuje [compatibleFrameworks](/visualstudio/deployment/compatibleframeworks-element-clickonce-deployment) elementu podczas zapisywania manifestu aplikacji, który już został podpisany za pomocą certyfikatu przy użyciu MageUI.exe. Zamiast tego należy użyć [Mage.exe](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
## <a name="uielement-list"></a>Lista elementów UI  
 W następującej tabeli wymieniono elementy menu i paski narzędzi, które są dostępne.  
  
|Polecenie|Menu|Skrót|Opis|  
|-------------|----------|--------------|-----------------|  
|**Manifest aplikacji**|**Plik, nowy**||Tworzy nowy manifest aplikacji.|  
|**Manifest wdrażania**|**Plik, nowy**||Tworzy nowy manifest wdrożenia.|  
|**Otwórz**|**Plik**|CTRL+O|Otwiera do edycji istniejący manifest wdrażania, manifest aplikacji lub licencję zaufania.|  
|**Zamknij**|**Plik**|CTRL+F4|Zamyka otwarty plik.<br /><br /> Jeśli modyfikujesz plik przed jego zamknięciem, MageUI.exe monituje o ponowne podpisywanie pliku kluczem publicznym, parą kluczy lub przechowywanym certyfikatem.|  
|**Zapisz**|**Plik**|CTRL+S|Zapisuje na dysku dokument, który aktualnie ma fokus wprowadzania użytkownika.|  
|**Zapisz jako**|**Plik**||Zapisuje plik na dysku, umożliwiając podanie nowej nazwy pliku i/lub lokalizacji.|  
|**Zapisz wszystko**|**Plik**||Zapisuje zmiany wprowadzone do wszystkich plików aktualnie otwartych w MageUI.exe.|  
|**Preferencje**|**Plik**||Otwiera **preferencje** okno dialogowe. Aby uzyskać więcej informacji, zobacz następującą sekcję.|  
|**Exit**|**Plik**|ALT+F4|Zamyka program MageUI.exe.|  
|**Cut**|**Edytowanie**|CTRL+X|Usuwa zaznaczony tekst z aplikacji i przenosi je do Schowka systemu Windows.|  
|**Kopiuj**|**Edytowanie**|CTRL+C|Kopiuje zaznaczony tekst do Schowka systemu Windows.|  
|**Wklej**|**Edytowanie**|CTRL+V|Wkleja tekst ze Schowka systemu Windows do aktywnego elementu tekstu.|  
|**Delete**|**Edytowanie**||Usuwa element zaznaczony na liście, takie jak licencja zaufania na **manifestu wdrażania** kartę.|  
|**Zamknij wszystkie**|**Window**||Zamyka wszystkie pliki otwarte w MageUI.exe. Jeżeli jeden lub więcej plików wymagają zapisania, MageUI.exe wyświetli monit o zapisanie ich. MageUI.exe również wyświetla monit o wybranie klucza podpisywania dla każdego niepodpisanego lub zmienionego pliku.|  
|**— informacje**|**Pomoc**||Wyświetla informacje o wersji i prawach autorskich dotyczące MageUI.exe.|  
  
## <a name="preferences-dialog-box"></a>Okno dialogowe Preferencje  
 **Preferencje** okno dialogowe zawiera następujące elementy.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Zaloguj się przy zapisywaniu**|Monituje o podpisanie pliku przy każdym zapisie modyfikacji.|  
|**Użyj domyślnego certyfikatu podpisywania**|Używa klucza wprowadzonego w **plik certyfikatu** pole tekstowe do podpisania wszystkich plików. Eliminuje monit podpisywania, który zwykle pojawia się podczas zapisywania pliku i **Zaloguj się przy zapisywaniu** jest zaznaczone. Użyj wielokropka ( **...** ) znajdujący się obok **plik certyfikatu** pole tekstowe, aby wybrać plik klucza.|  
|Algorytm porządkowania|Określa algorytm, za pomocą którego zostaną wygenerowane skróty zależności. Wartością musi być „sha256RSA” lub „sha1RSA”. Domyślną wartością jest SHA1. Używana zarówno w manifestach aplikacji, jak i wdrażania. Jeśli użytkownik poda certyfikat podczas zapisywania manifestu, używane są algorytmy w certyfikacie do wygenerowania rozkładów zależności.|  
  
## <a name="signing-options-dialog-box"></a>Okno dialogowe Opcje podpisywania  
 **Opcje podpisywania** pojawi się okno dialogowe podczas pierwszego zapisywania manifestu lub licencji zaufania lub po zmianie manifestu lub licencji zaufania. Pojawia się tylko, jeśli **Zaloguj się przy zapisywaniu** opcji **preferencje** okno dialogowe jest zaznaczone. Użytkownik musi być połączony z Internetem podczas podpisywania manifestu określającego wartość w **TimeStamping URI** pola tekstowego.  
  
 To okno dialogowe zawiera następujące elementy.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Podpisz plikiem certyfikatu**|Podpisuje manifest certyfikatem cyfrowym przechowywanym w systemie plików.|  
|**Plik**|Zapewnia miejsce do wpisania ścieżki do pliku pfx reprezentującego certyfikat.|  
|**...**|Otwiera **wybierz plik** okno dialogowe wybierania istniejącego pliku pfx.|  
|**Nowy**|Generuje nowy pfx niesprawdzalny przez urząd certyfikacji (CA). Aby uzyskać więcej informacji na temat typów certyfikatów używanych do podpisywania wdrożeń technologii ClickOnce zobacz [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview).|  
|**Hasło**|Miejsce na wpisanie hasła używanego do podpisywania tym certyfikatem. Jeśli nie ma to zastosowania, może być puste.|  
|**Podpisz przechowywanym certyfikatem**|Wyświetla listę wyboru certyfikatów cyfrowych przechowywanych w magazynie certyfikatów na komputerze.|  
|**TimeStamping URI**|Wyświetla identyfikator URI usługi sygnatur cyfrowych. Przypisanie do manifestu znacznika czasu zapobiega konieczności ponownego podpisania manifestu, jeśli certyfikat cyfrowy wygaśnie przed wdrożeniem następnej wersji aplikacji. Aby uzyskać więcej informacji, zobacz [Windows członkowie programu głównych certyfikatów](https://go.microsoft.com/fwlink/?LinkId=159000) i [ClickOnce i podpis Authenticode](/visualstudio/deployment/clickonce-and-authenticode).|  
|**Nie podpisuj**|Umożliwia zapisanie manifestu bez dodawania podpisu z certyfikatu cyfrowego.|  
  
## <a name="tab-and-panel-descriptions"></a>Opisy karta i panelu  
 Po otwarciu w programie MageUI.exe dokument pojawia się w obrębie własnej strony karty. Każda karta zawiera zestaw paneli właściwości. Panele zawierają zgrupowane podzbiory danych dokumentu.  
  
### <a name="application-manifest-tab"></a>Karta manifestu aplikacji  
 **Manifest aplikacji** karty wyświetla zawartość manifestu aplikacji. Manifest aplikacji w tym artykule opisano wszystkie pliki dołączone do wdrożenia i uprawnień wymaganych do uruchomienia na kliencie aplikacji.  
  
 **Manifest aplikacji** karta zawiera następujące karty.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Określa informacje identyfikacyjne dotyczące tego wdrożenia.|  
|**Opis**|Określa wydawcę, produkt i pomocy technicznej informacji.|  
|**Opcje aplikacji**|Określa, czy to jest aplikacją przeglądarki oraz czy jest to tym manifestu jest źródło informacji zaufania.|  
|**Pliki**|Określa wszystkie pliki, wchodzących w skład tego wdrożenia.|  
|**Wymagane uprawnienia**|Określa zestaw minimalne uprawnienia wymagane przez aplikację do uruchamiania na komputerze klienckim.|  
  
### <a name="name-tab"></a>Nazwa karty  
 **Nazwa** karta jest wyświetlana, gdy najpierw Utwórz lub Otwórz manifest aplikacji. Jednoznacznie identyfikuje wdrożenia i opcjonalnie określa platformę prawidłową docelową.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Wymagana. Nazwa manifestu aplikacji. Zazwyczaj taka sama jak nazwa pliku.|  
|**Wersja**|Wymagana. Numer wersji wdrożenia w formie *N.N.N.N*. Wymagany jest tylko pierwszy numer kompilacji głównych. Na przykład dla wersji 1.0 aplikacji prawidłowe wartości obejmuje `1`, `1.0`, `1.0.0`, i `1.0.0.0`.|  
|**Procesor**|Opcjonalna. Architektura komputera, na którym można uruchomić tego wdrożenia. Wartość domyślna to `msil`, lub języka Microsoft Intermediate Language, który jest domyślnym formatem wszystkich zestawów zarządzanych. Zmień to pole, jeśli zestawy mają wstępnie skompilowany w aplikacji dla określonej architektury. Aby uzyskać więcej informacji o wstępnej kompilacji, zobacz [Ngen.exe (Generator obrazu natywnego)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|  
|**Kultury**|Opcjonalna. Legalną dwuczęściową krajów i regionów kod ISO w którym aplikacja jest uruchomiona. Wartość domyślna to `neutral`.|  
|**Token klucza publicznego**|Opcjonalna. Klucz publiczny, za pomocą którego została podpisana tego manifestu aplikacji. Jeśli jest to manifest nowych lub bez znaku, w tym polu będzie wyświetlany jako `Unsigned`.|  
  
### <a name="description-tab"></a>Opis karty  
 Te informacje są zazwyczaj dostarczane w pliku manifestu wdrożenia. Te pola mogą być modyfikowane tylko, jeśli **manifestu zaufania informacji z aplikacji użyj** zaznaczone jest pole wyboru **Opcje aplikacji** kartę.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Publisher**|Nazwa osoby lub organizacji jest odpowiedzialny za aplikacji. Ta wartość jest używana jako nazwa folderu menu Start.|  
|**Produkt**|Pełna nazwa produktu. W przypadku wybrania **zainstalować lokalnie** dla **typ aplikacji** element na **opcje wdrażania** karta manifestu wdrożenia, ta nazwa jest wyświetlanych w **Start** łącze menu i **apletu Dodaj lub usuń programy** dla tej aplikacji.|  
|**Lokalizacja pomocy technicznej**|Adres URL, z którego klienci mogą uzyskać pomoc i obsługa techniczna dla aplikacji.|  
  
### <a name="application-options-tab"></a>Karta Opcje aplikacji  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Aplikacji przeglądarka Windows Presentation Foundation**|Określa, czy jest to aplikacja WPF, która działa w przeglądarce jako aplikacja przeglądarki XAML (XBAP).|  
|**Użyj informacji o zaufania manifestu aplikacji**|Określa, czy ten manifest zawiera informacje zaufania.|  
  
### <a name="files-tab"></a>Karta pliki  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Katalog aplikacji**|Katalog, w którym znajdują się pliki aplikacji. Użyj wielokropka ( **...** ) przycisk, aby wybrać katalog.|  
|**Wypełnij**|Dodaje do manifestu aplikacji wszystkie pliki w katalogu aplikacji i podkatalogów. Jeśli MageUI.exe znajdzie jednego pliku wykonywalnego w katalogu, jego automatycznie oznacza to jako punkt wejścia, który jest wykonywany jako pierwszy, gdy aplikacja ClickOnce jest uruchamiana na komputerze klienckim.|  
|**Pliki aplikacji**|Wyświetla listę wszystkich plików w aplikacji. Każdy plik ma trzy atrybuty można edytować, omówiono poniżej.|  
|**Typ pliku**|Typ pliku może być jedną z czterech wartości:<br /><br /> -Brak.<br />-   Entry Point. Podstawowy plik wykonywalny aplikacji. Tylko jeden plik wykonywalny może zostać oznaczony jako punkt wejścia.<br />— Plik danych. Plik, taki jak plik XML, który dostarcza dane do aplikacji.<br />— Plik ikony. Ikony aplikacji, takich jak pojawia się na pulpicie lub w rogu okna aplikacji.|  
|**Optional**|Pliki oznaczone jako opcjonalne nie zostaną pobrane na początkowej instalacji lub aktualizacji, ale może zostać pobrana w czasie wykonywania za pomocą interfejsu API na żądanie System.Deployment. Aby uzyskać więcej informacji, zobacz [instruktażu: Pobieranie zestawów na żądanie z wdrożeniem ClickOnce interfejsu API przy użyciu narzędzia Projektant](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer).|  
|**Grupa**|Etykieta dla grupy plików opcjonalne. Zastosuj etykietę grupy do grupy plików i Pobierz partię plików za pomocą jednego wywołania interfejsu API za pomocą interfejsu API na żądanie.|  
  
### <a name="permissions-required-tab"></a>Na karcie wymagane uprawnienia  
 Użyj **wymagane są uprawnienia** kartę, jeśli musisz przyznać aplikacji większy dostęp na komputerze lokalnym nie są przyznawane domyślnie. Aby uzyskać więcej informacji, zobacz [zabezpieczanie aplikacji ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Typ zestawu uprawnień**|Zestaw minimalne uprawnienia wymagane przez tę aplikację do uruchamiania na komputerze klienckim. Aby uzyskać opis tych zestawów uprawnień i uprawnienia, które ani nie popytu patrz [nazwane zestawy uprawnień](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).|  
|**Szczegóły**|Ustaw XML utworzone dla manifestu aplikacji do reprezentowania uprawnienia. Jeśli nie masz dobre zrozumienie manifest aplikacji w formacie XML, nie należy edytować plik XML ręcznie. Aby uzyskać więcej informacji, zobacz [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest).|  
  
### <a name="deployment-manifest-tab"></a>Karta manifestu wdrożenia  
 **Manifestu wdrażania** karta zawiera następujące karty.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Określa informacje identyfikacyjne dotyczące tego wdrożenia.|  
|**Opis**|Określa wydawcę, produkt i pomocy technicznej informacji.|  
|**Opcje wdrażania**|Określa dodatkowe informacje na temat wdrożenia, takie jak typ aplikacji i lokalizacja początkowa.|  
|**Opcje aktualizacji**|Określa, jak często technologia ClickOnce będzie sprawdzać aktualizacje aplikacji.|  
|**Odwołanie do aplikacji**|Określa manifest aplikacji dla tego wdrożenia.|  
  
### <a name="name-tab"></a>Nazwa karty  
 **Nazwa** karta jest wyświetlana, gdy najpierw Utwórz lub Otwórz manifest wdrożenia. Jednoznacznie identyfikuje wdrożenia i opcjonalnie określa platformę prawidłową docelową.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Wymagana. Nazwa pliku manifestu wdrożenia. Zazwyczaj taka sama jak nazwa pliku.|  
|**Wersja**|Wymagana. Numer wersji wdrożenia w formie *N.N.N.N*. Wymagany jest tylko pierwszy numer kompilacji głównych. Na przykład dla wersji 1.0 aplikacji prawidłowe wartości obejmuje `1`, `1.0`, `1.0.0`, i `1.0.0.0`.|  
|**Procesor**|Opcjonalna. Architektura komputera, na którym można uruchomić tego wdrożenia. Wartość domyślna to `msil`, lub języka Microsoft Intermediate Language, domyślny format wszystkich zestawów zarządzanych. Zmień to pole, jeśli skompilowałeś zestawy w aplikacji dla określonej architektury.|  
|**Kultury**|Opcjonalna. Kod kraju/regionu ISO legalną dwuczęściową w którym aplikacja jest uruchomiona. Wartość domyślna to `neutral`.|  
|**Token klucza publicznego**|Opcjonalna. Klucz publiczny, za pomocą którego została podpisana tego manifestu wdrażania. Jeśli jest to manifest nowych lub bez znaku, w tym polu będzie wyświetlany jako `Unsigned`.|  
  
### <a name="description-tab"></a>Opis karty  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Publisher**|Wymagana. Nazwa osoby lub organizacji jest odpowiedzialny za aplikacji. Ta wartość jest używana jako nazwa folderu menu Start.|  
|**Produkt**|Wymagana. Pełna nazwa produktu. W przypadku wybrania **zainstalować lokalnie** dla **typ aplikacji** element na **opcje wdrażania** kartę, ta nazwa będzie wyświetlanych w **Start** łącze menu i **apletu Dodaj lub usuń programy** dla tej aplikacji.|  
|**Lokalizacja pomocy technicznej**|Opcjonalna. Adres URL, z którego klienci mogą uzyskać pomoc i obsługa techniczna dla aplikacji.|  
  
### <a name="deployment-options-tab"></a>Karta Opcje wdrożenia  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Typ aplikacji**|Opcjonalna. Określa, czy ta aplikacja instaluje się na komputerze klienckim (**zainstalować lokalnie**), działa w trybie online (**tylko Online**), lub aplikacji WPF, która działa w przeglądarce (**przeglądarki WPF Aplikacja**). Wartość domyślna to **zainstalować lokalnie**.|  
|**Lokalizacja początkowa**|Opcjonalna. Adres URL, z którego powinien rzeczywiście uruchomienia aplikacji. Przydatne podczas wdrażania aplikacji z dysku CD, który powinien automatycznie zaktualizowana z sieci Web.|  
|**Obejmują lokalizacja początkowa (ProviderURL) w manifeście**|Opcjonalna. Określa adres URL, pod którym technologia ClickOnce będzie szukać aktualizacji aplikacji.|  
|**Automatycznie, uruchom aplikację po zainstalowaniu**|Wymagana. Określa, czy aplikacja ClickOnce uruchamiać natychmiast po wstępnej instalacji z adresu URL. Wartość domyślna to, że pole wyboru jest zaznaczone.|  
|**Zezwalaj na parametry adresu URL, które zostaną przekazane do aplikacji**|Wymagana. Zezwala na transfer danych parametru w aplikacji ClickOnce za pomocą ciągu zapytania, dołączone do adresu URL pliku manifestu wdrożenia. Wartość domyślna to, że pole wyboru jest wyczyszczone.|  
|**Rozszerzenie pliku .deploy**|Wymagana. Po wybraniu wszystkich plików w manifeście aplikacji musi mieć rozszerzenie .deploy. Wartość domyślna to, że pole wyboru jest wyczyszczone.|  
  
### <a name="update-options-tab"></a>Karta Opcje aktualizacji  
 **Opcje aktualizacji** karta zawiera tylko opcje wymienione w tym miejscu po **typ aplikacji** wyboru na **nazwa** karta jest ustawiona na **zainstalować lokalnie** .  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Ta aplikacja ma sprawdzać dostępność aktualizacji**|Określa, czy technologia ClickOnce będzie sprawdzać aktualizacje aplikacji. Jeśli to pole wyboru nie jest zaznaczone, aplikacja nie będzie sprawdzać dostępność aktualizacji, jeśli nie możesz zaktualizować programowo przy użyciu interfejsów API w <xref:System.Deployment.Application> przestrzeni nazw.|  
|**Wybierz, jeśli aplikacja ma sprawdzać dostępność aktualizacji**|Oferuje dwie opcje sprawdzania aktualizacji:<br /><br /> -   **Przed uruchomieniem aplikacji**. Sprawdzenie aktualizacji są wykonywane przed wykonywania aplikacji.<br />-   **Po uruchomieniu aplikacji**. Sprawdzenie aktualizacji rozpoczyna się po formularza głównego aplikacji została zainicjowana i uruchomi przy następnym uruchomieniu aplikacji.|  
|**Częstotliwość sprawdzania aktualizacji**|Określa, jak często ClickOnce ma sprawdzać dostępność aktualizacji:<br /><br /> -   **Sprawdź za każdym razem, gdy aplikacja zostanie uruchomiona**. ClickOnce wykona sprawdzenie aktualizacji, za każdym razem, gdy użytkownik otwiera aplikację.<br />-   **Sprawdź, co**: Wybierz przedział czasu i jednostek (godzin, dni lub tygodni), który musi upłynąć przed sprawdzania dostępności aktualizacji.|  
|**Określanie minimalnej wymaganej wersji tej aplikacji**|Opcjonalna. Określa wymaganą instalację, uniemożliwiając użytkownikom pracy przy użyciu starszej wersji określonej wersji aplikacji.|  
|**Wersja**|Jeśli wymagane **określanie minimalnej wymaganej wersji tej aplikacji** pole wyboru jest zaznaczone. Podany numer wersji musi mieć postać *N.N.N.N*. Wymagany jest tylko pierwszy numer kompilacji głównych. Na przykład dla wersji 1.0 aplikacji prawidłowe wartości obejmuje `1`, `1.0`, `1.0.0`, i `1.0.0.0`.|  
  
### <a name="application-reference-tab"></a>Karta odwołania aplikacji  
 **Odwołania aplikacji** karta zawiera te same pola jako **nazwa** kartę opisane we wcześniejszej części tego tematu. Jedynym wyjątkiem jest następujące pole.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Wybierz manifestu**|Można wybrać w manifeście aplikacji. Wszystkie inne pola na tej stronie zostaną wyświetlone po wybraniu manifest aplikacji.|  
  
## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
- [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Mage.exe (narzędzie generowania manifestu i edytowania)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)
