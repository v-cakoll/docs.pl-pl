---
title: .NET Framework — Przewodnik wdrażania dla administratorów
description: Zapoznaj się z przewodnikiem wdrażania platformy .NET dla administratorów. Te informacje służą do wdrażania programu .NET w wersji 4,5 i jej zależności systemowych w sieci.
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
ms.openlocfilehash: d58eac4f21e4f1069ac392aacb4e9818831e914c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622656"
---
# <a name="net-framework-deployment-guide-for-administrators"></a>.NET Framework — Przewodnik wdrażania dla administratorów

W tym artykule krok po kroku opisano, jak administrator systemu może wdrożyć .NET Framework 4,5 i zależności systemu w sieci za pomocą usługi Microsoft Endpoint Configuration Manager. W tym artykule przyjęto założenie, że wszystkie docelowe komputery klienckie spełniają minimalne wymagania programu .NET Framework. Aby zapoznać się z listą wymagań oprogramowania i sprzętu dotyczących instalowania .NET Framework 4,5, zobacz [wymagania systemowe](../get-started/system-requirements.md).

> [!NOTE]
> Oprogramowanie przywoływane w tym dokumencie, w tym, bez ograniczenia, .NET Framework 4,5, Configuration Manager i Active Directory, podlega postanowieniom licencyjnym. W tych instrukcjach przyjęto założenie, że takie postanowienia licencyjne i warunki zostały przejrzane i zaakceptowane przez właściwych licencjobiorców oprogramowania. Te instrukcje nie unieważniają żadnego postanowienia tych umów licencyjnych.
>
> Aby uzyskać informacje na temat pomocy technicznej dla .NET Framework, zobacz [.NET Framework oficjalne zasady pomocy technicznej](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) w witrynie sieci Web Pomoc techniczna firmy Microsoft.

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

W przypadku korzystania z infrastruktury obsługiwanej przez program Configuration Manager można wdrożyć pakiet redystrybucyjny .NET Framework na komputerach w sieci. Tworzenie infrastruktury obejmuje utworzenie i zdefiniowanie pięciu podstawowych obszarów: kolekcji, pakietu i programu dla oprogramowania, punktów dystrybucji i wdrożeń.

- **Kolekcje** są grupami zasobów Configuration Manager, takich jak użytkownicy, grupy użytkowników lub komputery, na których wdrożono .NET Framework. Aby uzyskać więcej informacji, zobacz [wprowadzenie do kolekcji w Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) w bibliotece dokumentacji Configuration Manager.

