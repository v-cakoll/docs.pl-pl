---
title: .NET Framework — Przewodnik wdrażania dla administratorów
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b4c2d4205e87d8be21f82eaf74b17e316d9057e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="net-framework-deployment-guide-for-administrators"></a>.NET Framework — Przewodnik wdrażania dla administratorów
W tym artykule opisano, jak administrator systemu może wdrożyć [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i jego zależności systemu przez sieć przy użyciu programu Microsoft System Center Configuration Manager. W tym artykule przyjęto założenie, że wszystkie docelowe komputery klienckie spełniają minimalne wymagania programu .NET Framework. Aby uzyskać listę wymagania sprzętowe i programowe instalacji [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md).  
  
> [!NOTE]
>  Oprogramowania wymienione w niniejszym dokumencie, w tym bez ograniczeń, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager i usługi Active Directory, jest każda zgodnie z postanowieniami licencyjnymi. W tych instrukcjach przyjęto założenie, że takie postanowienia licencyjne i warunki zostały przejrzane i zaakceptowane przez właściwych licencjobiorców oprogramowania. Te instrukcje nie unieważniają żadnego postanowienia tych umów licencyjnych.  
>   
>  Aby uzyskać informacje o pomocy technicznej dla programu .NET Framework, zobacz [obsługuje zasady cyklu pomocy firmy Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=196607) w witrynie sieci Web Microsoft Support.  
  
 Ten temat zawiera następujące sekcje:  
  
 [Proces wdrażania](#the_deployment_process)  
 [Wdrażanie programu .NET Framework](#deploying_in_a_test_environment)  
 [Tworzenie kolekcji](#creating_a_collection)  
 [Tworzenie pakietów i programów](#creating_a_package)  
 [Wybierz punkt dystrybucji](#select_dist_point)  
 [Wdrażanie pakietu](#deploying_package)  
[Zasoby](#resources)  
[Rozwiązywanie problemów](#troubleshooting)  
  
<a name="the_deployment_process"></a>   
## <a name="the-deployment-process"></a>Proces wdrażania  
 Gdy jest dostępna wymagana infrastruktura, należy użyć programu System Center 2012 Manager Configuration w celu wdrożenia pakietu redystrybucyjnego programu .NET Framework na komputerach w sieci. Tworzenie infrastruktury obejmuje utworzenie i zdefiniowanie pięciu podstawowych obszarów: kolekcji, pakietu i programu dla oprogramowania, punktów dystrybucji i wdrożeń.  
  
-   **Kolekcje** grup zasobów programu Configuration Manager, takich jak użytkownicy, grupy użytkowników lub komputerów, na których jest wdrożona programu .NET Framework. Aby uzyskać więcej informacji, zobacz [kolekcje w programie Configuration Manager](http://technet.microsoft.com/library/gg682169.aspx) w bibliotece dokumentacji programu Configuration Manager.  
  
-   **Pakiety i programy** zazwyczaj reprezentują aplikacje do zainstalowania na komputerze klienckim, ale może także zawierać pojedyncze pliki, aktualizacji lub nawet poszczególnych poleceń. Aby uzyskać więcej informacji, zobacz [pakietów i programów w programie Configuration Manager](http://technet.microsoft.com/library/gg699369.aspx) w bibliotece dokumentacji programu Configuration Manager.  
  
-   **Punkty dystrybucji** są role systemu, które przechowują pliki wymagane do działania oprogramowania na komputerach klienckich w lokacji programu Configuration Manager. Gdy klient programu Configuration Manager odbiera i przetwarza wdrożenie oprogramowania, kontaktuje się z punktem dystrybucji w celu pobrania zawartości skojarzonej z oprogramowaniem i rozpoczęcia procesu instalacji. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zarządzania zawartością w programie Configuration Manager](http://technet.microsoft.com/library/gg682083.aspx) w bibliotece dokumentacji programu Configuration Manager.  
  
-   **Wdrożenia** poinstruować odpowiednich członków kolekcji określone miejsce docelowe instalacji pakietu oprogramowania. Aby uzyskać więcej informacji, zobacz [jak wdrażać aplikacje w programie Configuration Manager](http://technet.microsoft.com/library/gg682082.aspx) w bibliotece dokumentacji programu Configuration Manager.  
  
> [!IMPORTANT]
>  Procedury opisane w tym temacie zawierają typowe ustawienia służące do tworzenia i wdrażania pakietu oraz programu i mogą nie obejmować wszystkich możliwych ustawień. Inne opcje wdrożenia programu Configuration Manager, zobacz [biblioteka dokumentacji programu Configuration Manager](http://technet.microsoft.com/library/gg682041.aspx).  
  
<a name="deploying_in_a_test_environment"></a>   
## <a name="deploying-the-net-framework"></a>Wdrażanie programu .NET Framework  
 System Center 2012 Configuration Manager można użyć do wdrożenia instalacji dyskretnej [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], których użytkownicy nie wchodzą w interakcje z procesu instalacji. Wykonaj następujące kroki:  
  
1.  [Utwórz kolekcję](#creating_a_collection).  
  
2.  [Tworzenie pakietów i programów dla programu .NET Framework redistributable](#creating_a_package).  
  
3.  [Wybierz punkt dystrybucji](#select_dist_point).  
  
4.  [Wdrażanie pakietu](#deploying_package).  
  
<a name="creating_a_collection"></a>   
### <a name="create-a-collection"></a>Tworzenie kolekcji  
 W tym kroku należy wybrać komputery, na których będzie wdrażany pakiet i program, i zgrupować je w kolekcji urządzeń. Aby utworzyć kolekcję w programie Configuration Manager, można użyć bezpośrednich reguł członkostwa (elementy członkowskie kolekcji są określane ręcznie) lub reguł zapytań (program Configuration Manager określa elementy członkowskie kolekcji na podstawie określonych kryteriów). Aby uzyskać więcej informacji na temat reguł członkostwa, w tym zapytania i bezpośredniego reguły, zobacz [wprowadzenie do kolekcji w programie Configuration Manager](http://technet.microsoft.com/library/gg682177.aspx) w bibliotece dokumentacji programu Configuration Manager.  
  
 Aby utworzyć kolekcję:  
  
1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność**.  
  
2.  W **zasoby i zgodność** obszaru roboczego wybierz **kolekcje urządzeń**.  
  
3.  Na **Home** karcie **Utwórz** grupy, wybierz **Utwórz kolekcję urządzeń**.  
  
4.  Na **ogólne** strony **Kreatora tworzenia kolekcji urządzeń**, wprowadź nazwę kolekcji.  
  
5.  Wybierz **Przeglądaj** do określenia kolekcji ograniczającej.  
  
6.  Na **reguł członkostwa** wybierz pozycję **Dodaj regułę**, a następnie wybierz pozycję **reguły bezpośredniej** otworzyć **bezpośredniego Kreatora tworzenia reguły członkostwa**. Wybierz **dalej**.  
  
7.  Na **wyszukiwanie zasobów** strony w **klasy zasobów** wybierz **zasób systemowy**. W **nazwa atrybutu** wybierz **nazwa**. W **wartość** wprowadź `%`, a następnie wybierz pozycję **dalej**.  
  
8.  Na **zasobów wybierz** strony, zaznacz pole wyboru dla każdego komputera, który chcesz wdrożyć .NET Framework. Wybierz **dalej**, a następnie Zakończ pracę kreatora.  
  
9. Na **reguł członkostwa** strony **Kreatora tworzenia kolekcji urządzeń**, wybierz **dalej**, a następnie Zakończ pracę kreatora.  
  
 Aby uzyskać więcej informacji o kolekcjach, zobacz [kolekcje w programie Configuration Manager](http://technet.microsoft.com/library/bb693730.aspx) w bibliotece dokumentacji programu Configuration Manager.  
  
<a name="creating_a_package"></a>   
### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a>Tworzenie pakietu i programu dla redystrybucyjnego pakietu programu .NET Framework  
 Wykonanie poniższych kroków umożliwia ręczne utworzenie pakietu redystrybucyjnego programu .NET Framework. Pakiet będzie zawierał określone parametry instalacji programu .NET Framework oraz lokalizację, z której pakiet będzie dystrybuowany na komputery docelowe.  
  
 Aby utworzyć pakiet:  
  
1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania**...  
  
2.  W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **Zarządzanie aplikacjami**, a następnie wybierz pozycję **pakiety**.  
  
3.  Na **Home** karcie **Utwórz** grupy, wybierz **tworzenia pakietu**.  
  
4.  Na **pakietu** strony **Kreatora tworzenia pakietu i programu**, wprowadź następujące informacje:  
  
    -   Nazwa: `.NET Framework 4.5`  
  
    -   Producent: `Microsoft`  
  
    -   Język. `English (US)`  
  
5.  Wybierz **ten pakiet zawiera pliki źródłowe**, a następnie wybierz pozycję **Przeglądaj** do wybierz lokalnego lub sieciową folderu zawierającego pliki instalacyjne programu .NET Framework. Po wybraniu folderu, wybierz **OK**, a następnie wybierz pozycję **dalej**.  
  
6.  Na **typu programu** strony kreatora wybierz **Program standardowy**, a następnie wybierz pozycję **dalej**.  
  
7.  Na **Program** strony **Kreatora tworzenia pakietu i programu**, wprowadź następujące informacje:  
  
    1.  **Nazwa:** `.NET Framework 4.5`  
  
    2.  **Wiersz polecenia:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (Opcje wiersza polecenia są opisane w tabeli po wykonaniu tych kroków)  
  
    3.  **Instalacja:** wybierz **ukryte**.  
  
    4.  **Program może zostać uruchomiony:** wybierz opcję określającą, czy program można uruchomić niezależnie od tego, czy użytkownik jest zalogowany.  
  
8.  Na **wymagania** wybierz pozycję **dalej** można zaakceptować wartości domyślne, a następnie Zakończ pracę kreatora.  
  
 W poniższej tabeli opisano opcje wiersza polecenia określone w kroku 7.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/q**|Ustawia tryb cichy. Nie jest wymagane wprowadzanie danych przez użytkownika i nie są wyświetlane dane wyjściowe.|  
|**/ norestart**|Uniemożliwia Instalatorowi automatyczne wykonywanie ponownego rozruchu. Użycie tej opcji spowoduje, że program Configuration Manager będzie musiał obsługiwać ponowne uruchamianie komputera.|  
|**/chainingpackage** *PackageName*|Określa nazwę pakietu, który tworzy łańcuch. Te informacje były zgłaszane z innych informacji o sesji instalacji dla tych, którzy zalogowali się [Program poprawy jakości obsługi programu Microsoft klienta (CEIP)](http://go.microsoft.com/fwlink/p/?LinkId=248244). Jeśli nazwa pakietu zawiera spacje, użyj podwójnych cudzysłowów prostych jako ograniczników; na przykład: **/chainingpackage "Łańcucha produktu"**.|  
  
 Wykonanie tych kroków spowoduje utworzenie pakietu o nazwie .NET Framework 4.5. Program wdraża instalację dyskretną programu .NET Framework 4.5. W przypadku instalacji dyskretnej użytkownicy nie interakcji z procesu instalacji i CBC aplikacja ma kod powrotny przechwytywania i ponowne uruchomienie; zobacz [uzyskiwanie informacji o postępie z pakietu instalacyjnego](http://go.microsoft.com/fwlink/?LinkId=179606).  
 
<a name="select_dist_point"></a>   
### <a name="select-a-distribution-point"></a>Wybieranie punktu dystrybucji  
 Aby dystrybuować pakiet i program na komputery klienckie z serwera, należy najpierw wyznaczyć system lokacji jako punkt dystrybucji, a następnie dystrybuować pakiet do punktu dystrybucji.  
  
 Wykonując poniższe kroki, można wybrać punkt dystrybucji dla pakietu programu .NET Framework 4.5 utworzonego w poprzedniej sekcji:  
  
1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania**.  
  
2.  W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **Zarządzanie aplikacjami**, a następnie wybierz pozycję **pakiety**.  
  
3.  Wybierz pakiet z listy pakietów **.NET Framework 4.5** utworzoną w poprzedniej sekcji.  
  
4.  Na **Home** karcie **wdrożenia** grupy, wybierz **Dystrybuuj zawartość**.  
  
5.  Na **ogólne** karcie **kreatora dystrybucji zawartości**, wybierz **dalej**.  
  
6.  Na **miejsce docelowe zawartości** strony kreatora wybierz **Dodaj**, a następnie wybierz pozycję **punktu dystrybucji**.  
  
7.  W **punktów dystrybucji Dodaj** oknie dialogowym Wybierz punkty dystrybucji, który hosta pakiet i program, a następnie wybierz **OK**.  
  
8.  Ukończ pracę kreatora.  
  
 Pakiet zawiera teraz wszystkie informacje niezbędne do dyskretnego wdrożenia programu .NET Framework 4.5. Przed przystąpieniem do wdrażania pakietów i programów, sprawdź, czy został zainstalowany w punkcie dystrybucji; zobacz sekcję "Monitor zawartość" [operacje i Obsługa zarządzania zawartością w programie Configuration Manager](http://technet.microsoft.com/library/gg712694.aspx#BKMK_MonitorContent) w bibliotece dokumentacji programu Configuration Manager.  
  
<a name="deploying_package"></a>   
### <a name="deploy-the-package"></a>Wdrażanie pakietu  
 Aby wdrożyć pakiet i program .NET Framework 4.5:  
  
1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania**.  
  
2.  W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **Zarządzanie aplikacjami**, a następnie wybierz pozycję **pakiety**.  
  
3.  Z listy pakietów, wybierz pakiet utworzony o nazwie **.NET Framework 4.5**.  
  
4.  Na **Home** karcie **wdrożenia** grupy, wybierz **Wdróż**.  
  
5.  Na **ogólne** strony **Kreatora wdrażania oprogramowania**, wybierz **Przeglądaj**, a następnie wybierz kolekcję, do której został utworzony wcześniej. Wybierz **dalej**.  
  
6.  Na **zawartości** strony kreatora, sprawdź, czy jest wyświetlany punkt, z którego ma być dystrybucji oprogramowania, a następnie wybierz **dalej**.  
  
7.  Na **ustawienia wdrażania** strony kreatora upewnij się, że **akcji** ustawiono **zainstalować**, i **celu** ma ustawioną wartość **Wymagane**. Te wartości ustawień gwarantują, że pakiet oprogramowania będzie obowiązkowo instalowany na komputerach docelowych. Wybierz **dalej**.  
  
8.  Na **Planowanie** strony kreatora, określić, kiedy .NET Framework do zainstalowania. Możesz wybrać **nowy** przypisywania czas instalacji, lub poinstruować oprogramowania do zainstalowania podczas logowania użytkownika na lub wyłączyć lub tak szybko, jak to możliwe. Wybierz **dalej**.  
  
9. Na **środowisko użytkownika** kreatora Użyj domyślnej wartości i wybierz **dalej**.  
  
    > [!WARNING]
    >  W środowisku produkcyjnym mogą obowiązywać zasady wymagające wybrania innych ustawień harmonogramu wdrażania. Aby uzyskać informacje o tych opcjach, zobacz [anonsu nazwa właściwości: kartę Harmonogram](http://technet.microsoft.com/library/bb694016.aspx) w bibliotece TechNet.  
  
10. Na **punktów dystrybucji** kreatora Użyj domyślnej wartości i wybierz **dalej**.  
  
11. Ukończ pracę kreatora. Możesz monitorować postęp wdrażania w **wdrożeń** węzła **monitorowanie** obszaru roboczego.  
  
 Teraz pakiet zostanie wdrożony w kolekcji docelowej i rozpocznie się dyskretna instalacja programu .NET Framework 4.5. Aby uzyskać informacje na temat kody błędów instalacji programu .NET Framework 4.5, zobacz [kody powrotne](#return_codes) później w tym temacie.  
  
<a name="resources"></a>   
## <a name="resources"></a>Zasoby  
 Aby uzyskać więcej informacji dotyczących infrastruktury do testowania wdrożenia [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] do dystrybucji pakietu, zobacz następujące zasoby.  
  
 **Usługi Active Directory, DNS, DHCP:**  
  
-   [Usługi domenowe Active Directory systemu Windows Server 2008](http://technet.microsoft.com/library/dd378891.aspx)  
  
-   [Serwer DNS](http://technet.microsoft.com/library/cc732997.aspx)  
  
-   [Serwer DHCP](http://technet.microsoft.com/library/cc896553.aspx)  
  
 **Program SQL Server 2008:**  
  
-   [Instalowanie programu SQL Server 2008 (SQL Server wideo)](http://technet.microsoft.com/library/dd299415.aspx)  
  
-   [Omówienie usług SQL Server 2008 zabezpieczeń dla administratorów bazy danych](http://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)  
  
 **System Center 2012 Configuration Manager, (punkt zarządzania, punkt dystrybucji):**  
  
-   [Administrowanie witryną dla programu System Center 2012 Configuration Manager](http://technet.microsoft.com/library/gg681983.aspx)  
  
-   [Menedżera konfiguracji pojedynczej lokacji planowania i wdrażania](http://technet.microsoft.com/library/bb680961.aspx)  
  
 **Klient programu System Center 2012 Configuration Manager dla komputerów z systemem Windows:**  
  
-   [Wdrażanie klientów programu System Center 2012 Configuration Manager](http://technet.microsoft.com/library/gg699391.aspx)  
  
<a name="troubleshooting"></a>   
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
  
### <a name="log-file-locations"></a>Lokalizacje plików dziennika  
 Następujące pliki dziennika są generowane podczas instalacji platformy .NET Framework:  
  
 .NET framework %Temp%\Microsoft *wersji*\*txt  
 .NET framework %Temp%\Microsoft *wersji*\*.html  
  
 gdzie *wersji* jest to wersja platformy .NET, który użytkownik instaluje, takich jak 4.5 lub 4.7.2.  
 
 Można również określić katalog do dziennika, które pliki zostały napisane przy użyciu `/log` opcji wiersza polecenia do polecenia instalacji platformy .NET Framework. Aby uzyskać więcej informacji, zobacz [.NET Framework — przewodnik wdrażania dla deweloperów](deployment-guide-for-developers.md#command-line-options). 
 
 Można użyć [narzędzie do zbierania dzienników](https://www.microsoft.com/download/details.aspx?id=12493) Aby zbierać pliki dziennika .NET Framework i utworzyć plik skompresowany plik cabinet (cab), które zmniejsza rozmiar plików.  
  
<a name="return_codes"></a>   
### <a name="return-codes"></a>Kody powrotne  
 W poniższej tabeli wymieniono zwraca najbardziej typowe kody z [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalacji pakietu redystrybucyjnego programu. Kody powrotne są takie same dla wszystkich wersji instalatora.  
  
 Dla łącza, aby uzyskać szczegółowe informacje, zobacz następną sekcję, [Pobierz kody błędów](#additional_error_codes).  
  
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
  
-   [Kody błędów Background Intelligent Transfer Service (BITS)](http://msdn.microsoft.com/library/aa362823.aspx)  
  
-   [Kody błędów moniker adresu URL](http://msdn.microsoft.com/library/ms775145.aspx)  
  
-   [Kody błędów WinHttp](http://msdn.microsoft.com/library/aa383770.aspx)  
  
 Inne kody błędów:  
  
-   [Kody błędów Instalatora Windows](http://msdn.microsoft.com/library/aa368542.aspx)  
  
-   [Kody wyników programu Windows Update Agent](http://technet.microsoft.com/library/cc720442.aspx)  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [Wymagania systemowe](../../../docs/framework/get-started/system-requirements.md)
