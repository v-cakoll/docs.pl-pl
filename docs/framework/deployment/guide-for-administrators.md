---
title: .NET Framework — Przewodnik wdrażania dla administratorów
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
ms.openlocfilehash: be15ce0b0bed37da6fe400e98bfdd118c48f7ba0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716528"
---
# <a name="net-framework-deployment-guide-for-administrators"></a>.NET Framework — Przewodnik wdrażania dla administratorów

W tym artykule krok po kroku opisano, jak administrator systemu może wdrażać program .NET Framework 4.5 i jego zależności systemowe w sieci przy użyciu programu Microsoft Endpoint Configuration Manager. W tym artykule przyjęto założenie, że wszystkie docelowe komputery klienckie spełniają minimalne wymagania programu .NET Framework. Aby uzyskać listę wymagań dotyczących oprogramowania i sprzętu do zainstalowania programu .NET Framework 4.5, zobacz [Wymagania systemowe](../get-started/system-requirements.md).

> [!NOTE]
> Oprogramowanie, do którego odwołuje się niniejszy dokument, w tym między innymi programy .NET Framework 4.5, Menedżer konfiguracji i usługa Active Directory, podlegają postanowieniu licencji. W tych instrukcjach przyjęto założenie, że takie postanowienia licencyjne i warunki zostały przejrzane i zaakceptowane przez właściwych licencjobiorców oprogramowania. Te instrukcje nie unieważniają żadnego postanowienia tych umów licencyjnych.
>
> Aby uzyskać informacje na temat pomocy technicznej dla programu .NET Framework, zobacz [.NET Framework oficjalne zasady pomocy technicznej](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) w witrynie pomocy technicznej firmy Microsoft.

Ten temat zawiera następujące sekcje:

