---
title: 'Porady: konfigurowanie usług aplikacji klienta'
ms.date: 03/30/2017
helpviewer_keywords:
- client application services, configuring
ms.assetid: 34a8688a-a32c-40d3-94be-c8e610c6a4e8
ms.openlocfilehash: 6f754a2a66187ac94d31d0d5a3a665c969652d26
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2018
ms.locfileid: "48846516"
---
# <a name="how-to-configure-client-application-services"></a>Porady: konfigurowanie usług aplikacji klienta
W tym temacie opisano, jak używać programu Visual Studio **projektanta projektu** Włączanie i konfigurowanie usług aplikacji klienta. Usługi aplikacji klienta można użyć do weryfikowania użytkowników i pobierania ról użytkownika i ustawienia z istniejącego [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] usługi aplikacji. Po przeprowadzeniu konfiguracji, jest dostępne włączone usługi w kodzie aplikacji zgodnie z opisem w [przegląd usług aplikacji klienta](../../../docs/framework/common-client-technologies/client-application-services-overview.md). Aby uzyskać więcej informacji na temat [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] usługi aplikacji, zobacz [przegląd usług aplikacji ASP.NET](https://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).  
  
 Można włączyć i skonfigurować usługi aplikacji klienta na **usług** strony **projektanta projektu**. **Usług** strona aktualizuje wartości w pliku App.config projektu. Aby uzyskać dostęp do **projektanta projektu**, użyj **właściwości** polecenie **projektu** menu. Aby uzyskać więcej informacji na temat **usług** stronie, zobacz [Strona usług, Projektant projektu](/visualstudio/ide/reference/services-page-project-designer).  
  
 Poniższa procedura opisuje sposób przeprowadzania podstawowej konfiguracji dla usług aplikacji klienta. Zaawansowana konfiguracja, które opcje są opisane w kolejnych sekcjach.  
  
### <a name="to-configure-client-application-services"></a>Aby skonfigurować usługi aplikacji klienta  
  
1.  W **Eksploratora rozwiązań**, wybierz węzeł projektu i następnie **projektu** menu, kliknij przycisk **właściwości**.  
  
     **Projektanta projektu** pojawia się.  
  
2.  Kliknij przycisk **usług** kartę. **Usług** zostanie wyświetlona strona, jak pokazano na poniższej ilustracji.  
  
     ![Na karcie usług w Projektancie projektu](../../../docs/framework/common-client-technologies/media/casdesigner.png "casdesigner")  
  
3.  Na **usług** wybierz opcję **włączyć usługi aplikacji klienckiej**.  
  
    > [!NOTE]
    >  Usługi aplikacji klienta wymaga pełnej wersji programu .NET Framework i nie są obsługiwane w programie .NET Framework Client Profile. Jeśli **włączyć usługi aplikacji klienckiej** pole wyboru jest wyłączone, upewnij się, że **platformę docelową** jest ustawiony do wersji programu .NET Framework 3.5 lub nowszej. Aby wyświetlić **platformę docelową** ustawienie w języku C#, otwórz projektanta projektu, a następnie kliknij przycisk **aplikacji** strony. Aby wyświetlić **platformę docelową** ustawienie w języku Visual Basic, otwórz projektanta projektu, kliknij przycisk **skompilować** strony, a następnie kliknij przycisk **zaawansowane opcje kompilacji**.  
  
4.  Wybierz **Użyj uwierzytelniania formularzy** Jeśli planujesz własnych kontrolek logowania lub okno dialogowe, lub wybierz **uwierzytelniania Windows użyj** do używania tożsamości dostarczonych przez system operacyjny. Aby uzyskać więcej informacji, zobacz [przegląd usług aplikacji klienta](../../../docs/framework/common-client-technologies/client-application-services-overview.md).  
  
    > [!NOTE]
    >  Jeśli wybierzesz **uwierzytelniania Windows użyj**, usługi aplikacji klienta zostaną automatycznie skonfigurowane do użycia bazę danych programu SQL Server Compact. Jest to wskazywane w **Zaawansowane ustawienia dla usług** okno dialogowe, zgodnie z opisem w następnej sekcji. Jeśli wybierzesz opcję **użycie formularza uwierzytelniania**, **Użyj niestandardowego ciągu połączenia** ustawienia nie zostaną automatycznie wyczyszczone. To może spowodować błędy, jeśli [!INCLUDE[ssEW](../../../includes/ssew-md.md)] bazy danych został już wygenerowany do użycia z usługą uwierzytelniania Windows. Aby naprawić te błędy, wyczyść **Użyj niestandardowego ciągu połączenia** w **Zaawansowane ustawienia dla usług** okno dialogowe.  
  
5.  W przypadku wybrania **użycie formularza uwierzytelniania**w **lokalizacji usługi uwierzytelniania** pola, określ adres URL hosta usługi nie zawiera nazwy pliku. Projektant automatycznie dołączy nazwę standardowego pliku (Authentication_JSON_AppService.axd), gdy go zapisuje wartości do pliku konfiguracji.  
  
6.  Opcjonalnie Jeśli została wybrana **użycie formularza uwierzytelniania**, można określić wartość w **Dostawca poświadczeń** pole. Dostawca poświadczeń musi implementować <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> interfejsu. Za pomocą dostawcy poświadczeń, można oddzielić interfejs użytkownika logowania z innym kodem aplikacji. Dzięki temu można utworzyć okno dialogowe pojedynczego logowania do użycia w wielu aplikacjach. Aby uzyskać więcej informacji, zobacz [porady: Implementowanie logowania użytkownika przy użyciu usług aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md).  
  
     Jeśli określisz dostawcy poświadczeń, należy określić go jako nazwę typu kwalifikowanego zestawu. Aby uzyskać więcej informacji, zobacz <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> i [nazw zestawów](../../../docs/framework/app-domains/assembly-names.md). W najprostszej postaci nazwę typu kwalifikowanego zestawu wyglądają podobnie do poniższego przykładu:  
  
    ```  
    MyNamespace.MyLoginClass, MyAssembly  
    ```  
  
7.  W **ról usługi lokalizacji** i **ustawienia sieci Web usługi lokalizacji** pól tekstowych, określ lokalizację usługi, dla każdej usługi, nie zawiera nazwy pliku. Projektant automatycznie dołączy nazwy standardowego pliku (Role_JSON_AppService.axd i Profile_JSON_AppService.axd) po zapisuje wartość do pliku konfiguracji.  
  
8.  Opcjonalnie kliknij **zaawansowane** do modyfikowania ustawień zaawansowanych, takich jak lokalne zachowania buforowania. Aby uzyskać więcej informacji zobacz następną procedurę.  
  
## <a name="advanced-configuration"></a>Konfiguracja zaawansowana  
 W poniższych procedurach opisano sposób konfigurowania usług aplikacji klienckich dla mniej typowych scenariuszy. Na przykład można użyć tych opcji konfiguracji dla aplikacji wdrożonych w miejscach publicznych, lub użyć szyfrowanej bazy danych programu SQL Server Compact jako pamięci podręcznej danych lokalnych.  
  
#### <a name="to-configure-advanced-settings-for-client-application-services"></a>Aby skonfigurować zaawansowane ustawienia dla usług aplikacji klienta  
  
1.  Na **usług** strony **projektanta projektu**, kliknij przycisk **zaawansowane**.  
  
     **Zaawansowane ustawienia dla usług** pojawi się okno dialogowe, jak pokazano na poniższej ilustracji. Aby uzyskać więcej informacji na temat tego okna dialogowego, zobacz [Zaawansowane ustawienia dla usług, okno dialogowe](/visualstudio/ide/reference/advanced-settings-for-services-dialog-box).  
  
     ![Zaawansowane ustawienia dla usług, okno dialogowe](../../../docs/framework/common-client-technologies/media/casdialog.png "casdialog")  
  
2.  Zaznacz lub wyczyść **Zapisz wartość skrótu hasła lokalnie, aby włączyć logowanie w trybie offline**. Po wybraniu tej opcji, zaszyfrowane hasło użytkownika będą buforowane lokalnie. Jest to przydatne w przypadku zaimplementowania trybu offline dla aplikacji. Ta opcja jest zaznaczona, można sprawdzić poprawność użytkowników nawet wtedy, gdy <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> została ustawiona właściwość `true`.  
  
3.  Zaznacz lub wyczyść **wymagać od użytkowników zalogować się ponownie przy każdym wygasa plik cookie serwera**. Plik cookie uwierzytelniania jest skonfigurowany na zdalnej usługi i wskazuje, ile danych logowania użytkownika pozostaną aktywne. Aby uzyskać więcej informacji o sposobie konfigurowania pliku cookie, zobacz `timeout` atrybutu w [formularzy elementem uwierzytelniania (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/8163b8b5-ea6c-46c8-b5a9-c4c3de31c0b3).  
  
     Wybierz tę opcję, próby uzyskania dostępu zdalnego ról lub zgłosi usług ustawień sieci Web po wygaśnięciu pliku cookie uwierzytelniania <xref:System.Net.WebException>. Można obsługiwać ten wyjątek i wyświetlić okno dialogowe logowania w celu ponownego zweryfikowania użytkowników. Na przykład to zachowanie zobacz [Instruktaż: przy użyciu usług aplikacji klienta](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md). Ta opcja jest przydatne w przypadku aplikacji wdrożonych w miejscach publicznych upewnić się, czy użytkownicy, którzy aplikacja działa po użyciu nie pozostanie uwierzytelniony przez czas nieokreślony.  
  
     Jeśli usuniesz zaznaczenie tej opcji i próby dostępu zdalnego, po upływie pliku cookie uwierzytelniania, użytkownicy będą się ponownie sprawdzić poprawności nazwy automatycznie.  
  
4.  Określ wartość dla **limit czasu pamięci podręcznej usługi roli**. Ustaw dany interwał czasu małej wartości, gdy role są aktualizowane często lub większej wartości role są rzadko aktualizowane. W przypadku zastosowania trybu offline, należy ustawić interwał czasu na dużą wartość, aby zapobiec informacje o roli przed wygaśnięciem, gdy aplikacja jest w trybie offline.  
  
     Dostawcy ról uzyskuje dostęp do wartości pamięci podręcznej roli lub usługi ról podczas wywoływania <xref:System.Web.Security.RolePrincipal.IsInRole%2A> metody. Aby programowo zresetować pamięć podręczną i wymusić tę metodę w celu uzyskania dostępu do usługi zdalnej, należy wywołać <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> metody.  
  
5.  Zaznacz lub wyczyść **Użyj niestandardowego ciągu połączenia**. Aby uzyskać więcej informacji zobacz następną procedurę.  
  
#### <a name="to-configure-client-application-services-to-use-a-database-for-the-local-cache"></a>Aby skonfigurować usługi aplikacji klienta na potrzeby bazy danych z lokalnej pamięci podręcznej  
  
1.  Na **usług** strony **projektanta projektu**, kliknij przycisk **zaawansowane**.  
  
     **Zaawansowane ustawienia dla usług** pojawi się okno dialogowe.  
  
2.  Wybierz **Użyj niestandardowego ciągu połączenia**.  
  
     Wartość domyślna `Data Source = |SQL/CE|` pojawia się w polu tekstowym.  
  
3.  Aby wygenerować bazę danych programu SQL Server Compact, Zachowaj wartość domyślną ciągu połączenia. Generuj plik bazy danych Visual Studio i umieścić go w katalogu, wskazywanym przez <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> właściwości.  
  
4.  Generowanie i używanie zaszyfrowanych [!INCLUDE[ssEW](../../../includes/ssew-md.md)] bazy danych, Dodaj `password` i `encrypt database` wartości parametry połączenia, jak pokazano w poniższym przykładzie.  
  
    > [!NOTE]
    >  Koniecznie Określ silne hasło. Nie można zmienić hasła, po wygenerowaniu bazy danych.  
  
    ```  
    Data Source = |SQL/CE|;password=<password>;encrypt database=true  
    ```  
  
5.  Aby użyć swoją własną bazę danych programu SQL Server, należy określić parametry połączenia. Informacje o formaty ciągu prawidłowe połączenie znajduje się w dokumentacji programu SQL Server. Ta baza danych nie jest generowany automatycznie. Parametry połączenia muszą odwoływać się do istniejącej bazy danych, które można tworzyć przy użyciu następujących instrukcji SQL.  
  
    ```  
    CREATE TABLE ApplicationProperties (PropertyName nvarchar(256),  
        PropertyValue nvarchar(256))  
    CREATE TABLE UserProperties (PropertyName nvarchar(256),  
        PropertyValue nvarchar(256))  
    CREATE TABLE Roles (UserName nvarchar(256),   
        RoleName nvarchar(256))  
    CREATE TABLE Settings (PropertyName nvarchar(256),   
        PropertyStoredAs nvarchar(1), PropertyValue nvarchar(2048))  
    ```  
  
## <a name="using-custom-providers"></a>Za pomocą dostawcy niestandardowi  
 Domyślnie funkcja usług aplikacji klienta korzysta z dostawców w <xref:System.Web.ClientServices.Providers?displayProperty=nameWithType> przestrzeni nazw. Po skonfigurowaniu aplikacji przy użyciu **usług** strony **projektanta projektu**, odwołania do tych dostawców są dodawane do pliku App.config. Tych domyślnych dostawców uzyskiwać dostęp do odpowiedniego dostawcy na serwerze. Usługi sieci Web są często skonfigurowane do dostępu do danych użytkownika za pośrednictwem dostawców usług takich jak <xref:System.Web.Security.SqlMembershipProvider> i <xref:System.Web.Security.SqlRoleProvider>.  
  
 Jeśli chcesz użyć niestandardowego usługodawcy, będzie zazwyczaj zmienia dostawcy po stronie serwera, tak że wpływają na wszystkie aplikacje klienckie, które dostęp do serwera. Jednak masz możliwość korzystania z dostawców innych niż domyślne po stronie klienta. W pliku App.config projektu, można określić niestandardowych dostawców uwierzytelniania lub ról, jak pokazano w poniższej procedurze. Aby uzyskać informacje o tym, jak utworzyć niestandardowe uwierzytelnianie i dostawców ról, zobacz [implementowanie dostawcy członkostwa](https://msdn.microsoft.com/library/d8658b8e-c962-4f64-95e1-4acce35e4582) i [implementowanie dostawcy roli](https://msdn.microsoft.com/library/851671ce-bf9b-43f2-aba4-bc9d28b11c7d). Umożliwia także dostawcy ustawień niestandardowych, modyfikując projektu `Settings` klasy (dostępne jako `Properties.Settings.Default` w języku C# i `My.Settings` w języku Visual Basic). Aby uzyskać więcej informacji, zobacz [Architektura ustawień aplikacji](../../../docs/framework/winforms/advanced/application-settings-architecture.md).  
  
#### <a name="to-configure-client-application-services-to-use-non-default-providers"></a>Aby skonfigurować usługi aplikacji klienta do używania dostawców innych niż domyślne  
  
1.  Aby użyć uwierzytelniania inne niż domyślne lub dostawcy usług ról, najpierw zakończyć wszystkie ustawienia konfiguracji za pomocą **usług** strony.  
  
2.  Zamknij **Projektant projektu**. Jest to konieczne, ponieważ **usług** strona zostanie zaktualizowana automatycznie pliku App.config, nawet wtedy, gdy nie należy modyfikować wszystkie ustawienia. Jeśli ręcznie zmodyfikować pliku App.config, zgodnie z opisem w tej procedurze, a następnie wróć do **usług** stronie modyfikacje zostaną zresetowane.  
  
3.  W **Eksploratora rozwiązań**, kliknij dwukrotnie ikonę pliku App.config.  
  
     Plik konfiguracji aplikacji zostanie otwarty w edytorze tekstów.  
  
4.  Znajdź `<providers>` elemencie `<membership>` lub `<roleManager>` elementu. Te elementy są elementami podrzędnymi `<system.web>` elementu. `<membership>` Element jest używany do określenia dostawcy uwierzytelniania i `<roleManager>` element jest używany do określania dostawców ról.  
  
5.  Dodaj `<add>` element jako element podrzędny elementu `<providers>` elementu. Należy określić `name` i `type` atrybuty, jak pokazano w poniższym przykładzie. `type` Wartość atrybutu musi być nazwą typu kwalifikowanego zestawu. Aby uzyskać więcej informacji, zobacz <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> i [nazw zestawów](../../../docs/framework/app-domains/assembly-names.md).  
  
    ```xml  
    <add name="MyCustomRoleProvider" type="MyNamespace.MyRoleProvider, MyAssembly" />  
    ```  
  
6.  Modyfikowanie `defaultProvider` atrybutu `<membership>` lub `<roleManager>` elementu, aby określić wartość name z `<add>` element, który zostało dodane w poprzednim kroku.  
  
    ```xml  
    <roleManager enabled="true" defaultProvider="MyCustomRoleProvider">  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi aplikacji klienckich](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [Omówienie usług aplikacji klienckich](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [Strona usług, Projektant projektu](/visualstudio/ide/reference/services-page-project-designer)  
 [Zaawansowane ustawienia dla usług, okno dialogowe](/visualstudio/ide/reference/advanced-settings-for-services-dialog-box)  
 [Instrukcje: implementowanie logowania użytkownika przy użyciu usług aplikacji klienckich](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 [Przewodnik: używanie usług aplikacji klienckich](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [Implementowanie dostawcy członkostwa](https://msdn.microsoft.com/library/d8658b8e-c962-4f64-95e1-4acce35e4582)  
 [Implementowanie dostawcy roli](https://msdn.microsoft.com/library/851671ce-bf9b-43f2-aba4-bc9d28b11c7d)  
 [Architektura ustawień aplikacji](../../../docs/framework/winforms/advanced/application-settings-architecture.md)  
 [Tworzenie i Konfigurowanie bazy danych usługi aplikacji dla programu SQL Server](https://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)
