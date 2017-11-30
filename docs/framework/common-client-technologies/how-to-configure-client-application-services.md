---
title: "Porady: konfigurowanie usług aplikacji klienta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: client application services, configuring
ms.assetid: 34a8688a-a32c-40d3-94be-c8e610c6a4e8
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1f4f518b1676e998cf8a3fd93f893398342cba6f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-client-application-services"></a>Porady: konfigurowanie usług aplikacji klienta
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] **projektanta projektu** Włączanie i konfigurowanie usługi aplikacji klienta. Usługi aplikacji klienta można użyć do weryfikowania użytkowników i pobierania ról użytkownika i ustawienia z istniejącego [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] usługi aplikacji. Po przeprowadzeniu konfiguracji, są dostępne włączone usługi w kodzie aplikacji zgodnie z opisem w [przegląd usług aplikacji klienta](../../../docs/framework/common-client-technologies/client-application-services-overview.md). Aby uzyskać więcej informacji na temat [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] usług aplikacji, zobacz [przegląd usług aplikacji ASP.NET](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).  
  
 Można włączyć i skonfigurować usługi aplikacji klienta na **usług** strony **projektanta projektu**. **Usług** strona aktualizuje wartości w pliku App.config projektu. Aby uzyskać dostęp do **projektanta projektu**, użyj **właściwości** na **projektu** menu. Aby uzyskać więcej informacji na temat **usług** strony, zobacz [Strona usług, Projektant projektu](https://msdn.microsoft.com/library/bb398109).  
  
 Poniższa procedura zawiera opis sposobu przeprowadzenia konfiguracji podstawowej dla usług aplikacji klienta. Zaawansowane opcje zostały opisane w kolejnych sekcjach konfiguracji.  
  
### <a name="to-configure-client-application-services"></a>Aby skonfigurować usługi aplikacji klienta  
  
1.  W **Eksploratora rozwiązań**, wybierz węzeł projektu, a następnie na **projektu** menu, kliknij przycisk **właściwości**.  
  
     **Projektanta projektu** pojawi się.  
  
2.  Kliknij przycisk **usług** kartę. **Usług** zostanie wyświetlona strona, jak pokazano na poniższej ilustracji.  
  
     ![Na karcie usług w Projektancie projektu](../../../docs/framework/common-client-technologies/media/casdesigner.png "casdesigner")  
  
3.  Na **usług** wybierz pozycję **włączyć usługi aplikacji klienckiej**.  
  
    > [!NOTE]
    >  Usługi aplikacji klienta wymaga pełnej wersji programu .NET Framework i nie są obsługiwane w programie .NET Framework Client Profile. Jeśli **włączyć usługi aplikacji klienckiej** pole wyboru jest wyłączone, upewnij się, że **platformy docelowej** jest ustawiony do programu .NET Framework 3.5 lub nowszej. Aby wyświetlić **platformy docelowej** ustawienie w języku C#, Otwórz w Projektancie projektu, a następnie kliknij przycisk **aplikacji** strony. Aby wyświetlić **platformy docelowej** ustawienie w języku Visual Basic, Otwórz w Projektancie projektu, kliknij przycisk **skompilować** , a następnie kliknij przycisk **zaawansowane opcje kompilacji**.  
  
4.  Wybierz **Użyj uwierzytelniania formularzy** planowania udostępnić własny kontrolek logowania lub okno dialogowe, lub wybierz **Użyj uwierzytelniania systemu Windows** do korzystania z tożsamości dostarczane przez system operacyjny. Aby uzyskać więcej informacji, zobacz [przegląd usług aplikacji klienta](../../../docs/framework/common-client-technologies/client-application-services-overview.md).  
  
    > [!NOTE]
    >  W przypadku wybrania **Użyj uwierzytelniania systemu Windows**, usługi aplikacji klienta automatycznie zostanie skonfigurowany do korzystania z bazy danych programu SQL Server Compact. Jest to wskazane **Zaawansowane ustawienia dla usług** okno dialogowe zgodnie z opisem w następnej sekcji. Jeśli następnie wybierz **uwierzytelnianie formularzy użyj**, **Użyj niestandardowych parametrów połączenia** ustawienia nie zostaną automatycznie wyczyszczone. Może to spowodować błędy, jeśli [!INCLUDE[ssEW](../../../includes/ssew-md.md)] bazy danych został już wygenerowany do użycia z uwierzytelnianiem systemu Windows. Aby usunąć te błędy, wyczyść **Użyj niestandardowych parametrów połączenia** w **Zaawansowane ustawienia dla usług** okno dialogowe.  
  
5.  W przypadku wybrania **uwierzytelnianie formularzy użyj**w **lokalizacji usługi uwierzytelniania** Określ adres URL hosta usługi nie zawiera nazwy pliku. Projektant automatycznie dołączy nazwę standardowego pliku (Authentication_JSON_AppService.axd), gdy wartość jest zapisywany do pliku konfiguracji.  
  
6.  Opcjonalnie w przypadku wybrania **uwierzytelnianie formularzy użyj**, można określić wartość w **dostawcy poświadczeń** pole. Dostawca poświadczeń musi implementować <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> interfejsu. Za pomocą dostawcy poświadczeń, można oddzielić interfejsu użytkownika logowania w kodzie aplikacji. Dzięki temu można utworzyć okno dialogowe pojedynczego logowania do użycia w wielu aplikacjach. Aby uzyskać więcej informacji, zobacz [porady: Implementowanie logowania użytkownika z usługi aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md).  
  
     Jeśli określisz dostawcy poświadczeń, muszą określić go jako nazwy typu kwalifikowanego zestawu. Aby uzyskać więcej informacji, zobacz <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> i [nazwy zestawu](../../../docs/framework/app-domains/assembly-names.md). W najprostszej postaci nazwa kwalifikowana zestawu typu wygląda podobnie do poniższego przykładu:  
  
    ```  
    MyNamespace.MyLoginClass, MyAssembly  
    ```  
  
7.  W **ról usługi lokalizacji** i **Lokalizacja usługi ustawień sieci Web** pola tekstowe, określ lokalizację usługi dla każdej usługi, nie zawiera nazwy pliku. Projektant automatycznie dołączy nazwy pliku (Role_JSON_AppService.axd i Profile_JSON_AppService.axd) Jeśli wartość jest zapisywany do pliku konfiguracji.  
  
8.  Opcjonalnie kliknij **zaawansowane** do modyfikowania ustawień zaawansowanych, takich jak zachowanie buforowania w lokalnym. Aby uzyskać więcej informacji zobacz następną procedurę.  
  
## <a name="advanced-configuration"></a>Konfiguracja zaawansowana  
 Poniższe procedury opisują Konfigurowanie usługi aplikacji klienta w mniej typowych scenariuszach. Na przykład można użyć tych opcji konfiguracji dla aplikacji wdrażanych w miejscach publicznych, lub do użycia jako pamięci podręcznej danych lokalnych zaszyfrowanych bazy danych programu SQL Server Compact.  
  
#### <a name="to-configure-advanced-settings-for-client-application-services"></a>Aby skonfigurować zaawansowane ustawienia dla usług aplikacji klienta  
  
1.  Na **usług** strony **projektanta projektu**, kliknij przycisk **zaawansowane**.  
  
     **Zaawansowane ustawienia dla usług** zostanie wyświetlone okno dialogowe, jak pokazano na poniższej ilustracji. Aby uzyskać więcej informacji dotyczących tego okna dialogowego, zobacz [Zaawansowane ustawienia dla usług — okno dialogowe](/visualstudio/ide/reference/advanced-settings-for-services-dialog-box).  
  
     ![Zaawansowane ustawienia dla usług — okno dialogowe](../../../docs/framework/common-client-technologies/media/casdialog.png "casdialog")  
  
2.  Wybierz lub wyczyść **zapisać skrót hasła lokalnie, aby włączyć logowanie offline**. Po wybraniu tej opcji zaszyfrowane hasło użytkownika będą buforowane lokalnie. Jest to przydatne w przypadku zastosowania w trybie offline dla aplikacji. W przypadku wybrania tej opcji można sprawdzić poprawność użytkowników nawet wtedy, gdy <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> ustawioną właściwość `true`.  
  
3.  Wybierz lub wyczyść **wymagać od użytkowników zalogować się ponownie przy każdym wygasa plik cookie z serwera**. Plik cookie uwierzytelniania jest skonfigurowane w zdalnej usługi i wskazuje, jak długo będzie aktywna logowania użytkownika. Aby uzyskać więcej informacji o sposobie konfigurowania pliku cookie, zobacz `timeout` atrybutu w [formularzy Element uwierzytelniania (schemat ustawień programu ASP.NET)](http://msdn.microsoft.com/en-us/8163b8b5-ea6c-46c8-b5a9-c4c3de31c0b3).  
  
     Wybierz tę opcję, próby uzyskania dostępu zdalnego ról lub zgłosi usługi ustawień sieci Web po wygaśnięciu pliku cookie uwierzytelniania <xref:System.Net.WebException>. Można obsłużyć tego wyjątku i wyświetlić okno dialogowe logowania, ponownie sprawdź poprawność użytkowników. Na przykład tego zachowania, zobacz [wskazówki: Korzystanie z usługi aplikacji klienta](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md). Ta opcja jest przydatna w przypadku aplikacji wdrożonych w miejscach publicznych upewnij się, że zawsze uwierzytelniani użytkownicy uzyskują pozostaw aplikacji uruchomiony po nie pozostanie Użyj.  
  
     Jeśli wyczyścisz tej opcji i próba uzyskania dostępu zdalnego usługi, po wygaśnięciu pliku cookie uwierzytelniania użytkowników będzie można ponownie sprawdzić poprawności automatycznie.  
  
4.  Określ wartość **limit czasu pamięci podręcznej usługi roli**. Mała wartość należy ustawić dany interwał czasu, gdy role są aktualizowane często lub większej wartości role są aktualizacji rzadko. W przypadku zastosowania w trybie offline, należy ustawić przedział czasu na dużą wartość, aby zapobiec informacje o rolach wygaśnięcia, podczas gdy aplikacja jest w trybie offline.  
  
     Dostawca roli uzyskuje dostęp do wartości pamięci podręcznej roli lub usługi ról podczas wywoływania <xref:System.Web.Security.RolePrincipal.IsInRole%2A> metody. Aby programowo zresetować pamięć podręczną i wymusić tę metodę w celu uzyskania dostępu do zdalnej usługi, należy wywołać <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> metody.  
  
5.  Wybierz lub wyczyść **Użyj niestandardowych parametrów połączenia**. Aby uzyskać więcej informacji zobacz następną procedurę.  
  
#### <a name="to-configure-client-application-services-to-use-a-database-for-the-local-cache"></a>Aby skonfigurować usługi aplikacji klienta do korzystania z bazy danych dla lokalnej pamięci podręcznej  
  
1.  Na **usług** strony **projektanta projektu**, kliknij przycisk **zaawansowane**.  
  
     **Zaawansowane ustawienia dla usług** zostanie wyświetlone okno dialogowe.  
  
2.  Wybierz **Użyj niestandardowych parametrów połączenia**.  
  
     Wartość domyślna `Data Source = |SQL/CE|` do pola tekstowego.  
  
3.  Aby wygenerować i korzystania z bazy danych programu SQL Server Compact, zachowaj domyślną wartość ciągu połączenia. [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]zostanie wygenerowany plik bazy danych i umieść ją w katalogu wskazywanego przez <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> właściwości.  
  
4.  Generowanie i używanie zaszyfrowanych [!INCLUDE[ssEW](../../../includes/ssew-md.md)] bazy danych, należy dodać `password` i `encrypt database` wartości w parametrach połączenia, jak pokazano w poniższym przykładzie.  
  
    > [!NOTE]
    >  Należy określić silne hasło. Po wygenerowaniu bazy danych nie można zmienić hasła.  
  
    ```  
    Data Source = |SQL/CE|;password=<password>;encrypt database=true  
    ```  
  
5.  Aby skorzystać z własnego [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bazy danych, określ ciąg połączenia. Informacje o formaty ciągu prawidłowe połączenie, zobacz [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dokumentacji. Ta baza danych nie jest generowany automatycznie. Parametry połączenia muszą odwoływać się do istniejącej bazy danych, które można tworzyć przy użyciu następujących instrukcji SQL.  
  
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
  
## <a name="using-custom-providers"></a>Przy użyciu niestandardowych dostawców  
 Domyślnie funkcja usług aplikacji klienta korzysta z dostawców w <xref:System.Web.ClientServices.Providers?displayProperty=nameWithType> przestrzeni nazw. Po skonfigurowaniu aplikacji przy użyciu **usług** strony **projektanta projektu**, odwołania do tych dostawców są dodawane do pliku App.config. Ci dostawcy domyślnego dostępu do odpowiedniego dostawcy na serwerze. Aby uzyskać dostęp do danych użytkownika za pośrednictwem dostawców takich jak często skonfigurowano usługi sieci Web <xref:System.Web.Security.SqlMembershipProvider> i <xref:System.Web.Security.SqlRoleProvider>.  
  
 Jeśli chcesz użyć niestandardowego usługodawcy, zwykle ulegnie zmianie dostawcy po stronie serwera, aby wpływają na wszystkie aplikacje klienckie, które uzyskują dostęp do serwera. Jednak masz możliwość przy użyciu dostawców innych niż domyślne po stronie klienta. Można określić niestandardowych dostawców uwierzytelniania lub ról w pliku App.config projektu, jak pokazano w poniższej procedurze. Aby uzyskać informacje o sposobie tworzenia niestandardowych uwierzytelniania i dostawców ról, zobacz [implementowanie dostawcy członkostwa](http://msdn.microsoft.com/library/d8658b8e-c962-4f64-95e1-4acce35e4582) i [implementowanie dostawcy roli](http://msdn.microsoft.com/library/851671ce-bf9b-43f2-aba4-bc9d28b11c7d). Umożliwia także dostawcy ustawienia niestandardowe, modyfikując projektu `Settings` klasy (dostępne jako `Properties.Settings.Default` w języku C# i `My.Settings` w [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]). Aby uzyskać więcej informacji, zobacz [Architektura ustawień aplikacji](../../../docs/framework/winforms/advanced/application-settings-architecture.md).  
  
#### <a name="to-configure-client-application-services-to-use-non-default-providers"></a>Aby skonfigurować usługi aplikacji klienta do używania dostawców innych niż domyślne  
  
1.  Aby używać uwierzytelniania innych niż domyślne lub dostawcy usług ról, najpierw wykonać wszystkie ustawienia konfiguracji przy użyciu **usług** strony.  
  
2.  Zamknij **Projektant projektu**. Jest to konieczne, ponieważ **usług** strona zostanie zaktualizowana automatycznie pliku App.config, nawet jeśli nie należy modyfikować ustawienia. Jeśli ręcznie zmodyfikować plik App.config, zgodnie z opisem w tej procedurze, a następnie wróć do **usług** strony, te modyfikacje zostaną zresetowane.  
  
3.  W **Eksploratora rozwiązań**, kliknij dwukrotnie plik App.config.  
  
     Plik konfiguracji aplikacji zostanie otwarty w edytorze tekstów.  
  
4.  Znajdź `<providers>` w elemencie `<membership>` lub `<roleManager>` elementu. Te elementy są elementami podrzędnymi `<system.web>` elementu. `<membership>` Element służy do określania dostawców uwierzytelniania i `<roleManager>` element służy do określania dostawców ról.  
  
5.  Dodaj `<add>` element jako element podrzędny `<providers>` elementu. Należy określić `name` i `type` atrybutów, jak pokazano w poniższym przykładzie. `type` Wartość atrybutu musi być nazwą typu kwalifikowanego zestawu. Aby uzyskać więcej informacji, zobacz <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> i [nazwy zestawu](../../../docs/framework/app-domains/assembly-names.md).  
  
    ```xml  
    <add name="MyCustomRoleProvider" type="MyNamespace.MyRoleProvider, MyAssembly" />  
    ```  
  
6.  Modyfikowanie `defaultProvider` atrybutu `<membership>` lub `<roleManager>` element, aby określić wartość name z `<add>` element, który został dodany w poprzednim kroku.  
  
    ```xml  
    <roleManager enabled="true" defaultProvider="MyCustomRoleProvider">  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi aplikacji klienta](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [Przegląd usług aplikacji klienta](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [Strona usług, Projektant projektu](https://msdn.microsoft.com/library/bb398109)  
 [Zaawansowane ustawienia dla usług — okno dialogowe](/visualstudio/ide/reference/advanced-settings-for-services-dialog-box)  
 [Porady: Implementowanie logowania użytkownika z usługi aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 [Wskazówki: Korzystanie z usługi aplikacji klienta](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [Implementowanie dostawcy członkostwa](http://msdn.microsoft.com/library/d8658b8e-c962-4f64-95e1-4acce35e4582)  
 [Implementowanie dostawcy roli](http://msdn.microsoft.com/library/851671ce-bf9b-43f2-aba4-bc9d28b11c7d)  
 [Architektura ustawień aplikacji](../../../docs/framework/winforms/advanced/application-settings-architecture.md)  
 [Tworzenie i Konfigurowanie bazy danych usług aplikacji dla programu SQL Server](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)