- [Proces wdrażania](#the_deployment_process)
- [Wdrażanie programu .NET Framework](#deploying_in_a_test_environment)
- [Tworzenie kolekcji](#creating_a_collection)
- [Tworzenie pakietu i programu](#creating_a_package)
- [Wybieranie punktu dystrybucji](#select_dist_point)
- [Wdrażanie pakietu](#deploying_package)
- [Zasoby](#resources)
- [Rozwiązywanie problemów](#troubleshooting)

<a name="the_deployment_process"></a>

## <a name="the-deployment-process"></a>Proces wdrażania

Jeśli masz infrastrukturę pomocniczą w miejscu, należy użyć programu Menedżer konfiguracji do wdrożenia pakietu redystrybucyjnego .NET Framework do komputerów w sieci. Tworzenie infrastruktury obejmuje utworzenie i zdefiniowanie pięciu podstawowych obszarów: kolekcji, pakietu i programu dla oprogramowania, punktów dystrybucji i wdrożeń.

- **Kolekcje** to grupy zasobów programu Configuration Manager, takie jak użytkownicy, grupy użytkowników lub komputery, do których wdrożono program .NET Framework. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do kolekcji w programie Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) w bibliotece dokumentacji programu Configuration Manager.

- **Pakiety i programy** zazwyczaj reprezentują aplikacje, które mają być zainstalowane na komputerze klienckim, ale mogą również zawierać pojedyncze pliki, aktualizacje, a nawet pojedyncze polecenia. Aby uzyskać więcej informacji, zobacz [Pakiety i programy w programie Configuration Manager](https://docs.microsoft.com/configmgr/apps/deploy-use/packages-and-programs) w bibliotece dokumentacji programu Configuration Manager.

- **Punkty dystrybucji** to role systemu lokacji programu Menedżer konfiguracji, które przechowują pliki wymagane do uruchamiania oprogramowania na komputerach klienckich. Gdy klient programu Configuration Manager odbiera i przetwarza wdrożenie oprogramowania, kontaktuje się z punktem dystrybucji w celu pobrania zawartości skojarzonej z oprogramowaniem i rozpoczęcia procesu instalacji. Aby uzyskać więcej informacji, zobacz [Podstawowe pojęcia dotyczące zarządzania zawartością w programie Configuration Manager](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/fundamental-concepts-for-content-management) w bibliotece dokumentacji programu Configuration Manager.

- **Wdrożenia** poinstruować odpowiednich członków określonej kolekcji docelowej, aby zainstalować pakiet oprogramowania.

> [!IMPORTANT]
> Procedury opisane w tym temacie zawierają typowe ustawienia służące do tworzenia i wdrażania pakietu oraz programu i mogą nie obejmować wszystkich możliwych ustawień. Aby uzyskać inne opcje wdrażania programu Configuration Manager, zobacz [bibliotekę dokumentacji programu Menedżer konfiguracji](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29).

<a name="deploying_in_a_test_environment"></a>

## <a name="deploying-the-net-framework"></a>Wdrażanie programu .NET Framework

Za pomocą programu Configuration Manager można wdrożyć instalację dyskretną programu .NET Framework 4.5, w której użytkownicy nie wchodzą w interakcję z procesem instalacji. Wykonaj następujące kroki:

1. [Tworzenie kolekcji](#creating_a_collection).

2. [Utwórz pakiet i program dla programu .NET Framework redystrybucyjnego](#creating_a_package).

3. [Wybierz punkt dystrybucji](#select_dist_point).

4. [Wdrażanie pakietu](#deploying_package).

<a name="creating_a_collection"></a>

### <a name="create-a-collection"></a>Tworzenie kolekcji

W tym kroku należy wybrać komputery, na których będzie wdrażany pakiet i program, i zgrupować je w kolekcji urządzeń. Aby utworzyć kolekcję w programie Configuration Manager, można użyć bezpośrednich reguł członkostwa (elementy członkowskie kolekcji są określane ręcznie) lub reguł zapytań (program Configuration Manager określa elementy członkowskie kolekcji na podstawie określonych kryteriów). Aby uzyskać więcej informacji na temat reguł członkostwa, w tym zapytań i reguł bezpośrednich, zobacz [Wprowadzenie do kolekcji w programie Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) w bibliotece dokumentacji programu Configuration Manager.

Aby utworzyć kolekcję:

1. W konsoli programu Menedżer konfiguracji wybierz pozycję **Zasoby i zgodność**.

2. W obszarze roboczym **Zasoby i zgodność** wybierz pozycję **Kolekcje urządzeń**.

3. Na karcie **Narzędzia główne** w grupie **Tworzenie** wybierz pozycję **Utwórz kolekcję urządzeń**.

4. Na stronie **Ogólne** **Kreatora tworzenia kolekcji urządzeń**wprowadź nazwę kolekcji.

5. Wybierz **pozycję Przeglądaj,** aby określić kolekcję ograniczającą.

6. Na stronie **Reguły członkostwa** wybierz pozycję **Dodaj regułę**, a następnie wybierz pozycję **Reguła bezpośrednia,** aby otworzyć **Kreatora tworzenia bezpośrednich reguł członkostwa**. Wybierz pozycję **Dalej**.

7. Na stronie **Wyszukiwanie zasobów na** liście Klasa **zasobu** wybierz pozycję **Zasób systemowy**. Na liście **Nazwa atrybutu** wybierz pozycję **Nazwa**. W polu **Wartość** `%`wprowadź , a następnie wybierz pozycję **Dalej**.

8. Na stronie **Wybierz zasoby** zaznacz pole wyboru dla każdego komputera, na który chcesz wdrożyć program .NET Framework. Wybierz **pozycję Dalej**, a następnie ukończ kreatora.

9. Na stronie **Reguły członkostwa** **Kreatora tworzenia kolekcji urządzeń**wybierz pozycję **Dalej**, a następnie uzupełnij kreatora.

<a name="creating_a_package"></a>

### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a>Tworzenie pakietu i programu dla redystrybucyjnego pakietu programu .NET Framework

Wykonanie poniższych kroków umożliwia ręczne utworzenie pakietu redystrybucyjnego programu .NET Framework. Pakiet będzie zawierał określone parametry instalacji programu .NET Framework oraz lokalizację, z której pakiet będzie dystrybuowany na komputery docelowe.

Aby utworzyć pakiet:

1. W konsoli programu Menedżer konfiguracji wybierz pozycję **Biblioteka oprogramowania**.

2. W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Zarządzanie aplikacjami,** a następnie wybierz pozycję **Pakiety**.

3. Na karcie **Narzędzia główne** w grupie **Tworzenie** wybierz pozycję **Utwórz pakiet**.

4. Na stronie **Pakiet** **Kreatora tworzenia pakietów i programów**wprowadź następujące informacje:

    - Nazwa:`.NET Framework 4.5`

    - Producent:`Microsoft`

    - Język. `English (US)`

5. Wybierz **pozycję Ten pakiet zawiera pliki źródłowe,** a następnie wybierz pozycję **Przeglądaj,** aby wybrać folder lokalny lub sieciowy zawierający pliki instalacyjne programu .NET Framework. Po wybraniu folderu wybierz przycisk **OK**, a następnie wybierz pozycję **Dalej**.

6. Na stronie **Typ programu** kreatora wybierz pozycję **Program standardowy**, a następnie wybierz pozycję **Dalej**.

7. Na stronie **Program** **Kreatora tworzenia pakietów i programów**wprowadź następujące informacje:

    1. **Nazwa:**`.NET Framework 4.5`

    2. **Wiersz polecenia:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (opcje wiersza polecenia są opisane w tabeli po tych krokach)

    3. **Biegnij:** Wybierz **pozycję Ukryte**.

    4. **Program można uruchomić:** Wybierz opcję określającą, że program może działać niezależnie od tego, czy użytkownik jest zalogowany.

8. Na stronie **Wymagania** wybierz pozycję **Dalej,** aby zaakceptować wartości domyślne, a następnie wykonaj kreatora.

W poniższej tabeli opisano opcje wiersza polecenia określone w kroku 7.

|Opcja|Opis|
|------------|-----------------|
|**/q**|Ustawia tryb cichy. Nie jest wymagane wprowadzanie danych przez użytkownika i nie są wyświetlane dane wyjściowe.|
|**/norestart**|Uniemożliwia Instalatorowi automatyczne wykonywanie ponownego rozruchu. Użycie tej opcji spowoduje, że program Configuration Manager będzie musiał obsługiwać ponowne uruchamianie komputera.|
|**/chainingpackage** *PackageName*|Określa nazwę pakietu, który tworzy łańcuch. Te informacje są zgłaszane wraz z innymi informacjami o sesji instalacji dla osób, które zarejestrowały się w programie poprawy jakości obsługi klienta firmy Microsoft(CEIP). Jeśli nazwa pakietu zawiera spacje, należy użyć podwójnych cudzysłowów jako ograniczników; na przykład: **/chainingpackage "Chaining Product"**.|

Wykonanie tych kroków spowoduje utworzenie pakietu o nazwie .NET Framework 4.5. Program wdraża instalację dyskretną programu .NET Framework 4.5. W instalacji dyskretnej użytkownicy nie wchodzą w interakcje z procesem instalacji, a aplikacja łańcucha musi przechwycić kod zwrotny i obsługiwać ponowne uruchamianie; zobacz [Uzyskiwanie informacji o postępie z pakietu instalacyjnego](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100)).

<a name="select_dist_point"></a>

### <a name="select-a-distribution-point"></a>Wybieranie punktu dystrybucji

Aby dystrybuować pakiet i program na komputery klienckie z serwera, należy najpierw wyznaczyć system lokacji jako punkt dystrybucji, a następnie dystrybuować pakiet do punktu dystrybucji.

Wykonując poniższe kroki, można wybrać punkt dystrybucji dla pakietu programu .NET Framework 4.5 utworzonego w poprzedniej sekcji:

1. W konsoli programu Menedżer konfiguracji wybierz pozycję **Biblioteka oprogramowania**.

2. W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Zarządzanie aplikacjami,** a następnie wybierz pozycję **Pakiety**.

3. Z listy pakietów wybierz pakiet **.NET Framework 4.5** utworzony w poprzedniej sekcji.

4. Na karcie **Narzędzia główne** w grupie **Wdrażanie** wybierz pozycję **Dystrybucja zawartości**.

5. Na karcie **Ogólne** **Kreatora dystrybucji zawartości**wybierz pozycję **Dalej**.

6. Na stronie **Miejsce docelowe zawartości** kreatora wybierz pozycję **Dodaj**, a następnie wybierz pozycję **Punkt dystrybucji**.

7. W oknie dialogowym **Dodawanie punktów dystrybucji** wybierz punkt dystrybucji, w których będzie obsługiwany pakiet i program, a następnie wybierz przycisk **OK**.

8. Wykonaj kroki kreatora.

Pakiet zawiera teraz wszystkie informacje niezbędne do dyskretnego wdrożenia programu .NET Framework 4.5. Przed wdrożeniem pakietu i programu sprawdź, czy został zainstalowany w punkcie dystrybucji; zobacz sekcję "Monitorowanie stanu zawartości" [monitoruj zawartość rozpowszechnianą z programem Menedżer konfiguracji](https://docs.microsoft.com/configmgr/core/servers/deploy/configure/monitor-content-you-have-distributed) w bibliotece dokumentacji programu Menedżer konfiguracji.

<a name="deploying_package"></a>

### <a name="deploy-the-package"></a>Wdrażanie pakietu

Aby wdrożyć pakiet i program .NET Framework 4.5:

1. W konsoli programu Menedżer konfiguracji wybierz pozycję **Biblioteka oprogramowania**.

2. W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Zarządzanie aplikacjami,** a następnie wybierz pozycję **Pakiety**.

3. Z listy pakietów wybierz utworzony pakiet o nazwie **.NET Framework 4.5**.

4. Na karcie **Narzędzia główne** w grupie **Wdrażanie** wybierz pozycję **Wdrażanie**.

5. Na stronie **Ogólne** **Kreatora wdrażania oprogramowania**wybierz pozycję **Przeglądaj**, a następnie wybierz utworzoną wcześniej kolekcję. Wybierz pozycję **Dalej**.

6. Na stronie **Zawartość** kreatora sprawdź, czy wyświetlany jest punkt, z którego chcesz dystrybuować oprogramowanie, a następnie wybierz pozycję **Dalej**.

7. Na stronie **Ustawienia wdrażania** kreatora upewnij się, że **akcja** jest ustawiona na **Zainstaluj,** a **cel** jest ustawiony na **Wymagane**. Te wartości ustawień gwarantują, że pakiet oprogramowania będzie obowiązkowo instalowany na komputerach docelowych. Wybierz pozycję **Dalej**.

8. Na stronie **Planowanie** kreatora określ, kiedy ma zostać zainstalowany program .NET Framework. Można wybrać **opcję Nowy,** aby przypisać czas instalacji lub poinstruować oprogramowanie, aby zainstalować, gdy użytkownik loguje się lub wyłącza, lub tak szybko, jak to możliwe. Wybierz pozycję **Dalej**.

9. Na stronie **User Experience** kreatora użyj wartości domyślnych i wybierz pozycję **Dalej**.

    > [!WARNING]
    > W środowisku produkcyjnym mogą obowiązywać zasady wymagające wybrania innych ustawień harmonogramu wdrażania. Aby uzyskać informacje o tych opcjach, zobacz [Właściwości nazwy anonsu: Karta Harmonogram](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).

10. Na stronie **Punkty dystrybucji** kreatora użyj wartości domyślnych i wybierz pozycję **Dalej**.

11. Wykonaj kroki kreatora. Można monitorować postęp wdrożenia w **węźle Wdrożenia** obszaru roboczego **Monitorowanie.**

Teraz pakiet zostanie wdrożony w kolekcji docelowej i rozpocznie się dyskretna instalacja programu .NET Framework 4.5. Aby uzyskać informacje na temat kodów błędów instalacji programu .NET Framework 4.5, zobacz sekcję [Kody zwrotów](#return_codes) w dalszej części tego tematu.

<a name="resources"></a>

## <a name="resources"></a>Zasoby

Aby uzyskać więcej informacji na temat infrastruktury do testowania wdrożenia pakietu redystrybucyjnego .NET Framework 4.5, zobacz następujące zasoby.

**Active Directory, DNS, DHCP:**

- [Usługi Active Directory Domain Services](/windows/desktop/ad/active-directory-domain-services)

- [System nazw domen (DNS)](/windows-server/networking/dns/dns-top)

- [Protokół DHCP](/windows-server/networking/technologies/dhcp/dhcp-top)

**Program SQL Server 2008:**

- [Instalowanie programu SQL Server 2008 (sql server video)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))

- [Omówienie zabezpieczeń programu SQL Server 2008 dla administratorów baz danych](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)

**Program System Center 2012 Configuration Manager (punkt zarządzania, punkt dystrybucji):**

- [Administrowanie lokacją dla programu System Center 2012 Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg681983%28v=technet.10%29)

- [Planowanie i wdrażanie pojedynczej lokacji programu Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb680961%28v=technet.10%29)

**Klient programu System Center 2012 Configuration Manager dla komputerów z systemem Windows:**

- [Wdrażanie klientów dla programu System Center 2012 Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg699391%28v=technet.10%29)

<a name="troubleshooting"></a>

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="log-file-locations"></a>Lokalizacje plików dziennika

Podczas instalacji programu .NET Framework są generowane następujące pliki dziennika:

- %temp%\Microsoft .NET Framework *wersja*\*.txt
- %temp%\Microsoft .NET Framework *wersja*\*.html

gdzie *wersja* jest wersją programu .NET Framework, którą instalujesz, taką jak 4.5 lub 4.7.2.

Można również określić katalog, do którego są zapisywane pliki dziennika, używając opcji `/log` wiersza polecenia w poleceniu instalacji programu .NET Framework. Aby uzyskać więcej informacji, zobacz [przewodnik po wdrażaniu programu .NET Framework dla deweloperów](deployment-guide-for-developers.md#command-line-options).

Za pomocą narzędzia do [zbierania dzienników](https://www.microsoft.com/download/details.aspx?id=12493) można zbierać pliki dziennika programu .NET Framework i tworzyć skompresowany plik szafy (cab), który zmniejsza rozmiar plików.

<a name="return_codes"></a>

### <a name="return-codes"></a>Kody powrotne

W poniższej tabeli wymieniono najczęstsze kody zwrotne z programu redystrybucyjnego programu .NET Framework 4.5. Kody powrotne są takie same dla wszystkich wersji instalatora.

Aby uzyskać łącza do szczegółowych informacji, zobacz następną sekcję [Pobieranie kodów błędów](#additional_error_codes).

|Kod powrotu|Opis|
|-----------------|-----------------|
|0|Instalacja została zakończona pomyślnie.|
|1602|Użytkownik anulował instalację.|
|1603|Podczas instalacji wystąpił błąd krytyczny.|
|1641|Do ukończenia instalacji wymagane jest ponowne uruchomienie komputera. Ten komunikat oznacza sukces.|
|3010|Do ukończenia instalacji wymagane jest ponowne uruchomienie komputera. Ten komunikat oznacza sukces.|
|5100|Komputer użytkownika nie spełnia wymagań systemowych.|

<a name="additional_error_codes"></a>

### <a name="download-error-codes"></a>Kody błędów pobierania

- [Kody błędów usługi inteligentnego transferu w tle (BITS)](/windows/desktop/Bits/bits-return-values)

- [Kody błędów monikera url](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145%28v=vs.85%29)

- [Kody błędów winhttp](/windows/desktop/WinHttp/error-messages)

Inne kody błędów:

- [Kody błędów Instalatora Windows](/windows/desktop/msi/error-codes)

- [Kody wyników programu Windows Update Agent](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))

## <a name="see-also"></a>Zobacz też

- [Przewodnik wdrażania dla deweloperów](deployment-guide-for-developers.md)
- [Wymagania systemowe](../get-started/system-requirements.md)