- **Pakiety i programy** zwykle reprezentują aplikacje, które mają być zainstalowane na komputerze klienckim, ale mogą również zawierać pojedyncze pliki, aktualizacje lub nawet poszczególne polecenia. Aby uzyskać więcej informacji, zobacz [pakiety i programy w Configuration Manager](https://docs.microsoft.com/configmgr/apps/deploy-use/packages-and-programs) w bibliotece dokumentacji Configuration Manager.

- **Punkty dystrybucji** są Configuration Manager ról systemu lokacji, które przechowują pliki wymagane do uruchamiania oprogramowania na komputerach klienckich. Gdy klient programu Configuration Manager odbiera i przetwarza wdrożenie oprogramowania, kontaktuje się z punktem dystrybucji w celu pobrania zawartości skojarzonej z oprogramowaniem i rozpoczęcia procesu instalacji. Aby uzyskać więcej informacji, zobacz [podstawowe pojęcia związane z zarządzaniem zawartością w programie Configuration Manager](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/fundamental-concepts-for-content-management) w bibliotece dokumentacji Configuration Manager.

- **Wdrożenia** instruują odpowiednich członków określonej kolekcji docelowej w celu zainstalowania pakietu oprogramowania.

> [!IMPORTANT]
> Procedury opisane w tym temacie zawierają typowe ustawienia służące do tworzenia i wdrażania pakietu oraz programu i mogą nie obejmować wszystkich możliwych ustawień. Inne Configuration Manager opcje wdrażania można znaleźć w [bibliotece dokumentacji Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29).

<a name="deploying_in_a_test_environment"></a>

## <a name="deploying-the-net-framework"></a>Wdrażanie programu .NET Framework

Za pomocą Configuration Manager można wdrożyć instalację dyskretną .NET Framework 4,5, w której użytkownicy nie współpracują z procesem instalacji. Wykonaj następujące kroki:

1. [Utwórz kolekcję](#creating_a_collection).

2. [Utwórz pakiet i program dla .NET Framework pakiet redystrybucyjny](#creating_a_package).

3. [Wybierz punkt dystrybucji](#select_dist_point).

4. [Wdróż pakiet](#deploying_package).

<a name="creating_a_collection"></a>

### <a name="create-a-collection"></a>Tworzenie kolekcji

W tym kroku należy wybrać komputery, na których będzie wdrażany pakiet i program, i zgrupować je w kolekcji urządzeń. Aby utworzyć kolekcję w programie Configuration Manager, można użyć bezpośrednich reguł członkostwa (elementy członkowskie kolekcji są określane ręcznie) lub reguł zapytań (program Configuration Manager określa elementy członkowskie kolekcji na podstawie określonych kryteriów). Aby uzyskać więcej informacji na temat reguł członkostwa, w tym zapytań i reguł bezpośrednich, zobacz [wprowadzenie do kolekcji w Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) w bibliotece dokumentacji Configuration Manager.

Aby utworzyć kolekcję:

1. W konsoli Configuration Manager wybierz pozycję **zasoby i zgodność**.

2. W obszarze roboczym **zasoby i zgodność** wybierz pozycję **Kolekcje urządzeń**.

3. Na karcie **Narzędzia główne** w grupie **Tworzenie** wybierz pozycję **Utwórz kolekcję urządzeń**.

4. Na stronie **Ogólne** **Kreatora tworzenia kolekcji urządzeń**wprowadź nazwę kolekcji.

5. Wybierz pozycję **Przeglądaj** , aby określić kolekcję ograniczającą.

6. Na stronie **reguły członkostwa** wybierz pozycję **Dodaj regułę**, a następnie wybierz pozycję **reguła bezpośrednia** , aby otworzyć **Kreatora tworzenia reguły członkostwa bezpośredniego**. Wybierz pozycję **Next** (Dalej).

7. Na stronie **Wyszukiwanie zasobów** na liście **Klasa zasobów** wybierz pozycję **zasób systemowy**. Na liście **nazwa atrybutu** wybierz pozycję **Nazwa**. W polu **wartość** wprowadź `%` , a następnie wybierz przycisk **dalej**.

8. Na stronie **Wybierz zasoby** zaznacz pole wyboru obok każdego komputera, na którym chcesz wdrożyć .NET Framework. Wybierz pozycję **dalej**, a następnie Zakończ pracę kreatora.

9. Na stronie **reguły członkostwa** **Kreatora tworzenia kolekcji urządzeń**wybierz **dalej**, a następnie Ukończ pracę kreatora.

<a name="creating_a_package"></a>

### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a>Tworzenie pakietu i programu dla redystrybucyjnego pakietu programu .NET Framework

Wykonanie poniższych kroków umożliwia ręczne utworzenie pakietu redystrybucyjnego programu .NET Framework. Pakiet będzie zawierał określone parametry instalacji programu .NET Framework oraz lokalizację, z której pakiet będzie dystrybuowany na komputery docelowe.

Aby utworzyć pakiet:

1. W konsoli Configuration Manager wybierz pozycję **Biblioteka oprogramowania**.

2. W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Zarządzanie aplikacjami**, a następnie wybierz pozycję **pakiety**.

3. Na karcie **Narzędzia główne** w grupie **Tworzenie** wybierz pozycję **Utwórz pakiet**.

4. Na stronie **pakiet** **Kreatora tworzenia pakietu i programu**wprowadź następujące informacje:

    - Nazwij`.NET Framework 4.5`

    - Instrukcj`Microsoft`

    - Język. `English (US)`

5. Wybierz opcję **ten pakiet zawiera pliki źródłowe**, a następnie wybierz pozycję **Przeglądaj** , aby wybrać folder lokalny lub sieciowy zawierający pliki instalacyjne .NET Framework. Po wybraniu folderu wybierz **przycisk OK**, a następnie wybierz przycisk **dalej**.

6. Na stronie **Typ programu** kreatora wybierz pozycję **program standardowy**, a następnie wybierz przycisk **dalej**.

7. Na stronie **program** w **Kreatorze tworzenia pakietu i programu**wprowadź następujące informacje:

    1. **Nazwa:**`.NET Framework 4.5`

    2. **Wiersz polecenia:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (Opcje wiersza polecenia są opisane w tabeli po wykonaniu tych kroków)

    3. **Uruchom:** Wybierz **Ukryj**.

    4. **Program może zostać uruchomiony:** Wybierz opcję, która określa, że program może być uruchamiany niezależnie od tego, czy użytkownik jest zalogowany.

8. Na stronie **wymagania** wybierz pozycję **dalej** , aby zaakceptować wartości domyślne, a następnie Ukończ pracę kreatora.

W poniższej tabeli opisano opcje wiersza polecenia określone w kroku 7.

|Opcja|Opis|
|------------|-----------------|
|**parametru**|Ustawia tryb cichy. Nie jest wymagane wprowadzanie danych przez użytkownika i nie są wyświetlane dane wyjściowe.|
|**/norestart**|Uniemożliwia Instalatorowi automatyczne wykonywanie ponownego rozruchu. Użycie tej opcji spowoduje, że program Configuration Manager będzie musiał obsługiwać ponowne uruchamianie komputera.|
|**/chainingpackage** *pakietname*|Określa nazwę pakietu, który tworzy łańcuch. Te informacje są zgłaszane z innymi informacjami sesji instalacji dla tych, którzy zarejestrowali się w programie Microsoft Program poprawy jakości obsługi klienta (CEIP). Jeśli nazwa pakietu zawiera spacje, użyj podwójnych cudzysłowów jako ograniczników; na przykład: **/chainingpackage "iloczyn łańcucha"**.|

Wykonanie tych kroków spowoduje utworzenie pakietu o nazwie .NET Framework 4.5. Program wdraża instalację dyskretną programu .NET Framework 4.5. W przypadku instalacji dyskretnej użytkownicy nie pracują z procesem instalacji, a aplikacja łańcucha musi przechwycić kod powrotny i obsłużyć ponowne uruchomienie. Zobacz [Uzyskiwanie informacji o postępie z pakietu instalacyjnego](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100)).

<a name="select_dist_point"></a>

### <a name="select-a-distribution-point"></a>Wybieranie punktu dystrybucji

Aby dystrybuować pakiet i program na komputery klienckie z serwera, należy najpierw wyznaczyć system lokacji jako punkt dystrybucji, a następnie dystrybuować pakiet do punktu dystrybucji.

Wykonując poniższe kroki, można wybrać punkt dystrybucji dla pakietu programu .NET Framework 4.5 utworzonego w poprzedniej sekcji:

1. W konsoli Configuration Manager wybierz pozycję **Biblioteka oprogramowania**.

2. W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Zarządzanie aplikacjami**, a następnie wybierz pozycję **pakiety**.

3. Z listy pakietów wybierz pakiet **.NET Framework 4,5** , który został utworzony w poprzedniej sekcji.

4. Na karcie **Narzędzia główne** w grupie **wdrożenie** wybierz pozycję **Dystrybuuj zawartość**.

5. Na karcie **Ogólne** w **Kreatorze dystrybucji zawartości**wybierz pozycję **dalej**.

6. Na stronie **miejsce docelowe zawartości** kreatora wybierz pozycję **Dodaj**, a następnie wybierz pozycję **punkt dystrybucji**.

7. W oknie dialogowym **Dodawanie punktów dystrybucji** wybierz punkty dystrybucji, które będą obsługiwać pakiet i program, a następnie wybierz **przycisk OK**.

8. Wykonaj kroki kreatora.

Pakiet zawiera teraz wszystkie informacje niezbędne do dyskretnego wdrożenia programu .NET Framework 4.5. Przed wdrożeniem pakietu i programu należy się upewnić, że został on zainstalowany w punkcie dystrybucji. Zobacz sekcję "Monitorowanie stanu zawartości" tematu [monitorowanie zawartości dystrybuowanej za pomocą Configuration Manager](https://docs.microsoft.com/configmgr/core/servers/deploy/configure/monitor-content-you-have-distributed) w bibliotece Configuration Manager dokumentacji.

<a name="deploying_package"></a>

### <a name="deploy-the-package"></a>Wdrażanie pakietu

Aby wdrożyć pakiet i program .NET Framework 4.5:

1. W konsoli Configuration Manager wybierz pozycję **Biblioteka oprogramowania**.

2. W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Zarządzanie aplikacjami**, a następnie wybierz pozycję **pakiety**.

3. Z listy pakietów wybierz utworzony pakiet o nazwie **.NET Framework 4,5**.

4. Na karcie **Narzędzia główne** w grupie **wdrożenie** wybierz pozycję **Wdróż**.

5. Na stronie **Ogólne** **Kreatora wdrażania oprogramowania**wybierz pozycję **Przeglądaj**, a następnie wybierz utworzoną wcześniej kolekcję. Wybierz pozycję **Next** (Dalej).

6. Na stronie **zawartość** kreatora sprawdź, czy jest wyświetlany punkt, z którego ma zostać rozdystrybuowane oprogramowanie, a następnie wybierz przycisk **dalej**.

7. Na stronie **Ustawienia wdrożenia** w Kreatorze upewnij się, że **Akcja** jest ustawiona na **Zainstaluj**, a **cel** jest ustawiony na wartość **wymagane**. Te wartości ustawień gwarantują, że pakiet oprogramowania będzie obowiązkowo instalowany na komputerach docelowych. Wybierz pozycję **Next** (Dalej).

8. Na stronie **Planowanie** w Kreatorze Określ, kiedy ma być zainstalowana .NET Framework. Możesz wybrać opcję **Nowy** , aby przypisać czas instalacji lub poinstruować oprogramowanie, które ma zostać zainstalowane, gdy użytkownik się zaloguje lub wyłączy lub najszybciej, jak to możliwe. Wybierz pozycję **Next** (Dalej).

9. Na stronie **środowisko użytkownika** kreatora Użyj wartości domyślnych i kliknij przycisk **dalej**.

    > [!WARNING]
    > W środowisku produkcyjnym mogą obowiązywać zasady wymagające wybrania innych ustawień harmonogramu wdrażania. Aby uzyskać informacje o tych opcjach, zobacz [Właściwości nazwy reklamy: karta harmonogram](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).

10. Na stronie **punkty dystrybucji** kreatora Użyj wartości domyślnych i kliknij przycisk **dalej**.

11. Wykonaj kroki kreatora. Postęp wdrożenia można monitorować w węźle **wdrożenia** obszaru roboczego **monitorowanie** .

Teraz pakiet zostanie wdrożony w kolekcji docelowej i rozpocznie się dyskretna instalacja programu .NET Framework 4.5. Informacje o kodach błędów instalacji .NET Framework 4,5 znajdują się w sekcji [kody powrotne](#return_codes) w dalszej części tego tematu.

<a name="resources"></a>

## <a name="resources"></a>Zasoby

Aby uzyskać więcej informacji na temat infrastruktury testowania wdrożenia pakietu redystrybucyjnego .NET Framework 4,5, zobacz następujące zasoby.

**Active Directory, DNS, DHCP:**

- [Active Directory Domain Services](/windows/desktop/ad/active-directory-domain-services)

- [System nazw domen (DNS)](/windows-server/networking/dns/dns-top)

- [Protokół DHCP](/windows-server/networking/technologies/dhcp/dhcp-top)

**SQL Server 2008:**

- [Instalowanie SQL Server 2008 (SQL Server wideo)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))

- [SQL Server 2008 — Omówienie zabezpieczeń dla administratorów bazy danych](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)

**Configuration Manager programu System Center 2012 (punkt zarządzania, punkt dystrybucji):**

- [Administrowanie lokacją dla programu System Center 2012 Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg681983%28v=technet.10%29)

- [Configuration Manager planowanie i wdrażanie pojedynczej lokacji](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb680961%28v=technet.10%29)

**Klient programu System Center 2012 Configuration Manager dla komputerów z systemem Windows:**

- [Wdrażanie klientów dla programu System Center 2012 Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg699391%28v=technet.10%29)

<a name="troubleshooting"></a>

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="log-file-locations"></a>Lokalizacje plików dziennika

Podczas instalacji .NET Framework są generowane następujące pliki dziennika:

- %temp%\Microsoft .NET Framework *wersja* \* . txt
- %temp%\Microsoft .NET Framework *wersja* \* . html

*wersja* , w której jest instalowana wersja .NET Framework, na przykład 4,5 lub 4.7.2.

Możesz również określić katalog, w którym zapisywane są pliki dziennika przy użyciu `/log` opcji wiersza polecenia w .NET Framework polecenie instalacji. Aby uzyskać więcej informacji, zobacz [.NET Framework Przewodnik wdrażania dla deweloperów](deployment-guide-for-developers.md#command-line-options).

Za pomocą narzędzia do [zbierania dzienników](https://www.microsoft.com/download/details.aspx?id=12493) można zbierać pliki dziennika .NET Framework i utworzyć skompresowany plik Cabinet (CAB), który zmniejsza rozmiar plików.

<a name="return_codes"></a>

### <a name="return-codes"></a>Kody powrotne

W poniższej tabeli wymieniono najbardziej typowe kody powrotu z programu instalacyjnego pakietu redystrybucyjnego .NET Framework 4,5. Kody powrotne są takie same dla wszystkich wersji instalatora.

Aby uzyskać linki do szczegółowych informacji, zobacz następną sekcję, [pobieranie kodów błędów](#additional_error_codes).

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

- [Kody błędów Usługa inteligentnego transferu w tle (bity)](/windows/desktop/Bits/bits-return-values)

- [Kody błędów monikera adresu URL](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145%28v=vs.85%29)

- [Kody błędów usługi WinHttp](/windows/desktop/WinHttp/error-messages)

Inne kody błędów:

- [Instalator Windows kody błędów](/windows/desktop/msi/error-codes)

- [Kody wyników agenta Windows Update](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))

## <a name="see-also"></a>Zobacz także

- [Przewodnik wdrażania dla deweloperów](deployment-guide-for-developers.md)
- [Wymagania systemowe](../get-started/system-requirements.md)
