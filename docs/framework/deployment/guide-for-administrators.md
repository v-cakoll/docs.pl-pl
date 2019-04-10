---
title: .NET Framework — Przewodnik wdrażania dla administratorów
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 41cdc3db069ecf7ea854b76ac45d4b268a357459
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309514"
---
# <a name="net-framework-deployment-guide-for-administrators"></a>.NET Framework — Przewodnik wdrażania dla administratorów
W tym artykule opisano, jak administrator systemu może wdrożyć [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i jego zależności systemowe przez sieć przy użyciu programu Microsoft System Center Configuration Manager. W tym artykule przyjęto założenie, że wszystkie docelowe komputery klienckie spełniają minimalne wymagania programu .NET Framework. Aby uzyskać listę wymagania sprzętowe i programowe dotyczące instalowania [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md).  
  
> [!NOTE]
>  Oprogramowanie wymienione w niniejszym dokumencie, w tym bez ograniczeń, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager i usługi Active Directory, objęte jest postanowieniami licencyjnymi. W tych instrukcjach przyjęto założenie, że takie postanowienia licencyjne i warunki zostały przejrzane i zaakceptowane przez właściwych licencjobiorców oprogramowania. Te instrukcje nie unieważniają żadnego postanowienia tych umów licencyjnych.  
>   
>  Aby uzyskać informacje na temat pomocy technicznej dla platformy .NET Framework, zobacz [obsługuje zasady cyklu życia programu Microsoft .NET Framework](https://go.microsoft.com/fwlink/?LinkId=196607) w witrynie Microsoft Support.  
  
 Ten temat zawiera następujące sekcje:  
  
 [Proces wdrażania](#the_deployment_process)  
 [Wdrażanie programu .NET Framework](#deploying_in_a_test_environment)  
 [Tworzenie kolekcji](#creating_a_collection)  
 [Tworzenie pakietu i programu](#creating_a_package)  
 [Wybieranie punktu dystrybucji](#select_dist_point)  
 [Wdrażanie pakietu](#deploying_package)  
[Zasoby](#resources)  
[Rozwiązywanie problemów](#troubleshooting)  
  
<a name="the_deployment_process"></a>   
## <a name="the-deployment-process"></a>Proces wdrażania  
 Gdy jest dostępna wymagana infrastruktura, należy użyć programu System Center 2012 Manager Configuration w celu wdrożenia pakietu redystrybucyjnego programu .NET Framework na komputerach w sieci. Tworzenie infrastruktury obejmuje utworzenie i zdefiniowanie pięciu podstawowych obszarów: kolekcji, pakietu i programu dla oprogramowania, punktów dystrybucji i wdrożeń.  
  
-   **Kolekcje** grup zasobów programu Configuration Manager, takich jak użytkownicy, grupy użytkowników lub komputerów, na których jest wdrożona programu .NET Framework. Aby uzyskać więcej informacji, zobacz [wprowadzenie do kolekcji w programie System Center Configuration Manager](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections) w bibliotece dokumentacji programu Configuration Manager.  
  
-   **Pakiety i programy** zazwyczaj reprezentują aplikacje do zainstalowania na komputerze klienckim, ale mogą także zawierać pojedyncze pliki, aktualizacji lub nawet polecenia. Aby uzyskać więcej informacji, zobacz [pakiety i programy w programie System Center Configuration Manager](https://docs.microsoft.com/sccm/apps/deploy-use/packages-and-programs) w bibliotece dokumentacji programu Configuration Manager.  
  
-   **Punkty dystrybucji** są przechowywania plików wymaganych do działania oprogramowania na komputery klienckie ról systemu lokacji programu Configuration Manager. Gdy klient programu Configuration Manager odbiera i przetwarza wdrożenie oprogramowania, kontaktuje się z punktem dystrybucji w celu pobrania zawartości skojarzonej z oprogramowaniem i rozpoczęcia procesu instalacji. Aby uzyskać więcej informacji, zobacz [podstawowe pojęcia związane z zarządzaniem zawartością w programie Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management) w bibliotece dokumentacji programu Configuration Manager.  
  
-   **Wdrożenia** poinstruować odpowiednie elementy członkowskie określonej kolekcji docelowej można zainstalować pakietu oprogramowania. 
  
> [!IMPORTANT]
>  Procedury opisane w tym temacie zawierają typowe ustawienia służące do tworzenia i wdrażania pakietu oraz programu i mogą nie obejmować wszystkich możliwych ustawień. Inne opcje wdrażania programu Configuration Manager, zobacz [bibliotece dokumentacji programu Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29).  
  
<a name="deploying_in_a_test_environment"></a>   
## <a name="deploying-the-net-framework"></a>Wdrażanie programu .NET Framework  
 System Center 2012 Configuration Manager można użyć do wdrożenia dyskretnej instalacji [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], gdzie użytkownicy nie oddziałują na proces instalacji. Wykonaj następujące kroki:  
  
1. [Utwórz kolekcję](#creating_a_collection).  
  
2. [Tworzenie pakietów i programów w programie .NET Framework do dystrybucji](#creating_a_package).  
  
3. [Wybierz punkt dystrybucji](#select_dist_point).  
  
4. [Wdrażanie pakietu](#deploying_package).  
  
<a name="creating_a_collection"></a>   
### <a name="create-a-collection"></a>Tworzenie kolekcji  
 W tym kroku należy wybrać komputery, na których będzie wdrażany pakiet i program, i zgrupować je w kolekcji urządzeń. Aby utworzyć kolekcję w programie Configuration Manager, można użyć bezpośrednich reguł członkostwa (elementy członkowskie kolekcji są określane ręcznie) lub reguł zapytań (program Configuration Manager określa elementy członkowskie kolekcji na podstawie określonych kryteriów). Aby uzyskać więcej informacji na temat reguł członkostwa, w tym o zapytaniach i regułach bezpośrednich, zobacz [wprowadzenie do kolekcji w programie System Center Configuration Manager](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections) w bibliotece dokumentacji programu Configuration Manager.  
  
 Aby utworzyć kolekcję:  
  
1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność**.  
  
2. W **zasoby i zgodność** obszaru roboczego, wybierz **kolekcje urządzeń**.  
  
3. Na **Home** karcie **Utwórz** grupy, wybierz **Utwórz kolekcję urządzeń**.  
  
4. Na **ogólne** strony **Kreatora tworzenia kolekcji urządzeń**, wprowadź nazwę kolekcji.  
  
5. Wybierz **Przeglądaj** określić kolekcję ograniczającą.  
  
6. Na **reguł członkostwa** wybierz **Dodaj regułę**, a następnie wybierz **reguły bezpośredniej** otworzyć **bezpośrednie Kreatora tworzenia reguły członkostwa**. Wybierz **dalej**.  
  
7. Na **wyszukiwanie zasobów** stronie **klasy zasobów** wybierz **zasób systemowy**. W **nazwa atrybutu** wybierz **nazwa**. W **wartość** wprowadź `%`, a następnie wybierz **dalej**.  
  
8. Na **Wybieranie zasobów** strony, zaznacz pole wyboru dla każdego komputera, który chcesz wdrożyć program .NET Framework do. Wybierz **dalej**, a następnie ukończ jego pracę.  
  
9. Na **reguł członkostwa** strony **Kreatora tworzenia kolekcji urządzeń**, wybierz **dalej**, a następnie ukończ jego pracę.  
  
<a name="creating_a_package"></a>   
### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a>Tworzenie pakietu i programu dla redystrybucyjnego pakietu programu .NET Framework  
 Wykonanie poniższych kroków umożliwia ręczne utworzenie pakietu redystrybucyjnego programu .NET Framework. Pakiet będzie zawierał określone parametry instalacji programu .NET Framework oraz lokalizację, z której pakiet będzie dystrybuowany na komputery docelowe.  
  
 Aby utworzyć pakiet:  
  
1. W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania**.  
  
2. W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **Zarządzanie aplikacjami**, a następnie wybierz **pakietów**.  
  
3. Na **Home** na karcie **Utwórz** grupy, wybierz **tworzenia pakietu**.  
  
4. Na **pakietu** strony **Kreatora tworzenia pakietu i programu**, wprowadź następujące informacje:  
  
    -   Nazwa: `.NET Framework 4.5`  
  
    -   Producent: `Microsoft`  
  
    -   Język. `English (US)`  
  
5. Wybierz **ten pakiet zawiera pliki źródłowe**, a następnie wybierz **Przeglądaj** wybrać lokalny lub zdalny folder zawierający pliki instalacyjne programu .NET Framework. Po wybraniu folderu, wybierz **OK**, a następnie wybierz **dalej**.  
  
6. Na **typ programu** strony kreatora, wybierz **Program standardowy**, a następnie wybierz **dalej**.  
  
7. Na **Program** strony **Kreatora tworzenia pakietu i programu**, wprowadź następujące informacje:  
  
    1.  **Nazwa:** `.NET Framework 4.5`  
  
    2.  **Wiersz polecenia:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (Opcje wiersza polecenia są opisane w tabeli po wykonaniu tych kroków)  
  
    3.  **Uruchom polecenie:** Wybierz **ukryte**.  
  
    4.  **Program może zostać uruchomiony:** Wybierz opcję określającą, czy program można uruchomić niezależnie od tego, czy użytkownik jest zalogowany.  
  
8. Na **wymagania** wybierz **dalej** aby zaakceptować wartości domyślne, a następnie ukończ jego pracę.  
  
 W poniższej tabeli opisano opcje wiersza polecenia określone w kroku 7.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/q**|Ustawia tryb cichy. Nie jest wymagane wprowadzanie danych przez użytkownika i nie są wyświetlane dane wyjściowe.|  
|**/norestart**|Uniemożliwia Instalatorowi automatyczne wykonywanie ponownego rozruchu. Użycie tej opcji spowoduje, że program Configuration Manager będzie musiał obsługiwać ponowne uruchamianie komputera.|  
|**/chainingpackage** *PackageName*|Określa nazwę pakietu, który tworzy łańcuch. Te informacje są zgłaszane wraz z innymi informacjami sesji instalacji dla tych, którzy podpisali [Program poprawy jakości środowiska Microsoft klienta (CEIP)](https://go.microsoft.com/fwlink/p/?LinkId=248244). Jeśli nazwa pakietu zawiera spacje, należy użyć podwójnego cudzysłowu jako ogranicznika; na przykład: **chainingpackage "Chaining Product"**.|  
  
 Wykonanie tych kroków spowoduje utworzenie pakietu o nazwie .NET Framework 4.5. Program wdraża instalację dyskretną programu .NET Framework 4.5. W trakcie instalacji dyskretnej użytkownicy nie oddziałują na proces instalacji, a aplikacja łańcuchowa musi przechwytywać kod powrotny i obsługiwać ponowny rozruch; zobacz [uzyskiwanie informacji o postępie z pakietu instalacyjnego](https://go.microsoft.com/fwlink/?LinkId=179606).  
 
<a name="select_dist_point"></a>   
### <a name="select-a-distribution-point"></a>Wybieranie punktu dystrybucji  
 Aby dystrybuować pakiet i program na komputery klienckie z serwera, należy najpierw wyznaczyć system lokacji jako punkt dystrybucji, a następnie dystrybuować pakiet do punktu dystrybucji.  
  
 Wykonując poniższe kroki, można wybrać punkt dystrybucji dla pakietu programu .NET Framework 4.5 utworzonego w poprzedniej sekcji:  
  
1. W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania**.  
  
2. W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **Zarządzanie aplikacjami**, a następnie wybierz **pakietów**.  
  
3. Z listy pakietów wybierz pakiet **.NET Framework 4.5** utworzoną w poprzedniej sekcji.  
  
4. Na **Home** na karcie **wdrożenia** grupy, wybierz **Dystrybuuj zawartość**.  
  
5. Na **ogólne** karcie **kreatora dystrybucji zawartości**, wybierz **dalej**.  
  
6. Na **miejsce docelowe zawartości** strony kreatora, wybierz **Dodaj**, a następnie wybierz **punktu dystrybucji**.  
  
7. W **Dodaj punkty dystrybucji** okna dialogowego Wybierz punkty dystrybucji, który będzie hostować pakiet i program, a następnie wybierz **OK**.  
  
8. Ukończ pracę kreatora.  
  
 Pakiet zawiera teraz wszystkie informacje niezbędne do dyskretnego wdrożenia programu .NET Framework 4.5. Przed przystąpieniem do wdrażania pakietów i programów, sprawdź, czy został on zainstalowany w punkcie dystrybucji; zobacz sekcję "Monitorowanie zawartości" [monitorowanie zawartości dystrybuowanej za pomocą System Center Configuration Manager](https://docs.microsoft.com/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed) w bibliotece dokumentacji programu Configuration Manager.  
  
<a name="deploying_package"></a>   
### <a name="deploy-the-package"></a>Wdrażanie pakietu  
 Aby wdrożyć pakiet i program .NET Framework 4.5:  
  
1. W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania**.  
  
2. W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **Zarządzanie aplikacjami**, a następnie wybierz **pakietów**.  
  
3. Z listy pakietów wybierz pakiet utworzony pod nazwą **.NET Framework 4.5**.  
  
4. Na **Home** na karcie **wdrożenia** grupy, wybierz **Wdróż**.  
  
5. Na **ogólne** strony **Kreatora wdrażania oprogramowania**, wybierz **Przeglądaj**, a następnie wybierz kolekcję, do której została utworzona wcześniej. Wybierz **dalej**.  
  
6. Na **zawartości** strony kreatora, sprawdź, czy jest wyświetlany punkt, z którego chcesz dystrybuować oprogramowanie, a następnie wybierz **dalej**.  
  
7. Na **ustawienia wdrażania** strony kreatora, upewnij się, że **akcji** jest ustawiona na **zainstalować**, i **przeznaczenia** jest ustawiona na **Wymagane**. Te wartości ustawień gwarantują, że pakiet oprogramowania będzie obowiązkowo instalowany na komputerach docelowych. Wybierz **dalej**.  
  
8. Na **Planowanie** strony kreatora, określić, kiedy .NET Framework do zainstalowania. Możesz wybrać **New** Aby przypisać godzinę instalacji, ale można też oprogramowanie w celu zainstalowania, gdy użytkownik loguje się na wyloguje lub jak najszybciej. Wybierz **dalej**.  
  
9. Na **komfortu** strony w Kreatorze Użyj wartości domyślnych i wybierz **dalej**.  
  
> [!WARNING]
> W środowisku produkcyjnym mogą obowiązywać zasady wymagające wybrania innych ustawień harmonogramu wdrażania. Aby uzyskać informacje o tych opcjach, zobacz [właściwości nazwy reklamy: Zaplanuj kartę](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).
  
10. Na **punktów dystrybucji** strony w Kreatorze Użyj wartości domyślnych i wybierz **dalej**.  
  
11. Ukończ pracę kreatora. Możesz monitorować postęp wdrażania **wdrożeń** węźle **monitorowanie** obszaru roboczego.  
  
 Teraz pakiet zostanie wdrożony w kolekcji docelowej i rozpocznie się dyskretna instalacja programu .NET Framework 4.5. Aby uzyskać informacje o kodach błędów instalacji programu .NET Framework 4.5, zobacz [kody powrotne](#return_codes) w dalszej części tego tematu.  
  
<a name="resources"></a>   
## <a name="resources"></a>Zasoby  
 Aby uzyskać więcej informacji dotyczących infrastruktury do testowania wdrożenia [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] do dystrybucji pakietu, zobacz następujące zasoby.  
  
 **Active Directory, DNS, DHCP:**  
  
-   [Usługi domenowe Active Directory](/windows/desktop/ad/active-directory-domain-services)  
  
-   [System nazw domen (DNS)](/windows-server/networking/dns/dns-top)  
  
-   [Protokół DHCP](/windows-server/networking/technologies/dhcp/dhcp-top)  
  
 **SQL Server 2008:**  
  
-   [Instalowanie programu SQL Server 2008 (SQL Server wideo)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))  
  
-   [Omówienie zabezpieczeń usługi SQL Server 2008 dla administratorów baz danych](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)  
  
 **System Center 2012 Configuration Manager (punkt zarządzania, punkt dystrybucji):**  
  
-   [Administrowanie lokacją dla programu System Center 2012 Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg681983%28v=technet.10%29)  
  
-   [Menedżer konfiguracji pojedyncza witryna planowania i wdrażania](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb680961%28v=technet.10%29)  
  
 **Klient programu System Center 2012 Configuration Manager dla komputerów z systemem Windows:**  
  
-   [Wdrażanie klientów dla programu System Center 2012 Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg699391%28v=technet.10%29)  
  
<a name="troubleshooting"></a>   
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
  
### <a name="log-file-locations"></a>Lokalizacje plików dziennika  
 Następujące pliki dziennika są generowane podczas instalacji .NET Framework:  
  
 .NET framework %Temp%\Microsoft *wersji*\*txt  
 .NET framework %Temp%\Microsoft *wersji*\*HTML  
  
 gdzie *wersji* jest wersja programu .NET Framework, który instalujesz, takie jak w wersji 4.5 lub 4.7.2.  
 
 Możesz również określić katalog, w dzienniku, które pliki są zapisywane przy użyciu `/log` opcji wiersza polecenia w poleceniu instalacji .NET Framework. Aby uzyskać więcej informacji, zobacz [.NET Framework — przewodnik wdrażania dla deweloperów](deployment-guide-for-developers.md#command-line-options). 
 
 Możesz użyć [narzędzie do zbierania dzienników](https://www.microsoft.com/download/details.aspx?id=12493) zbierać pliki dziennika w programie .NET Framework i Utwórz plik skompresowany plik cabinet (cab), która zmniejsza rozmiar plików.  
  
<a name="return_codes"></a>   
### <a name="return-codes"></a>Kody powrotne  
 W poniższej tabeli wymieniono najczęściej występujące kody powrotne z [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] programu instalacyjnego redystrybucyjnego pakietu. Kody powrotne są takie same dla wszystkich wersji instalatora.  
  
 Dla łącza do szczegółowych informacji, zobacz następną sekcję, [kody błędów pobierania](#additional_error_codes).  
  
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
  
-   [Kody błędów Intelligent Transfer Service (BITS) w tle](/windows/desktop/Bits/bits-return-values)  
  
-   [Kody błędu krótkiej nazwy adresu URL](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145%28v=vs.85%29)  
  
-   [Kody błędów usługi WinHttp](/windows/desktop/WinHttp/error-messages)  
  
 Inne kody błędów:  
  
-   [Kody błędów usługi Instalator Windows](/windows/desktop/msi/error-codes)

-   [Kody wyników programu Windows Update Agent](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))

## <a name="see-also"></a>Zobacz także

- [Przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md)
- [Wymagania systemowe](../../../docs/framework/get-started/system-requirements.md)
