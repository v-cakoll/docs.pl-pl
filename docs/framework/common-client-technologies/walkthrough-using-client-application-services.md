---
title: 'Wskazówki: używanie usług aplikacji klienta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application services host [client application services]
- client application services, walkthroughs
ms.assetid: bb7c8950-4517-4dae-b705-b74a14059b26
ms.openlocfilehash: b800848fc3cefb1f82fb5822007bc670c1684363
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788931"
---
# <a name="walkthrough-using-client-application-services"></a>Wskazówki: używanie usług aplikacji klienta
W tym temacie opisano sposób tworzenia aplikacji Windows, która korzysta z usług aplikacji klienta do uwierzytelniania użytkowników oraz pobieranie ról użytkownika i ustawień.  
  
 W tym przewodniku należy wykonać następujące zadania:  
  
-   Tworzenie aplikacji Windows Forms i włączanie i konfigurowanie usług aplikacji klienta za pomocą projektanta projektu programu Visual Studio.  
  
-   Utwórz prostą aplikację usługi sieci Web ASP.NET do hostowania usługi aplikacji, a następnie przetestować konfigurację klienta.  
  
-   Dodawanie uwierzytelniania formularzy do aplikacji. Rozpocznie się za pomocą nazwy zakodowane użytkownika i hasło do testowania usługi. Następnie dodasz formularz logowania, określając ją jako dostawca poświadczeń w konfiguracji aplikacji.  
  
-   Dodawanie funkcji opartej na rolach, włączanie i wyświetlanie przycisk tylko dla użytkowników w roli "manager".  
  
-   Dostęp do ustawień sieci Web. Rozpocznie się przez załadowanie ustawień sieci Web dla użytkowników uwierzytelnionych (test) na **ustawienia** strony w Projektancie projektu. Następnie użyje Windows Forms Designer można powiązać pole tekstowe do ustawień sieci Web. Na koniec zapisze zmodyfikowane wartości do serwera.  
  
-   Implementowanie wylogowania. Spowoduje Dodaj opcję wylogowania do formularza i wywołać metodę wylogowania.  
  
-   Włącz tryb offline. Należy podać pole wyboru, aby użytkownicy mogą określić ich stan połączenia. Ta wartość zostanie następnie użyta do określenia, czy dostawców usług aplikacji klienta będą używać lokalnie buforowanych danych zamiast uzyskiwanie dostępu do swoich usług sieci Web. Ponownie zostaną na koniec uwierzytelnienia bieżącego użytkownika, gdy aplikacja powróci do trybu online.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Potrzebne są następujące składnik do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_orcas_long](../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-client-application"></a>Tworzenie aplikacji klienckiej  
 Pierwszą rzeczą, który będzie wykonywać jest, Utwórz projekt Windows Forms. W tym instruktażu wykorzystano Windows Forms, ponieważ więcej osób zapoznać się z nią, ale proces jest podobny do projektów Windows Presentation Foundation (WPF).  
  
#### <a name="to-create-a-client-application-and-enable-client-application-services"></a>Aby utworzyć aplikację kliencką i włączyć usługi aplikacji klienta  
  
1.  W programie Visual Studio, wybierz **pliku &#124; New &#124; projektu** opcji menu.  
  
2.  W **nowy projekt** dialogowym **typów projektów** okienku rozwiń **języka Visual Basic** lub **Visual C#** węzeł i wybierz pozycję **Windows** typ projektu.  
  
3.  Upewnij się, że **.NET Framework 3.5** jest wybrany, a następnie wybierz **aplikacja interfejsu Windows Forms** szablonu.  
  
4.  Zmień projekt **nazwa** do `ClientAppServicesDemo`, a następnie kliknij przycisk **OK**.  
  
     Nowy projekt Windows Forms jest otwarty w programie Visual Studio.  
  
5.  Na **projektu** menu, wybierz opcję **właściwości ClientAppServicesDemo**.  
  
     Zostanie wyświetlony w Projektancie projektu.  
  
6.  Na **usług** zaznacz **włączyć usługi aplikacji klienckiej**.  
  
7.  Upewnij się, że **użycie formularza uwierzytelniania** jest zaznaczone, a następnie ustaw **lokalizacji usługi uwierzytelniania**, **ról usługi lokalizacji**, i **ustawień sieci Web usługi lokalizacji** do `http://localhost:55555/AppServices`.  
  
8.  Dla języka Visual Basic na **aplikacji** kartę, należy ustawić **tryb uwierzytelniania** do **zdefiniowanych przez aplikację**.  
  
 Projektant określone ustawienia są przechowywane w pliku app.config aplikacji.  
  
 W tym momencie aplikacja jest skonfigurowana na dostęp do wszystkich trzech usług z tym samym hoście. W następnej sekcji utworzysz hosta jako prostą aplikację usługi sieci Web, dzięki któremu można przetestować konfigurację klienta.  
  
## <a name="creating-the-application-services-host"></a>Tworzenie aplikacji hosta usługi  
 W tej sekcji utworzysz prostą aplikację usługi sieci Web, który uzyskuje dostęp do danych użytkownika z lokalnego pliku bazy danych programu SQL Server Compact. Następnie zostanie wypełniony bazy danych przy użyciu [narzędzie Administratorskie witryny sieci Web platformy ASP.NET](https://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec). Tej prostej konfiguracji umożliwia szybkie testowanie aplikacji klienckiej. Alternatywnie, można skonfigurować hosta usługi sieci Web do dostępu do danych użytkownika z pełnej bazy danych SQL Server lub za pomocą niestandardowego <xref:System.Web.Security.MembershipProvider> i <xref:System.Web.Security.RoleProvider> klasy. Aby uzyskać więcej informacji, zobacz [tworzenie i Konfigurowanie bazy danych usługi aplikacji dla programu SQL Server](https://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2).  
  
 Poniższa procedura służy do tworzenia i Konfiguruj usługę sieci AppServices Web.  
  
#### <a name="to-create-and-configure-the-application-services-host"></a>Aby utworzyć i skonfigurować hosta usługi aplikacji  
  
1.  W **Eksploratora rozwiązań**, wybierz rozwiązanie ClientAppServicesDemo, a następnie na **pliku** menu, wybierz opcję **Dodaj &#124; nowy projekt**.  
  
2.  W **Dodaj nowy projekt** dialogowym **typów projektów** okienku rozwiń **języka Visual Basic** lub **Visual C#** węzeł i wybierz pozycję  **Web** typ projektu.  
  
3.  Upewnij się, że **.NET Framework 3.5** jest wybrany, a następnie wybierz **aplikacji usługi sieci Web platformy ASP.NET** szablonu.  
  
4.  Zmień projekt **nazwa** do `AppServices` a następnie kliknij przycisk **OK**.  
  
     Nowy projekt aplikacji usługi sieci Web platformy ASP.NET jest dodawany do rozwiązania, a plik Service1.asmx.vb lub Service1.asmx.cs pojawia się w edytorze.  
  
    > [!NOTE]
    >  Plik Service1.asmx.vb lub Service1.asmx.cs nie jest używany w tym przykładzie. Jeśli chcesz zasłaniać środowisko pracy, możesz go zamknąć i usunięcia go z **Eksploratora rozwiązań**.  
  
5.  W **Eksploratora rozwiązań**, wybierz projekt AppServices, a następnie na **projektu** menu, wybierz opcję **właściwości AppServices**.  
  
     Zostanie wyświetlony w Projektancie projektu.  
  
6.  Na **Web** kartę, upewnij się, że **Użyj serwera wdrożeniowego usługi Visual Studio** jest zaznaczone.  
  
7.  Wybierz **określonego portu**, określ wartość `55555`, a następnie ustaw **ścieżki wirtualnej** do `/AppServices`.  
  
8.  Zapisz wszystkie pliki.  
  
9. W **Eksploratora rozwiązań**, otwórz plik Web.config i Znajdź `<system.web>` tagu początkowego.  
  
10. Dodaj następujący kod przed `<system.web>` tagu.  
  
     `authenticationService`, `profileService`, I `roleService` elementów w tym znaczników Włączanie i konfigurowanie usługi aplikacji. Do celów testowych `requireSSL` atrybutu `authenticationService` element jest ustawiony na wartość "false". `readAccessProperties` i `writeAccessProperties` atrybuty `profileService` elementu wskazują, że `WebSettingsTestText` właściwość jest odczytu/zapisu.  
  
    > [!NOTE]
    >  W kodzie produkcyjnym należy zawsze dostęp do usługi uwierzytelniania za pośrednictwem protokołu secure sockets layer (SSL przy użyciu protokołu HTTPS). Aby uzyskać informacje o tym, jak skonfigurować protokół SSL, zobacz [Konfigurowanie protokołu Secure Sockets Layer (IIS 6.0 Operations Guide)](https://go.microsoft.com/fwlink/?LinkId=91844).  
  
    ```xml  
    <system.web.extensions>  
      <scripting>  
        <webServices>  
          <authenticationService enabled="true" requireSSL = "false"/>  
          <profileService enabled="true"  
            readAccessProperties="WebSettingsTestText"  
            writeAccessProperties="WebSettingsTestText" />  
          <roleService enabled="true"/>  
        </webServices>  
      </scripting>  
    </system.web.extensions>  
    ```  
  
11. Dodaj następujący kod po `<system.web>` tagu początkowego, tak, aby w ramach `<system.web>` elementu.  
  
     `profile` Element konfiguruje jednej sieci Web, ustawienie o nazwie `WebSettingsTestText`.  
  
    ```xml  
    <profile enabled="true" >  
      <properties>  
        <add name="WebSettingsTestText" type="string"   
          readOnly="false" defaultValue="DefaultText"   
          serializeAs="String" allowAnonymous="false" />  
      </properties>  
    </profile>  
    ```  
  
 W poniższej procedurze do ukończenia konfiguracji usługi i wypełnić pliku lokalnej bazy danych służy narzędzie administrowanie witryną sieci Web platformy ASP.NET. Spowoduje dodanie dwóch użytkowników o nazwie `employee` i `manager` należących do dwóch ról przy użyciu takich samych nazwach. Hasła użytkowników są `employee!` i `manager!` odpowiednio.  
  
#### <a name="to-configure-membership-and-roles"></a>Aby skonfigurować członkostwa i ról  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt AppServices, a następnie na **projektu** menu, wybierz opcję **Konfiguracja ASP.NET**.  
  
     **Narzędzie Administratorskie witryny sieci Web platformy ASP.NET** pojawia się.  
  
2.  Na **zabezpieczeń** kliknij pozycję **Użyj Kreatora konfiguracji zabezpieczeń, aby skonfigurować zabezpieczenia krok po kroku**.  
  
     **Kreator konfiguracji zabezpieczeń** pojawi się i wyświetli **powitalnej** kroku.  
  
3.  Kliknij przycisk **Dalej**.  
  
     **Wybierz metodę dostępu** krok jest wyświetlany.  
  
4.  Wybierz **z Internetu**. Umożliwia skonfigurowanie usługi w celu używania uwierzytelniania formularzy, zamiast uwierzytelniania Windows.  
  
5.  Kliknij przycisk **dalej** dwa razy.  
  
     **Zdefiniuj role** krok jest wyświetlany.  
  
6.  Wybierz **Włącz role dla tej witryny sieci Web**.  
  
7.  Kliknij przycisk **Dalej**. **Utwórz nową rolę** zostanie wyświetlony formularz.  
  
8.  W **nową nazwę roli** polu tekstowym `manager` a następnie kliknij przycisk **Dodaj rolę**.  
  
     **Istniejące role** zostanie wyświetlona tabela z określoną wartością.  
  
9. W **nową nazwę roli** pola tekstowego Zastąp `manager` z `employee` a następnie kliknij przycisk **Dodaj rolę**.  
  
     Nowa wartość jest wyświetlana w **istniejące role** tabeli.  
  
10. Kliknij przycisk **Dalej**.  
  
     **Dodaj nowych użytkowników** krok jest wyświetlany.  
  
11. W **Create User** formularza, określ następujące wartości.  
  
  	|||  
  	|-|-|  
  	|**Nazwa użytkownika**|`manager`|  
  	|**Hasło**|`manager!`|  
  	|**Potwierdź hasło**|`manager!`|  
  	|**Poczta e-mail**|`manager@contoso.com`|  
  	|**Pytanie zabezpieczające**|`manager`|  
  	|**Odpowiedź zabezpieczeń**|`manager`|  
  
12. Kliknij przycisk **Utwórz użytkownika**.  
  
     Zostanie wyświetlony komunikat o powodzeniu.  
  
    > [!NOTE]
    >  **E-mail**, **pytanie zabezpieczające**, i **zabezpieczającą** wartości są wymagane w formularzu, ale nie są używane w tym przykładzie.  
  
13. Kliknij przycisk **Kontynuuj**.  
  
     **Create User** formularzu pojawi się.  
  
14. W **Create User** formularza, określ następujące wartości.  
  
  	|||  
  	|-|-|  
  	|**Nazwa użytkownika**|`employee`|  
  	|**Hasło**|`employee!`|  
  	|**Potwierdź hasło**|`employee!`|  
  	|**Poczta e-mail**|`employee@contoso.com`|  
  	|**Pytanie zabezpieczające**|`Employee`|  
  	|**Odpowiedź zabezpieczeń**|`employee`|  
  
15. Kliknij przycisk **Utwórz użytkownika**.  
  
     Zostanie wyświetlony komunikat o powodzeniu.  
  
16. Kliknij przycisk **Zakończ**.  
  
     **Narzędzie Administratorskie witryny sieci Web** pojawi się ponownie.  
  
17. Kliknij przycisk **użytkownicy Menedżera**.  
  
     Zostanie wyświetlona lista użytkowników.  
  
18. Kliknij przycisk **edytować ról** dla **pracowników** użytkownika, a następnie wybierz **pracowników** roli.  
  
19. Kliknij przycisk **edytować ról** dla **Menedżera** użytkownika, a następnie wybierz **Menedżera** roli.  
  
20. Zamknij okno przeglądarki, który jest hostem **narzędzie Administratorskie witryny sieci Web**.  
  
21. Jeśli pojawia się komunikat z pytaniem, jeśli chcesz ponownie załadować zmodyfikowany plik Web.config, kliknij przycisk **tak**.  
  
 Na tym kończy się instalacji usługi sieci Web. W tym momencie naciśnięciu klawisza F5, aby uruchomić aplikację kliencką i **ASP.NET Development Server** rozpocznie się automatycznie wraz z aplikacji klienckiej. Serwer będzie kontynuowane po Zamknij aplikację, ale zostanie uruchomiony ponownie po ponownym uruchomieniu aplikacji. Dzięki temu można wykrywać zmiany wprowadzone do pliku Web.config.  
  
 Aby zatrzymać serwer ręcznie, kliknij prawym przyciskiem myszy ikonę programu ASP.NET Development Server, w obszarze powiadomień paska zadań, a następnie kliknij przycisk **zatrzymać**. Jest to przydatne od czasu do czasu upewnić się, czy występuje czystego ponownego uruchomienia.  
  
## <a name="adding-forms-authentication"></a>Dodanie uwierzytelniania formularzy  
 W poniższej procedurze Dodaj kod do formularza głównego, próbuje zweryfikować użytkownika, która nie zezwala na dostęp po użytkownik podaje nieprawidłowe poświadczenia. Używasz nazwy zakodowane użytkownika i hasło do testowania usługi.  
  
#### <a name="to-validate-the-user-in-your-application-code"></a>Do weryfikacji użytkownika w kodzie aplikacji  
  
1.  W **Eksploratora rozwiązań**, w projekcie ClientAppServicesDemo Dodaj odwołanie do zestawu System.Web.  
  
2.  Wybierz plik Form1, a następnie wybierz pozycję **widoku &#124; kodu** z głównego menu programu Visual Studio.  
  
3.  W edytorze kodu Dodaj następujące instrukcje na górze pliku Form1.  
  
     [!code-csharp[ClientApplicationServices#001](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#001)]
     [!code-vb[ClientApplicationServices#001](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#001)]  
  
4.  W **Eksploratora rozwiązań**, kliknij dwukrotnie Form1, aby wyświetlić projektanta.  
  
5.  W projektancie, kliknij dwukrotnie na powierzchnię formularza, aby wygenerować <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> programu obsługi zdarzeń o nazwie `Form1_Load`.  
  
     Ustaw kursor zostanie wyświetlony Edytor kodu `Form1_Load` metody.  
  
6.  Dodaj następujący kod do `Form1_Load` metody.  
  
     Ten kod nie zezwala na dostęp użytkowników nieuwierzytelnionych przez zakończeniem działania aplikacji. Alternatywnie można udostępnić nieuwierzytelnionym użytkownikom formularza, ale nie zezwoli na dostęp do określonych funkcji. Zazwyczaj użytkownik będzie nie trwale kodować nazwę użytkownika i hasła, takie jak to, ale jest przydatny do celów testowych. W następnej sekcji tego kodu zostaną zastąpione bardziej niezawodny kod, który wyświetla okno dialogowe logowania i obejmuje obsługę wyjątków.  
  
     Należy pamiętać, że `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> jest metoda [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)]. Ta metoda deleguje swoją pracę z dostawcą uwierzytelniania skonfigurowanego i zwraca `true` Jeśli uwierzytelnianie zakończy się pomyślnie. Aplikacja nie wymaga bezpośredniego odwołania do dostawcy uwierzytelniania klienta.  
  
     [!code-csharp[ClientApplicationServices#300](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#300)]
     [!code-vb[ClientApplicationServices#300](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#300)]  
  
 Teraz naciśnij klawisz F5, aby uruchomić aplikację, a ponieważ podasz prawidłowej nazwy użytkownika i hasła, zostanie wyświetlony formularz.  
  
> [!NOTE]
>  Jeśli nie można uruchomić aplikację, spróbuj zatrzymać ASP.NET Development Server. Po ponownym uruchomieniu serwera, upewnij się, że port jest ustawiona na 55555.  
  
 Aby zamiast tego wyświetlić komunikat o błędzie, zmień <xref:System.Web.Security.Membership.ValidateUser%2A> parametrów. Na przykład Zastąp ciąg drugi `"manager!"` parametru przy użyciu niepoprawnego hasła, takie jak `"MANAGER"`.  
  
## <a name="adding-a-login-form-as-a-credentials-provider"></a>Dodawanie formularza logowania jako dostawca poświadczeń  
 Możesz uzyskać poświadczenia użytkownika w kodzie aplikacji i przekazywać je do <xref:System.Web.Security.Membership.ValidateUser%2A> metody. Jednak często jest warto zachować kod Uzyskiwanie poświadczeń oddzielony od kodu aplikacji, w przypadku, gdy chcesz go później zmienić.  
  
 W poniższej procedurze należy skonfigurować aplikację do używania dostawcy poświadczeń, a następnie zmień swoje <xref:System.Web.Security.Membership.ValidateUser%2A> wywołanie metody do przekazania <xref:System.String.Empty> dla obu parametrów. Puste ciągi sygnał <xref:System.Web.Security.Membership.ValidateUser%2A> metodę do wywołania <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> metody dostawcy skonfigurowane poświadczenia.  
  
#### <a name="to-configure-your-application-to-use-a-credentials-provider"></a>Aby skonfigurować aplikację do używania dostawcy poświadczeń  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt ClientAppServicesDemo, a następnie na **projektu** menu, wybierz opcję **właściwości ClientAppServicesDemo**.  
  
     Zostanie wyświetlony w Projektancie projektu.  
  
2.  Na **usług** kartę, należy ustawić **opcjonalne: Dostawca poświadczeń** wartość. Ta wartość wskazuje nazwę typu kwalifikowanego zestawu.  
  
    ```  
    ClientAppServicesDemo.Login, ClientAppServicesDemo  
    ```  
  
3.  W pliku kodu formularza Form1, Zastąp kod w `Form1_Load` metoda następującym kodem.  
  
     Ten kod wyświetla komunikat powitalny, a następnie wywołuje `ValidateUsingCredentialsProvider` metody, który zostanie dodany w następnym kroku. Jeśli użytkownik nie jest uwierzytelniony, `ValidateUsingCredentialsProvider` metoda zwraca `false` i `Form1_Load` metoda zwraca. Każdy dodatkowy kod to zapobiega uruchamianiu przed umożliwia zamknięcie aplikacji. Komunikat powitalny jest przydatne było jasne po ponownym uruchomieniu aplikacji. Dodasz kod, aby ponownie uruchomić aplikację, podczas implementowania wylogowania w dalszej części tego przewodnika.  
  
     [!code-csharp[ClientApplicationServices#011](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#011)]
     [!code-vb[ClientApplicationServices#011](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#011)]  
  
4.  Dodaj następującą metodę po `Form1_Load` metody.  
  
     Ta metoda przekazuje puste ciągi do `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metody, która powoduje wyświetlenie okna dialogowego logowania. Jeśli usługa uwierzytelniania jest niedostępny, <xref:System.Web.Security.Membership.ValidateUser%2A> metoda zgłosi <xref:System.Net.WebException>. W tym przypadku `ValidateUsingCredentialsProvider` metoda wyświetla ostrzeżenie i pyta, jeśli użytkownik chce spróbować ponownie w trybie offline. Ta funkcja wymaga **Zapisz wartość skrótu hasła lokalnie, aby włączyć logowanie w trybie offline** funkcji opisanych w [porady: Konfigurowanie usług aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md). Ta funkcja jest włączona domyślnie w przypadku nowych projektów.  
  
     Jeśli użytkownik nie zostanie zweryfikowana, `ValidateUsingCredentialsProvider` metoda wyświetla komunikat o błędzie i zamyka aplikację. Ponadto ta metoda zwraca wynik próby uwierzytelnienia.  
  
     [!code-csharp[ClientApplicationServices#020](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#020)]
     [!code-vb[ClientApplicationServices#020](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#020)]  
  
### <a name="creating-a-login-form"></a>Tworzenie formularza logowania  
 Dostawca poświadczeń jest klasa, która implementuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> interfejsu. Ten interfejs zawiera jedną metodę o nazwie <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> zwracającego <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> obiektu. W poniższych procedurach opisano, jak utworzyć okno dialogowe logowania, która implementuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> do wyświetlania, sama i zwracać poświadczeń określonych przez użytkownika.  
  
 Oddzielne procedury są dostarczane dla języków Visual Basic i C#, ponieważ zapewnia Visual Basic **formularz logowania** szablonu. Spowoduje to zapisanie pewien czas i nakład pracy kodowania.  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-visual-basic"></a>Aby utworzyć okno dialogowe logowania jako dostawca poświadczeń w języku Visual Basic  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt ClientAppServicesDemo, a następnie na **projektu** menu, wybierz opcję **Dodaj nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **formularz logowania** szablonu, zmień element **nazwa** do `Login.vb`, a następnie kliknij przycisk **Dodaj** .  
  
     W programie Windows Forms Designer pojawi się okno dialogowe logowania.  
  
3.  W Projektancie zaznacz **OK** przycisk a następnie w **właściwości** oknie `DialogResult` do `OK`.  
  
4.  W projektancie, Dodaj `CheckBox` formantu do formularza w obszarze **hasło** pola tekstowego.  
  
5.  W **właściwości** okna, podaj **(nazwa)** wartość `rememberMeCheckBox` i **tekstu** wartość `&Remember me`.  
  
6.  Wybierz **widoku &#124; kodu** z głównego menu programu Visual Studio.  
  
7.  W edytorze kodu Dodaj następujący kod na początku pliku.  
  
     [!code-vb[ClientApplicationServices#101](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#101)]  
  
8.  Zmodyfikuj podpis klasy tak, że klasa implementuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> interfejsu.  
  
     [!code-vb[ClientApplicationServices#110](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#110)]  
  
9. Upewnij się, że kursor znajduje się po `IClientformsAuthenticationCredentialsProvider`, a następnie naciśnij klawisz ENTER, aby wygenerować `GetCredentials` metody.  
  
10. Znajdź <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> implementacji i zastąp go następującym kodem.  
  
     [!code-vb[ClientApplicationServices#120](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#120)]  
  
 Poniższa procedura C# zawiera cały kod, listę dla okna dialogowego logowania proste. Układ dla tego okna dialogowego jest nieco surowych, ale jest ważnym elementem <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> implementacji.  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-c"></a>Aby utworzyć okno dialogowe logowania jako dostawca poświadczeń w języku C#  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt ClientAppServicesDemo, a następnie na **projektu** menu, wybierz opcję **Dodaj klasę**.  
  
2.  W **Dodaj nowy element** okno dialogowe, zmiana **nazwa** do `Login.cs`, a następnie kliknij przycisk **Dodaj**.  
  
     Plik Login.cs zostanie otwarty w edytorze kodu.  
  
3.  Zamień domyślny kod następującym kodem.  
  
     [!code-csharp[ClientApplicationServices#200](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#200)]  
  
 Możesz teraz uruchomić aplikację i wyświetlone okno dialogowe logowania są wyświetlane. Do przetestowania tego kodu, wypróbuj inne poświadczenia prawidłowe i nieprawidłowe i upewnij się, dostęp formularza tylko za pomocą prawidłowych poświadczeń. Prawidłowe nazwy użytkowników są `employee` i `manager` przy użyciu haseł `employee!` i `manager!` odpowiednio.  
  
> [!NOTE]
>  Nie należy wybierać **Pamiętaj mnie** w tym punkcie lub nie będą mogli logować się jako inny użytkownik, dopóki nie implementuje wylogowania w dalszej części tego przewodnika.  
  
## <a name="adding-role-based-functionality"></a>Dodawanie funkcji opartej na rolach  
 W poniższej procedurze należy dodać przycisk do formularza i wyświetl ją tylko dla użytkowników w roli menedżera.  
  
#### <a name="to-change-the-user-interface-based-on-user-role"></a>Aby zmienić interfejs użytkownika na podstawie roli użytkownika  
  
1.  W **Eksploratora rozwiązań**, w projekcie ClientAppServicesDemo Wybieranie Form1, a następnie wybierz **widoku &#124; projektanta** z głównego menu programu Visual Studio.  
  
2.  W projektancie, Dodaj <xref:System.Windows.Forms.Button> formantu do formularza z **przybornika**.  
  
3.  W **właściwości** okna, ustaw następujące właściwości dla przycisku.  
  
  	|Właściwość|Wartość|  
  	|--------------|-----------|  
  	|**(Name)**|managerOnlyButton|  
  	|**Tekst**|& Menedżera zadań|  
  	|**Widoczne**|`False`|  
  
4.  W edytorze kodu formularza Form1, Dodaj następujący kod na końcu `Form1_Load` metody.  
  
     Ten kod wywołuje `DisplayButtonForManagerRole` metody, który zostanie dodany w następnym kroku.  
  
     [!code-csharp[ClientApplicationServices#012](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#012)]
     [!code-vb[ClientApplicationServices#012](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#012)]  
  
5.  Dodaj następującą metodę do końca klasy Form1.  
  
     Ta metoda wywołuje <xref:System.Security.Principal.IPrincipal.IsInRole%2A> metody <xref:System.Security.Principal.IPrincipal> zwrócone przez `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> właściwości. Dla aplikacji skonfigurowanych do korzystania z usług aplikacji klienta, właściwość ta zwraca <xref:System.Web.ClientServices.ClientRolePrincipal>. Ponieważ ta klasa implementuje <xref:System.Security.Principal.IPrincipal> interfejsu, nie trzeba jawnie do niego odwołują.  
  
     Jeśli użytkownik znajduje się w roli "manager" `DisplayButtonForManagerRole` metody ustawia <xref:System.Windows.Forms.Control.Visible%2A> właściwość `managerOnlyButton` do `true`. Ta metoda również wyświetla komunikat o błędzie, jeśli <xref:System.Net.WebException> jest zgłaszany, co oznacza, że usługa ról jest niedostępna.  
  
    > [!NOTE]
    >  <xref:System.Web.ClientServices.ClientRolePrincipal.IsInRole%2A> Metoda zawsze zwraca `false` po wygaśnięciu ważności logowania użytkownika. To nie wystąpi, jeśli Twoja aplikacja wywołuje <xref:System.Security.Principal.IPrincipal.IsInRole%2A> metoda jeden raz wkrótce po uwierzytelnieniu, jak pokazano w przykładowym kodzie w ramach tego przewodnika. Jeśli aplikacja musi pobrać ról użytkownika w innym czasie, można dodać kod, aby przechowywać użytkowników, których logowania wygasła. Jeśli wszystkich ważnych użytkowników przypisanych do ról, możesz określić, czy nazwa logowania wygasła, wywołując <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A?displayProperty=nameWithType> metody. Jeśli nie zostały zwrócone żadne role, nazwa logowania wygasła. Na przykład ta funkcja zobacz <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A> metody. Ta funkcja tylko jest to konieczne, jeśli wybrano **wymagać od użytkowników zalogować się ponownie przy każdym wygasa plik cookie serwera** w konfiguracji aplikacji. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie usług aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
     [!code-csharp[ClientApplicationServices#030](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#030)]
     [!code-vb[ClientApplicationServices#030](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#030)]  
  
 Jeśli uwierzytelnianie zakończy się pomyślnie, Ustawia dostawcę uwierzytelniania klienta <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> właściwości wystąpienia <xref:System.Web.ClientServices.ClientRolePrincipal> klasy. Ta klasa implementuje <xref:System.Security.Principal.IPrincipal.IsInRole%2A> metody, aby praca jest delegowane do dostawcy skonfigurowanych ról. Jak wcześniej, kod aplikacji nie wymaga bezpośrednie odwołanie do dostawcy usług.  
  
 Możesz teraz uruchomić aplikację i zaloguj się jako pracownika, aby zobaczyć, że przycisk nie są wyświetlane, a następnie zaloguj się jako Menedżer ds. Aby wyświetlić przycisk.  
  
## <a name="accessing-web-settings"></a>Uzyskiwanie dostępu do ustawień sieci Web  
 W poniższej procedurze Dodawanie pola tekstowego do formularza i powiązać ustawienie sieci Web. Jak poprzedni kod, który używa uwierzytelniania i ról ustawień kodu nie Dostawca ustawień bezpośredni dostęp. Zamiast tego używa silnie typizowanych `Settings` klasy (dostępne jako `Properties.Settings.Default` w języku C# i `My.Settings` w języku Visual Basic) wygenerowane w projekcie programu Visual Studio.  
  
#### <a name="to-use-web-settings-in-your-user-interface"></a>Aby użyć ustawień sieci Web w interfejsie użytkownika  
  
1.  Upewnij się, że **serwera wdrożeniowego sieci Web platformy ASP.NET** nadal działa, sprawdzając w obszarze powiadomień paska zadań. Jeśli serwer musi zostać zatrzymana, ponowne uruchomienie aplikacji (który automatycznie uruchamia serwer), a następnie zamknij okno dialogowe logowania.  
  
2.  W **Eksploratora rozwiązań**, wybierz projekt ClientAppServicesDemo, a następnie na **projektu** menu, wybierz opcję **właściwości ClientAppServicesDemo**.  
  
     Zostanie wyświetlony w Projektancie projektu.  
  
3.  Na **ustawienia** kliknij pozycję **ustawień sieci Web obciążenia**.  
  
     A **logowania** pojawi się okno dialogowe.  
  
4.  Wprowadź poświadczenia dla pracownika lub manager i kliknij przycisk **logowanie**. Ustawienia sieci Web będą używane jest skonfigurowany do dostępu przy uwierzytelnionych użytkowników tylko wtedy, dlatego kliknięcie **logowania Pomiń** nie załaduje żadnych ustawień.  
  
     `WebSettingsTestText` Ustawienie jest wyświetlane w projektancie, wartością domyślną `DefaultText`. Ponadto `Settings` klasę, która zawiera `WebSettingsTestText` ma generowaną właściwość dla projektu.  
  
5.  W **Eksploratora rozwiązań**, w projekcie ClientAppServicesDemo Wybieranie Form1, a następnie wybierz **widoku &#124; projektanta** z głównego menu programu Visual Studio.  
  
6.  W projektancie, Dodaj <xref:System.Windows.Forms.TextBox> formantu do formularza.  
  
7.  W **właściwości** okna, podaj **(nazwa)** wartość `webSettingsTestTextBox`.  
  
8.  W edytorze kodu Dodaj następujący kod na końcu `Form1_Load` metody.  
  
     Ten kod wywołuje `BindWebSettingsTestTextBox` metody, który zostanie dodany w następnym kroku.  
  
     [!code-csharp[ClientApplicationServices#013](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#013)]
     [!code-vb[ClientApplicationServices#013](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#013)]  
  
9. Dodaj następującą metodę do końca klasy Form1.  
  
     Ta metoda wiąże <xref:System.Windows.Forms.TextBox.Text%2A> właściwość `webSettingsTestTextBox` do `WebSettingsTestText` właściwość `Settings` klasy generowanej we wcześniejszej części tej procedury. Ta metoda również wyświetla komunikat o błędzie, jeśli <xref:System.Net.WebException> jest zgłaszany, co oznacza, że ustawienia usługi sieci Web jest niedostępna.  
  
     [!code-csharp[ClientApplicationServices#040](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#040)]
     [!code-vb[ClientApplicationServices#040](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#040)]  
  
    > [!NOTE]
    >  Aby włączyć automatyczne dwukierunkowej komunikacji między kontrolki i ustawiając sieci Web zazwyczaj użyje powiązanie danych. Jednakże można także przejść do ustawień sieci Web bezpośrednio, jak pokazano w poniższym przykładzie:  
  
     [!code-csharp[ClientApplicationServices#322](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#322)]
     [!code-vb[ClientApplicationServices#322](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#322)]  
  
10. W Projektancie wybierz formularz, a następnie w **właściwości** okna, kliknij przycisk **zdarzenia** przycisku.  
  
11. Wybierz <xref:System.Windows.Forms.Form.FormClosing> zdarzeń, a następnie naciśnij klawisz ENTER, aby wygenerować procedurę obsługi zdarzeń.  
  
12. Zastąp wygenerowana metoda następującym kodem.  
  
     <xref:System.Windows.Forms.Form.FormClosing> Wywołań obsługi zdarzeń `SaveSettings` metody, która jest używane także przez funkcje wylogowania, który zostanie dodany w następnej sekcji. `SaveSettings` Metoda najpierw sprawdza, czy użytkownik nie zalogował. Dzieje się tak, sprawdzając <xref:System.Security.Principal.IIdentity.AuthenticationType%2A> właściwość <xref:System.Security.Principal.IIdentity> zwrócony przez bieżący podmiot zabezpieczeń. Bieżący podmiot zabezpieczeń jest pobierane w drodze `static` <xref:System.Threading.Thread.CurrentPrincipal%2A> właściwości. Jeśli użytkownik został uwierzytelniony dla usług aplikacji klienta, typ uwierzytelniania będzie "ClientForms". `SaveSettings` Metoda po prostu nie można sprawdzić <xref:System.Security.Principal.IIdentity.IsAuthenticated%2A?displayProperty=nameWithType> właściwość, ponieważ użytkownik może mieć prawidłowej tożsamości Windows po wylogowania.  
  
     Jeśli użytkownik nie zalogował się `SaveSettings` wywołania metody <xref:System.Configuration.ApplicationSettingsBase.Save%2A> metody `Settings` klasy generowanej we wcześniejszej części tej procedury. Ta metoda może zgłosić <xref:System.Net.WebException> po wygaśnięciu ważności pliku cookie uwierzytelniania. Dzieje się tak tylko wtedy, gdy wybrano **wymagać od użytkowników zalogować się ponownie przy każdym wygasa plik cookie serwera** w konfiguracji aplikacji. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie usług aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md). `SaveSettings` Obsługiwała przez wywołanie datę ważności pliku cookie <xref:System.Web.Security.Membership.ValidateUser%2A> Aby wyświetlić okno dialogowe logowania. Jeśli użytkownik loguje się pomyślnie, `SaveSettings` metoda próbuje ponownie zapisać ustawienia, wywołując sam.  
  
     Podobnie jak w poprzednim kodzie `SaveSettings` metoda wyświetla komunikat o błędzie, jeśli usługa zdalna jest niedostępna. Jeśli dostawca ustawień nie może uzyskać dostęp do usługi zdalnej, ustawienia nadal są zapisane w lokalnej pamięci podręcznej i ponowne załadowanie po ponownym uruchomieniu aplikacji.  
  
     [!code-csharp[ClientApplicationServices#050](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#050)]
     [!code-vb[ClientApplicationServices#050](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#050)]  
  
13. Dodaj następującą metodę do końca klasy Form1.  
  
     Ten kod obsługuje <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved?displayProperty=nameWithType> zdarzeń i wyświetla ostrzeżenie, jeśli dowolne z ustawień nie można zapisać. <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> Zdarzenie nie występuje, jeśli Usługa ustawień jest niedostępna lub pliku cookie uwierzytelniania wygasł. Przykładem sytuacji <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> wystąpi zdarzenie, jest, jeśli użytkownik zarejestrował się już. Ta procedura obsługi zdarzeń można przetestować, dodając kod wylogowania do `SaveSettings` metody bezpośrednio przed <xref:System.Configuration.ApplicationSettingsBase.Save%2A> wywołania metody. Kod wylogowania, który można użyć jest opisane w następnej sekcji.  
  
     [!code-csharp[ClientApplicationServices#090](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#090)]
     [!code-vb[ClientApplicationServices#090](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#090)]  
  
14. Dla języka C#, Dodaj następujący kod na końcu `Form1_Load` metody. Ten kod kojarzy metoda dodanym w ostatnim kroku przy użyciu <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> zdarzeń.  
  
     [!code-csharp[ClientApplicationServices#015](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#015)]  
  
 Aby przetestować aplikację na tym etapie, uruchamiać go wiele razy jako pracownika i menedżera, a następnie wpisz różne wartości w polu tekstowym. Wartości będzie zachowywane między sesjami na podstawie poszczególnych użytkowników.  
  
## <a name="implementing-logout"></a>Implementowanie wylogowania  
 Gdy użytkownik wybierze **Pamiętaj mnie** pole wyboru podczas logowania w aplikacji będą automatycznie uwierzytelniania użytkownika na kolejnych uruchomień. Następnie będzie automatyczne uwierzytelnianie, gdy aplikacja jest w trybie offline lub do momentu wygaśnięcia ważności pliku cookie uwierzytelniania. Czasami jednak wielu użytkowników będą potrzebowali dostępu do aplikacji lub pojedynczego użytkownika może być od czasu do czasu Zaloguj się przy użyciu różnych poświadczeń. Aby włączyć ten scenariusz, należy zaimplementować funkcji wylogowania, zgodnie z opisem w poniższej procedurze.  
  
#### <a name="to-implement-logout-functionality"></a>Do implementacji funkcji wylogowania  
  
1.  W Projektancie formularza Form1 Dodaj <xref:System.Windows.Forms.Button> formantu do formularza z **przybornika**.  
  
2.  W **właściwości** okna, podaj **(nazwa)** wartość `logoutButton` i **tekstu** wartość **& Wyloguj**.  
  
3.  Kliknij dwukrotnie `logoutButton` do generowania <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń.  
  
     Ustaw kursor zostanie wyświetlony Edytor kodu `logoutButton_Click` metody.  
  
4.  Zastąp wygenerowany `logoutButton_Click` metoda następującym kodem.  
  
     Ta procedura obsługi zdarzeń najpierw wywołuje `SaveSettings` metoda dodanego w poprzedniej sekcji. Następnie wywołuje program obsługi zdarzeń <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A?displayProperty=nameWithType> metody. Jeśli usługa uwierzytelniania jest niedostępny, <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A> metoda zgłosi <xref:System.Net.WebException>. W tym przypadku `logoutButton_Click` metoda wyświetla ostrzeżenie i tymczasowo zmienia się w tryb offline, aby wylogować użytkownika. Tryb offline jest opisane w następnej sekcji.  
  
     Wylogowania usuwa plik cookie uwierzytelniania lokalnego, więc tej nazwy logowania będzie wymagane po ponownym uruchomieniu aplikacji. Po wylogowania program obsługi zdarzeń uruchamia ponownie aplikację. Po ponownym uruchomieniu aplikacji, wyświetla komunikat powitalny, a następnie okno dialogowe logowania. Wiadomość powitalna sprawia, że jasne, że aplikacja została uruchomiona ponownie. Zapobiega to potencjalnych pomyłek, jeśli użytkownik musi zalogować się do zapisać ustawienia i następnie musi wykonać ponowne logowanie, ponieważ aplikacja została uruchomiona ponownie.  
  
     [!code-csharp[ClientApplicationServices#070](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#070)]
     [!code-vb[ClientApplicationServices#070](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#070)]  
  
 Aby przetestować funkcje wylogowania, uruchom aplikację, a następnie wybierz **Pamiętaj mnie** w oknie dialogowym logowania. Następnie zamknij i ponownie uruchom aplikację, aby upewnić się, że masz już się zalogować. Na koniec należy ponownie uruchomić aplikację, klikając przycisk w przypadku wylogowania.  
  
## <a name="enabling-offline-mode"></a>Włączanie trybu Offline  
 W poniższej procedurze dodasz pole wyboru do formularza, aby umożliwić użytkownikowi, aby przejść do trybu offline. Aplikacja oznacza tryb offline, ustawiając `static` <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A?displayProperty=nameWithType> właściwość `true`. Stan offline jest przechowywany na lokalnym dysku twardym w lokalizacji wskazanej przez <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> właściwości. Oznacza to, że stan offline są przechowywane na poszczególnych użytkowników, poszczególnych aplikacji.  
  
 W trybie offline wszystkie żądania usługi aplikacji klienta pobierać dane z lokalnej pamięci podręcznej, zamiast próbować uzyskać dostęp do usług. W domyślnej konfiguracji dane lokalne zawierają zaszyfrowane hasło użytkownika. Dzięki temu użytkownikowi na logowanie, gdy aplikacja jest w trybie offline. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie usług aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
#### <a name="to-enable-offline-mode-in-your-application"></a>Aby włączyć tryb offline w aplikacji  
  
1.  W **Eksploratora rozwiązań**, w projekcie ClientAppServicesDemo Wybieranie Form1, a następnie wybierz **widoku &#124; projektanta** z głównego menu programu Visual Studio.  
  
2.  W projektancie, Dodaj <xref:System.Windows.Forms.CheckBox> formantu do formularza.  
  
3.  W **właściwości** okna, podaj **(nazwa)** wartość `workOfflineCheckBox` i **tekstu** wartość **& działają w trybie offline**.  
  
4.  W **właściwości** okna, kliknij przycisk **zdarzenia** przycisku.  
  
5.  Wybierz <xref:System.Windows.Forms.CheckBox.CheckedChanged> zdarzeń, a następnie naciśnij klawisz ENTER, aby wygenerować procedurę obsługi zdarzeń.  
  
6.  Zastąp wygenerowana metoda następującym kodem.  
  
     Ten kod aktualizuje <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> wartości, a następnie dyskretnie revalidates użytkownika, gdy zostaną zwrócone do trybu online. <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A?displayProperty=nameWithType> Metoda używa buforowanych poświadczeń, tak, aby użytkownik nie trzeba jawnie Zaloguj. Jeśli usługa uwierzytelniania jest niedostępny, pojawi się komunikat ostrzegawczy, a aplikacja pozostaje w trybie offline.  
  
    > [!NOTE]
    >  <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A> Metodą jest jedynie jako udogodnienie. Ponieważ nie ma wartości zwracanej, nie może wskazywać, czy ponowne sprawdzenie poprawności nie powiodło się. Ponowne sprawdzenie poprawności może zakończyć się niepowodzeniem, na przykład, jeśli poświadczenia użytkownika zostały zmienione na serwerze. W takich przypadkach możesz chcieć dołączyć kod, który jawnie sprawdza użytkowników po wywołanie usługi nie powiedzie się. Aby uzyskać więcej informacji zobacz sekcję ustawień dostępu do sieci Web we wcześniejszej części tego przewodnika.  
  
     Po ponownego sprawdzania poprawności, ten kod zapisze wszelkie zmiany w lokalnych ustawień sieci Web, wywołując `SaveSettings` metoda dodanej wcześniej. Następnie pobiera wszystkie nowe wartości na serwerze, wywołując <xref:System.Configuration.ApplicationSettingsBase.Reload%2A> metoda projektu `Settings` klasy (dostępne jako `Properties.Settings.Default` w języku C# i `My.Settings` w języku Visual Basic).  
  
     [!code-csharp[ClientApplicationServices#080](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#080)]
     [!code-vb[ClientApplicationServices#080](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#080)]  
  
7.  Dodaj następujący kod na końcu `Form1_Load` metody, aby upewnić się, że pole wyboru Wyświetla bieżący stan połączenia.  
  
     [!code-csharp[ClientApplicationServices#014](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#014)]
     [!code-vb[ClientApplicationServices#014](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#014)]  
  
 Na tym kończy się przykładowej aplikacji. Aby przetestować funkcji trybu offline, uruchom aplikację, zaloguj się jako pracownika lub menedżera, a następnie wybierz **Praca w trybie offline**. Zmodyfikuj wartość w polu tekstowym, a następnie zamknij aplikację. Uruchom ponownie aplikację. Przed zalogowaniem się należy, kliknij prawym przyciskiem myszy ikonę programu ASP.NET Development Server, w obszarze powiadomień paska zadań, a następnie kliknij przycisk **zatrzymać**. Następnie zaloguj się, jak normalne. Nawet wtedy, gdy serwer nie działa, możesz nadal zalogować. Zmodyfikuj wartość pola tekstowego, exit i uruchom ponownie, aby zobaczyć wartość zmodyfikowane.  
  
## <a name="summary"></a>Podsumowanie  
 W tym instruktażu przedstawiono sposób Włączanie i używanie usług aplikacji klienta w aplikacji Windows Forms. Po skonfigurowaniu serwera testowego, dodano kod do aplikacji do uwierzytelniania użytkowników oraz pobieranie ról użytkownika i ustawienia aplikacji z serwera. Przedstawiono również sposób włączania trybu offline, więc, że aplikacja używa lokalnej pamięci podręcznej zamiast usługi zdalnego, gdy połączenie jest niedostępny.  
  
## <a name="next-steps"></a>Następne kroki  
 W przypadku aplikacji rzeczywistych będzie dostęp do danych dla wielu użytkowników z serwera zdalnego, które mogą być niedostępne lub mogą obniżyć bez powiadomienia. Aby zapewnić niezawodne aplikacji, musisz odpowiedzieć odpowiednio do sytuacji, w których ta usługa nie jest dostępna. Ten instruktaż zawiera bloków try/catch do przechwytywania <xref:System.Net.WebException> i jest wyświetlany komunikat o błędzie, gdy usługa jest niedostępna. W kodzie produkcyjnym możesz chcieć obsługę tego przypadku przełączania do trybu offline, zakończeniem działania aplikacji lub odmawianie dostępu do określonych funkcji.  
  
 Aby zwiększyć bezpieczeństwo aplikacji, upewnij się staranne przetestowanie aplikacji i serwera przed przystąpieniem do wdrożenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi aplikacji klienckich](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [Omówienie usług aplikacji klienckich](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [Instrukcje: konfigurowanie usług aplikacji klienckich](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [Narzędzie Administratorskie witryny sieci Web platformy ASP.NET](https://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec)  
 [Tworzenie i Konfigurowanie bazy danych usługi aplikacji dla programu SQL Server](https://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)  
 [Przewodnik: Używanie usług aplikacji ASP.NET](https://msdn.microsoft.com/library/f3f394f0-20d6-4361-aa8f-4b21bf4933eb)
