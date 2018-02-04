---
title: "Wskazówki: używanie usług aplikacji klienta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application services host [client application services]
- client application services, walkthroughs
ms.assetid: bb7c8950-4517-4dae-b705-b74a14059b26
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 71eac85d07ac54cf15edcfcc3a86de58afef5004
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="walkthrough-using-client-application-services"></a>Wskazówki: używanie usług aplikacji klienta
W tym temacie opisano sposób tworzenia aplikacji systemu Windows, który korzysta z usługi aplikacji klienta do uwierzytelniania użytkowników i ról użytkownika i ustawienia.  
  
 W tym przewodniku należy wykonać następujące zadania:  
  
-   Tworzenie aplikacji formularzy systemu Windows i używanie [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] projektanta projektu, aby włączyć i skonfigurować usługi aplikacji klienta.  
  
-   Utwórz prostą aplikację usługi sieci Web ASP.NET do hostowania usług aplikacji i przetestować konfigurację klienta.  
  
-   Uwierzytelnianie formularzy można dodać do aplikacji. Rozpoczęcia przy użyciu nazwy ustalony użytkownika i hasło do testowania usługi. Formularz logowania spowoduje dodanie, określając jako dostawca poświadczeń w konfiguracji aplikacji.  
  
-   Dodawanie funkcji opartej na rolach, włączanie i wyświetlanie przycisk tylko dla użytkowników w roli "manager".  
  
-   Dostęp do ustawień sieci Web. Rozpocznie się przez załadowanie ustawień sieci Web dla użytkowników uwierzytelnionych (test) na **ustawienia** strony projektanta projektu. Następnie użyje Projektant formularzy systemu Windows można powiązać pole tekstowe do ustawienia sieci Web. Na koniec zapisze wartości zmodyfikowanej do serwera.  
  
-   Implementuje wylogowania. Spowoduje dodanie opcję Wyloguj w formularzu i wywołanie metody wylogowania.  
  
-   Włącz tryb offline. Zapewni pole wyboru, dzięki czemu użytkownicy mogą określić stanu połączenia. Ta wartość zostanie następnie użyta, aby określić, czy dostawcy usług aplikacji klienta będą używać buforowane lokalnie zamiast dostęp do swoich usług sieci Web. Ponownie zostanie koniec uwierzytelniania bieżącego użytkownika, gdy aplikacja powróci do trybu online.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Potrzebne są następujące składnika w tym przewodniku:  
  
-   [!INCLUDE[vs_orcas_long](../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-client-application"></a>Tworzenie aplikacji klienckiej  
 Pierwszą czynnością, który będzie do jest utworzenie projektu formularzy systemu Windows. W tym przewodniku zastosowano formularzy systemu Windows, ponieważ więcej osób zapoznać się z nią, ale proces jest podobny do projektów Windows Presentation Foundation (WPF).  
  
#### <a name="to-create-a-client-application-and-enable-client-application-services"></a>Aby utworzyć aplikację kliencką i włączyć usługi aplikacji klienta  
  
1.  W [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], wybierz pozycję **plik &#124; Nowy &#124; Projekt** opcji menu.  
  
2.  W **nowy projekt** okna dialogowego, **typy projektów** okienku rozwiń **Visual Basic** lub **Visual C#** węzeł i wybierz **Windows** typu projektu.  
  
3.  Upewnij się, że **.NET Framework 3.5** jest wybrany, a następnie wybierz **aplikacji Windows Forms** szablonu.  
  
4.  Zmień projekt **nazwa** do `ClientAppServicesDemo`, a następnie kliknij przycisk **OK**.  
  
     Nowy projekt formularzy systemu Windows jest otwarty w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
5.  Na **projektu** menu, wybierz opcję **ClientAppServicesDemo właściwości**.  
  
     Zostanie wyświetlone w Projektancie projektu.  
  
6.  Na **usług** wybierz opcję **włączyć usługi aplikacji klienckiej**.  
  
7.  Upewnij się, że **uwierzytelnianie formularzy użyj** jest zaznaczone, a następnie ustaw **lokalizacji usługi uwierzytelniania**, **ról usługi lokalizacji**, i **ustawienia w sieci Web usługi lokalizacji** do `http://localhost:55555/AppServices`.  
  
8.  Aby uzyskać [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]na **aplikacji** ustaw **tryb uwierzytelniania** do **zdefiniowanym przez aplikację**.  
  
 Projektant określonego ustawienia są przechowywane w pliku app.config aplikacji.  
  
 W tym momencie aplikacja jest skonfigurowana do dostępu wszystkie trzy usługi z tym samym hoście. W następnej sekcji zostanie utworzenie hosta jako prostą aplikację usługi sieci Web, dzięki któremu można przetestować konfigurację klienta.  
  
## <a name="creating-the-application-services-host"></a>Tworzenie aplikacji hosta usługi  
 W tej sekcji utworzysz prostą aplikację usługi sieci Web, która uzyskuje dostęp do danych użytkownika z lokalnego pliku bazy danych programu SQL Server Compact. Następnie, zostaną wyświetlone w bazie danych przy użyciu [narzędzia administrowania witryną sieci Web ASP.NET](http://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec). Ten prosty konfiguracja pozwala szybko przetestować aplikację klienta. Alternatywnie, można skonfigurować hosta usługi sieci Web do dostępu do danych użytkownika z pełnej bazy danych programu SQL Server lub za pomocą niestandardowych <xref:System.Web.Security.MembershipProvider> i <xref:System.Web.Security.RoleProvider> klasy. Aby uzyskać więcej informacji, zobacz [tworzenia i konfigurowania bazy danych usług aplikacji dla programu SQL Server](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2).  
  
 W poniższej procedurze Utwórz i skonfiguruj usługę sieci Web usługi aplikacji.  
  
#### <a name="to-create-and-configure-the-application-services-host"></a>Aby utworzyć i skonfigurować hosta usługi aplikacji  
  
1.  W **Eksploratora rozwiązań**, wybierz rozwiązanie ClientAppServicesDemo, a następnie na **pliku** menu, wybierz opcję **Dodaj &#124; Nowy projekt**.  
  
2.  W **Dodawanie nowego projektu** okna dialogowego, **typy projektów** okienku rozwiń **Visual Basic** lub **Visual C#** węzeł i wybierz  **Web** typu projektu.  
  
3.  Upewnij się, że **.NET Framework 3.5** jest wybrany, a następnie wybierz **aplikacji usługi sieci Web ASP.NET** szablonu.  
  
4.  Zmień projekt **nazwa** do `AppServices` , a następnie kliknij przycisk **OK**.  
  
     Nowy projekt aplikacji usługi sieci Web ASP.NET jest dodany do rozwiązania, a plik Service1.asmx.vb lub Service1.asmx.cs pojawi się w edytorze.  
  
    > [!NOTE]
    >  Plik Service1.asmx.vb lub Service1.asmx.cs nie będzie używany w tym przykładzie. Jeśli chcesz zasłaniać środowiska pracy, można go zamknąć i usunąć go z **Eksploratora rozwiązań**.  
  
5.  W **Eksploratora rozwiązań**, wybierz projekt usługi aplikacji, a następnie na **projektu** menu, wybierz opcję **właściwości usługi aplikacji**.  
  
     Zostanie wyświetlone w Projektancie projektu.  
  
6.  Na **Web** karcie, upewnij się, że **Użyj serwera wdrożeniowego Visual Studio** jest zaznaczone.  
  
7.  Wybierz **określonego portu**, określ wartość `55555`, a następnie ustaw **ścieżka wirtualna** do `/AppServices`.  
  
8.  Zapisz wszystkie pliki.  
  
9. W **Eksploratora rozwiązań**, otwórz plik Web.config i Znajdź `<system.web>` tagu początkowego.  
  
10. Dodaj następujący kod znaczników przed `<system.web>` tagu.  
  
     `authenticationService`, `profileService`, I `roleService` elementów w tym znaczników Włączanie i konfigurowanie usług aplikacji. Podczas testowania, `requireSSL` atrybutu `authenticationService` element jest ustawiony na wartość "false". `readAccessProperties` i `writeAccessProperties` atrybuty `profileService` elementu wskazują, że `WebSettingsTestText` właściwość jest odczytu/zapisu.  
  
    > [!NOTE]
    >  W kodzie produkcyjnym należy zawsze dostęp do usługi uwierzytelniania za pośrednictwem zabezpieczeń SSL (przy użyciu protokołu HTTPS SSL). Aby uzyskać informacje o konfigurowaniu protokołu SSL, zobacz [Konfigurowanie protokołu Secure Sockets Layer (IIS 6.0 Operations Guide)](http://go.microsoft.com/fwlink/?LinkId=91844).  
  
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
  
11. Dodaj następujący kod po `<system.web>` tagu początkowego tak, aby w ramach `<system.web>` elementu.  
  
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
  
 W poniższej procedurze używasz narzędzia administracyjnego witryny sieci Web ASP.NET Zakończ konfigurację usługi i umieścić w pliku lokalnej bazy danych. Spowoduje dodanie dwóch użytkowników o nazwie `employee` i `manager` należących do dwóch ról pod tą samą nazwą. Hasła użytkowników są `employee!` i `manager!` odpowiednio.  
  
#### <a name="to-configure-membership-and-roles"></a>Aby skonfigurować członkostwa i ról  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt usługi aplikacji, a następnie na **projektu** menu, wybierz opcję **konfiguracja platformy ASP.NET**.  
  
     **Narzędzia administrowania witryną sieci Web ASP.NET** pojawi się.  
  
2.  Na **zabezpieczeń** , kliknij pozycję **Użyj Kreatora konfiguracji zabezpieczeń, aby skonfigurować zabezpieczenia krok po kroku**.  
  
     **Kreatora konfiguracji zabezpieczeń** jest wyświetlany **powitalnej** kroku.  
  
3.  Kliknij przycisk **Dalej**.  
  
     **Wybierz metodę dostępu** pojawi się kroku.  
  
4.  Wybierz **z Internetu**. Spowoduje to skonfigurowanie usługi do korzystania z uwierzytelniania formularzy zamiast uwierzytelniania systemu Windows.  
  
5.  Kliknij przycisk **dalej** dwa razy.  
  
     **Zdefiniowanie ról** pojawi się kroku.  
  
6.  Wybierz **Włącz role dla tej witryny sieci Web**.  
  
7.  Kliknij przycisk **Dalej**. **Utwórz nową rolę** zostanie wyświetlony formularz.  
  
8.  W **Nazwa nowej roli** polu tekstowym `manager` , a następnie kliknij przycisk **Dodaj rolę**.  
  
     **Istniejących ról** znajduje się tabela z określoną wartością.  
  
9. W **Nazwa nowej roli** pole tekstowe, Zastąp `manager` z `employee` , a następnie kliknij przycisk **Dodaj rolę**.  
  
     Nowa wartość jest wyświetlana w **istniejących ról** tabeli.  
  
10. Kliknij przycisk **Dalej**.  
  
     **Dodaj nowych użytkowników** pojawi się kroku.  
  
11. W **Tworzenie użytkownika** tworzą, określ następujące wartości.  
  
  	|||  
  	|-|-|  
  	|**Nazwa użytkownika**|`manager`|  
  	|**Hasło**|`manager!`|  
  	|**Potwierdź hasło**|`manager!`|  
  	|**Poczta e-mail**|`manager@contoso.com`|  
  	|**Pytanie zabezpieczające**|`manager`|  
  	|**Odpowiedź zabezpieczeń**|`manager`|  
  
12. Kliknij przycisk **Utwórz użytkownika**.  
  
     Zostanie wyświetlony komunikat z potwierdzeniem.  
  
    > [!NOTE]
    >  **E-mail**, **pytanie zabezpieczające**, i **odpowiedź zabezpieczeń** wartości są wymagane przez formularz, ale nie są używane w tym przykładzie.  
  
13. Kliknij przycisk **Kontynuuj**.  
  
     **Tworzenie użytkownika** tworzą pojawi się.  
  
14. W **Tworzenie użytkownika** tworzą, określ następujące wartości.  
  
  	|||  
  	|-|-|  
  	|**Nazwa użytkownika**|`employee`|  
  	|**Hasło**|`employee!`|  
  	|**Potwierdź hasło**|`employee!`|  
  	|**Poczta e-mail**|`employee@contoso.com`|  
  	|**Pytanie zabezpieczające**|`Employee`|  
  	|**Odpowiedź zabezpieczeń**|`employee`|  
  
15. Kliknij przycisk **Utwórz użytkownika**.  
  
     Zostanie wyświetlony komunikat z potwierdzeniem.  
  
16. Kliknij przycisk **Zakończ**.  
  
     **Narzędzie do administrowania witryną sieci Web** pojawi się ponownie.  
  
17. Kliknij przycisk **użytkownicy Menedżera**.  
  
     Zostanie wyświetlona lista użytkowników.  
  
18. Kliknij przycisk **Edytuj role** dla **pracownika** użytkownika, a następnie wybierz **pracownika** roli.  
  
19. Kliknij przycisk **Edytuj role** dla **Menedżera** użytkownika, a następnie wybierz **Menedżera** roli.  
  
20. Zamknij okno przeglądarki, który jest hostem **narzędzie do administrowania witryną sieci Web**.  
  
21. Jeśli pojawia się komunikat z pytaniem, jeśli chcesz ponownie załadować zmodyfikowany plik Web.config, kliknij przycisk **tak**.  
  
 Na tym kończy się Instalatora usługi sieci Web. W tym momencie, naciśnij klawisz F5, aby uruchomić aplikację kliencką i **ASP.NET Development Server** rozpocznie się automatycznie wraz z aplikacji klienta. Serwer będzie nadal działać po zakończeniu zamknij aplikację, ale zostanie ponownie uruchomiony po ponownym uruchomieniu aplikacji. Dzięki temu można wykryć wszelkie zmiany wprowadzone w pliku Web.config.  
  
 Aby zatrzymać serwer ręcznie, kliknij prawym przyciskiem myszy ikonę programu ASP.NET Development Server, w obszarze powiadomień na pasku zadań, a następnie kliknij przycisk **zatrzymać**. Jest to przydatne od czasu do czasu upewnić się, że występuje prawidłowego ponownego uruchomienia.  
  
## <a name="adding-forms-authentication"></a>Dodanie uwierzytelniania formularzy  
 W poniższej procedurze należy dodać kodu do formularza głównego próbuje sprawdza, czy użytkownik, która odmawia dostępu, gdy użytkownik wprowadzi nieprawidłowe poświadczenia. Używasz nazwę ustalony użytkownika i hasło do testowania usługi.  
  
#### <a name="to-validate-the-user-in-your-application-code"></a>Aby zweryfikować użytkownika w kodzie aplikacji  
  
1.  W **Eksploratora rozwiązań**, w projekcie ClientAppServicesDemo Dodaj odwołanie do zestawu System.Web.  
  
2.  Wybierz plik Form1, a następnie wybierz **widoku &#124; Kod** z [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] menu głównego.  
  
3.  W edytorze kodu Dodaj następujące instrukcje na początku pliku Form1.  
  
     [!code-csharp[ClientApplicationServices#001](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#001)]
     [!code-vb[ClientApplicationServices#001](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#001)]  
  
4.  W **Eksploratora rozwiązań**, kliknij dwukrotnie Form1 można wyświetlić projektanta.  
  
5.  W projektancie, kliknij dwukrotnie powierzchni formularza, aby wygenerować <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> obsługi zdarzenia o nazwie `Form1_Load`.  
  
     Edytor kodu pojawi się kursor znajduje się w `Form1_Load` metody.  
  
6.  Dodaj następujący kod do `Form1_Load` metody.  
  
     Ten kod nie zezwala na dostęp do użytkowników nieuwierzytelnionych podczas zamykania aplikacji. Alternatywnie można udostępnić nieuwierzytelnionym użytkownikom formularza, ale odmowa dostępu do określonych funkcji. Zazwyczaj użytkownik zostanie nie zakodowane nazwy użytkownika i hasła, takie jak to, ale jest przydatna do celów testowych. W następnej sekcji tego kodu spowoduje zamianę bardziej niezawodne kodu, który wyświetla okno dialogowe logowania i obejmuje obsługi wyjątków.  
  
     Należy pamiętać, że `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metoda znajduje się w [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)]. Ta metoda deleguje pracy dostawcy uwierzytelniania skonfigurowane i zwraca `true` Jeśli uwierzytelnianie zakończy się pomyślnie. Aplikacja nie wymaga bezpośrednie odwołanie do dostawcy uwierzytelniania klienta.  
  
     [!code-csharp[ClientApplicationServices#300](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#300)]
     [!code-vb[ClientApplicationServices#300](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#300)]  
  
 Teraz naciśnij klawisz F5, aby uruchomić aplikację, a ponieważ podać poprawną nazwę użytkownika i hasła, będzie widoczny jest formularz.  
  
> [!NOTE]
>  Jeśli nie możesz uruchomić aplikację, spróbuj zatrzymać ASP.NET Development Server. Sprawdź, czy port jest ustawiony na 55555, po ponownym uruchomieniu serwera.  
  
 Aby wyświetlić komunikat o błędzie zamiast niego, należy zmienić <xref:System.Web.Security.Membership.ValidateUser%2A> parametrów. Na przykład zastąpić drugi `"manager!"` parametr przy użyciu niepoprawnego hasła, takich jak `"MANAGER"`.  
  
## <a name="adding-a-login-form-as-a-credentials-provider"></a>Dodawanie formularz logowania jako dostawcy poświadczeń  
 Możesz uzyskać poświadczenia użytkownika w kodzie aplikacji i przekazania ich do <xref:System.Web.Security.Membership.ValidateUser%2A> metody. Często jest jednak warto przechowywać kodu Uzyskiwanie poświadczeń osobno od kodu aplikacji, w przypadku, gdy chcesz zmienić go później.  
  
 W poniższej procedurze należy skonfigurować aplikację do używania dostawcy poświadczeń, a następnie zmień Twoje <xref:System.Web.Security.Membership.ValidateUser%2A> wywołanie metody do przekazania <xref:System.String.Empty> obydwu tych parametrów. Puste ciągi sygnału <xref:System.Web.Security.Membership.ValidateUser%2A> metodę do wywołania <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> metody dostawcy skonfigurowane poświadczenia.  
  
#### <a name="to-configure-your-application-to-use-a-credentials-provider"></a>Aby skonfigurować aplikację do korzystania z dostawcy poświadczeń  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt ClientAppServicesDemo, a następnie na **projektu** menu, wybierz opcję **ClientAppServicesDemo właściwości**.  
  
     Zostanie wyświetlone w Projektancie projektu.  
  
2.  Na **usług** ustaw **Opcjonalnie: Dostawca poświadczeń** wartość. Ta wartość wskazuje nazwę typu kwalifikowanego zestawu.  
  
    ```  
    ClientAppServicesDemo.Login, ClientAppServicesDemo  
    ```  
  
3.  W pliku kodu Form1, Zastąp kod w `Form1_Load` metodę z następującym kodem.  
  
     Ten kod zostanie wyświetlony komunikat powitalny, a następnie wywołuje `ValidateUsingCredentialsProvider` metody, który zostanie dodany w następnym kroku. Jeśli użytkownik nie jest uwierzytelniony, `ValidateUsingCredentialsProvider` metoda zwraca `false` i `Form1_Load` zwraca metody. Zapobiega to jakiegokolwiek dodatkowego kodu uruchomiona przed umożliwia zamknięcie aplikacji. Komunikat powitalny, warto wyjaśnić po ponownym uruchomieniu aplikacji. Należy dodać kod, aby ponownie uruchomić aplikację podczas implementowania wylogowania w dalszej części tego przewodnika.  
  
     [!code-csharp[ClientApplicationServices#011](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#011)]
     [!code-vb[ClientApplicationServices#011](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#011)]  
  
4.  Dodaj następującą metodę po `Form1_Load` metody.  
  
     Ta metoda przekazuje puste ciągi do `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metodę, która powoduje wyświetlenie okna dialogowego logowania. Jeśli usługa uwierzytelniania jest niedostępny, <xref:System.Web.Security.Membership.ValidateUser%2A> metoda zgłosi <xref:System.Net.WebException>. W takim przypadku `ValidateUsingCredentialsProvider` metoda wyświetla ostrzeżenie i zapyta, czy użytkownik chce ponownie w trybie offline. Ta funkcja wymaga **zapisać skrót hasła lokalnie, aby włączyć logowanie offline** funkcji opisanych w [porady: Konfigurowanie usługi aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md). Ta funkcja jest włączona domyślnie dla nowych projektów.  
  
     Jeśli użytkownik nie jest weryfikowany, `ValidateUsingCredentialsProvider` metoda wyświetla komunikat o błędzie i kończy działanie aplikacji. Ponadto ta metoda zwraca wynik próby uwierzytelnienia.  
  
     [!code-csharp[ClientApplicationServices#020](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#020)]
     [!code-vb[ClientApplicationServices#020](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#020)]  
  
### <a name="creating-a-login-form"></a>Tworzenie formularza logowania  
 Dostawca poświadczeń jest klasa implementująca <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> interfejsu. Ten interfejs zawiera tylko jedną metodę o nazwie <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> zwracającą <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> obiektu. W poniższych procedurach opisano sposób tworzenia okno dialogowe logowania, który implementuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> do wyświetlania samego i zwracać poświadczeń określonych przez użytkownika.  
  
 Oddzielne procedury są udostępniane dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] i C# ponieważ [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] zapewnia **formularz logowania** szablonu. Spowoduje to zapisanie pewien czas i kodowania wysiłku.  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-visual-basic"></a>Aby utworzyć okno dialogowe logowania jako dostawca poświadczeń w języku Visual Basic  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt ClientAppServicesDemo, a następnie na **projektu** menu, wybierz opcję **Dodaj nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **formularz logowania** szablonu, zmień element **nazwa** do `Login.vb`, a następnie kliknij przycisk **Dodaj** .  
  
     W narzędziu Projektant dla formularzy systemu Windows zostanie wyświetlone okno dialogowe logowania.  
  
3.  W projektancie, wybierz **OK** przycisk, a następnie w **właściwości** ustaw `DialogResult` do `OK`.  
  
4.  W projektancie, Dodaj `CheckBox` sterowania do formularza w obszarze **hasło** pola tekstowego.  
  
5.  W **właściwości** okna, określ **(nazwa)** wartość `rememberMeCheckBox` i **tekst** wartość `&Remember me`.  
  
6.  Wybierz **widoku &#124; Kod** z [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] menu głównego.  
  
7.  W edytorze kodu Dodaj następujący kod na początku pliku.  
  
     [!code-vb[ClientApplicationServices#101](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#101)]  
  
8.  Zmodyfikuj podpisu klasy tak, aby klasa implementuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> interfejsu.  
  
     [!code-vb[ClientApplicationServices#110](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#110)]  
  
9. Upewnij się, że kursor znajduje się po `IClientformsAuthenticationCredentialsProvider`, a następnie naciśnij klawisz ENTER, aby wygenerować `GetCredentials` metody.  
  
10. Zlokalizuj <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> implementacji i zastąp go następującym kodem.  
  
     [!code-vb[ClientApplicationServices#120](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#120)]  
  
 Poniższa procedura C# zawiera cały kod dla okno dialogowe prostego logowania. Układ dla tego okna dialogowego jest nieco surowych, ale jest ważnym elementem <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> implementacji.  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-c"></a>Aby utworzyć okno dialogowe logowania jako dostawca poświadczeń w języku C#  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt ClientAppServicesDemo, a następnie na **projektu** menu, wybierz opcję **Dodaj klasę**.  
  
2.  W **Dodaj nowy element** okno dialogowe, zmień **nazwa** do `Login.cs`, a następnie kliknij przycisk **Dodaj**.  
  
     Plik Login.cs zostanie otwarty w edytorze kodu.  
  
3.  Zastąp następujący kod w kodzie domyślnym.  
  
     [!code-csharp[ClientApplicationServices#200](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#200)]  
  
 Można teraz uruchomić aplikację i wyświetlić okno dialogowe logowania są wyświetlane. Do przetestowania tego kodu, spróbuj innych poświadczeń, prawidłowe i nieprawidłowe i upewnij się, że masz dostęp formularza tylko z prawidłowymi poświadczeniami. Prawidłowe nazwy użytkowników są `employee` i `manager` z hasłami `employee!` i `manager!` odpowiednio.  
  
> [!NOTE]
>  Nie zaznaczaj **Zapamiętaj moje** w tym punkcie lub użytkownik nie będzie mógł zalogować się jako inny użytkownik, dopóki nie implementuje wylogowania w dalszej części tego przewodnika.  
  
## <a name="adding-role-based-functionality"></a>Dodawanie funkcji opartej na rolach  
 W poniższej procedurze Dodawanie przycisku do formularza i wyświetl ją tylko dla użytkowników w roli menedżera.  
  
#### <a name="to-change-the-user-interface-based-on-user-role"></a>Aby zmienić interfejsu użytkownika na podstawie roli użytkownika  
  
1.  W **Eksploratora rozwiązań**, w projekcie ClientAppServicesDemo wybierz Form1, a następnie wybierz **widoku &#124; Projektant** z [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] menu głównego.  
  
2.  W projektancie, Dodaj <xref:System.Windows.Forms.Button> sterowania do formularza z **przybornika**.  
  
3.  W **właściwości** okna, ustaw następujące właściwości dla przycisku.  
  
  	|Właściwość|Wartość|  
  	|--------------|-----------|  
  	|**(Name)**|managerOnlyButton|  
  	|**Tekst**|& Menedżera zadań|  
  	|**Widoczne**|`False`|  
  
4.  W edytorze kodu dla Form1, Dodaj następujący kod na końcu `Form1_Load` metody.  
  
     Ten kod wywołuje `DisplayButtonForManagerRole` metody, który zostanie dodany w następnym kroku.  
  
     [!code-csharp[ClientApplicationServices#012](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#012)]
     [!code-vb[ClientApplicationServices#012](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#012)]  
  
5.  Dodaj następującą metodę w celu klasy Form1.  
  
     Ta metoda wywołuje <xref:System.Security.Principal.IPrincipal.IsInRole%2A> metody <xref:System.Security.Principal.IPrincipal> zwrócony przez `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> właściwości. Aplikacje skonfigurowane do korzystania z usługi aplikacji klienta, ta właściwość zwraca <xref:System.Web.ClientServices.ClientRolePrincipal>. Ponieważ ta klasa implementuje <xref:System.Security.Principal.IPrincipal> interfejsu, nie trzeba jawnie odwoływać.  
  
     Jeśli użytkownik jest w roli "manager" `DisplayButtonForManagerRole` zestawy metody <xref:System.Windows.Forms.Control.Visible%2A> właściwość `managerOnlyButton` do `true`. Jeśli ta metoda także wyświetla komunikat o błędzie <xref:System.Net.WebException> jest zgłaszany, co oznacza, że usługa ról jest niedostępna.  
  
    > [!NOTE]
    >  <xref:System.Web.ClientServices.ClientRolePrincipal.IsInRole%2A> Metoda zawsze zwraca `false` Jeśli logowanie użytkownika wygasło. To nie występuje w przypadku aplikacji wywołuje <xref:System.Security.Principal.IPrincipal.IsInRole%2A> metody jeden raz wkrótce po uwierzytelnieniu, jak pokazano przykład kodu dla tego przewodnika. Jeśli aplikacja musi pobrać ról użytkownika w innym czasie, można dodać kod, aby ponownie sprawdź poprawność użytkowników, których logowanie wygasło. W przypadku wszystkich użytkowników przypisanych do ról, można określić, czy logowanie wygasło przez wywołanie metody <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A?displayProperty=nameWithType> metody. Jeśli nie zostały zwrócone żadne role, logowanie wygasło. Na przykład z tej funkcji, zobacz <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A> metody. Ta funkcja jest wymagane, jeśli wybrano tylko **wymagać od użytkowników zalogować się ponownie przy każdym wygasa plik cookie z serwera** w konfiguracji aplikacji. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie usługi aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
     [!code-csharp[ClientApplicationServices#030](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#030)]
     [!code-vb[ClientApplicationServices#030](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#030)]  
  
 Jeśli uwierzytelnianie zakończy się pomyślnie, Ustawia dostawcę uwierzytelniania klienta <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> dla właściwości wystąpienia <xref:System.Web.ClientServices.ClientRolePrincipal> klasy. Ta klasa implementuje <xref:System.Security.Principal.IPrincipal.IsInRole%2A> metody, aby praca jest delegowane do roli skonfigurowanego dostawcy. Jako przed, kod aplikacji nie wymaga bezpośrednie odwołanie do dostawcy usług.  
  
 Można teraz uruchomić aplikację i zaloguj się jako pracowników, czy przycisk nie są wyświetlane, a następnie zaloguj się jako manager, aby wyświetlić przycisk.  
  
## <a name="accessing-web-settings"></a>Uzyskiwanie dostępu do ustawień sieci Web  
 W poniższej procedurze Dodaj pole tekstowe do formularza i powiązać go z ustawienia sieci Web. Jak poprzedni kod, który korzysta z uwierzytelniania i ról ustawień kodu nie Dostawca ustawień bezpośredni dostęp. Zamiast tego używa jednoznacznie `Settings` klasy (dostępne jako `Properties.Settings.Default` w języku C# i `My.Settings` w [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) wygenerowana dla projektu przez [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
#### <a name="to-use-web-settings-in-your-user-interface"></a>Aby użyć ustawień sieci Web w interfejsie użytkownika  
  
1.  Upewnij się, że **serwera wdrożeniowego sieci Web ASP.NET** jest nadal uruchomiona, sprawdzając obszarze powiadomień paska zadań. Zatrzymanie serwer ponownie uruchom aplikację (który jest uruchamiany automatycznie serwera), a następnie zamknij okno dialogowe logowania.  
  
2.  W **Eksploratora rozwiązań**, wybierz projekt ClientAppServicesDemo, a następnie na **projektu** menu, wybierz opcję **ClientAppServicesDemo właściwości**.  
  
     Zostanie wyświetlone w Projektancie projektu.  
  
3.  Na **ustawienia** , kliknij pozycję **ustawień sieci Web obciążenia**.  
  
     A **logowania** zostanie wyświetlone okno dialogowe.  
  
4.  Wprowadź poświadczenia dla pracowników lub manager i kliknij przycisk **dziennika w**. Ustawienia sieci Web będzie używany jest skonfigurowana dla dostępu przez, uwierzytelnionym użytkownikom tego klikając **logowania Pomiń** wszystkie ustawienia nie zostanie załadowany.  
  
     `WebSettingsTestText` Ustawienie jest wyświetlane w Projektancie z wartością domyślną `DefaultText`. Ponadto `Settings` klasę, która zawiera `WebSettingsTestText` właściwości jest generowany dla projektu.  
  
5.  W **Eksploratora rozwiązań**, w projekcie ClientAppServicesDemo wybierz Form1, a następnie wybierz **widoku &#124; Projektant** z [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] menu głównego.  
  
6.  W projektancie, Dodaj <xref:System.Windows.Forms.TextBox> sterowania do formularza.  
  
7.  W **właściwości** okna, określ **(nazwa)** wartość `webSettingsTestTextBox`.  
  
8.  W edytorze kodu, Dodaj następujący kod na końcu `Form1_Load` metody.  
  
     Ten kod wywołuje `BindWebSettingsTestTextBox` metody, który zostanie dodany w następnym kroku.  
  
     [!code-csharp[ClientApplicationServices#013](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#013)]
     [!code-vb[ClientApplicationServices#013](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#013)]  
  
9. Dodaj następującą metodę w celu klasy Form1.  
  
     Ta metoda wiąże <xref:System.Windows.Forms.TextBox.Text%2A> właściwość `webSettingsTestTextBox` do `WebSettingsTestText` właściwość `Settings` klasy generowane we wcześniejszej części tej procedury. Jeśli ta metoda także wyświetla komunikat o błędzie <xref:System.Net.WebException> jest zgłaszany, co oznacza, że ustawienia usługi sieci Web jest niedostępna.  
  
     [!code-csharp[ClientApplicationServices#040](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#040)]
     [!code-vb[ClientApplicationServices#040](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#040)]  
  
    > [!NOTE]
    >  Aby włączyć automatyczne dwukierunkowej komunikacji między formantem a ustawienia sieci Web zwykle użyje wiązania z danymi. Jednakże można także przejść do ustawień sieci Web bezpośrednio, jak pokazano w poniższym przykładzie:  
  
     [!code-csharp[ClientApplicationServices#322](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#322)]
     [!code-vb[ClientApplicationServices#322](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#322)]  
  
10. W projektancie, wybierz formularz, a następnie w **właściwości** okna, kliknij przycisk **zdarzenia** przycisku.  
  
11. Wybierz <xref:System.Windows.Forms.Form.FormClosing> zdarzeń, a następnie naciśnij klawisz ENTER, aby wygenerować program obsługi zdarzeń.  
  
12. Zastąp metodę wygenerowanego następującym kodem.  
  
     <xref:System.Windows.Forms.Form.FormClosing> Wywołań obsługi zdarzeń `SaveSettings` metodę, która jest już używana przez funkcji wylogowania, który zostanie dodany w następnej sekcji. `SaveSettings` Metody najpierw sprawdza, czy użytkownik nie zalogował. Robi to poprzez sprawdzenie <xref:System.Security.Principal.IIdentity.AuthenticationType%2A> właściwość <xref:System.Security.Principal.IIdentity> zwrócony przez bieżący podmiot zabezpieczeń. Bieżący podmiot zabezpieczeń jest pobierane w drodze `static` <xref:System.Threading.Thread.CurrentPrincipal%2A> właściwości. Jeśli użytkownik został uwierzytelniony dla usług aplikacji klienta, typ uwierzytelniania będzie "ClientForms". `SaveSettings` Metoda po prostu nie można sprawdzić <xref:System.Security.Principal.IIdentity.IsAuthenticated%2A?displayProperty=nameWithType> właściwości ponieważ użytkownik może być nieprawidłowa tożsamość systemu Windows po wylogowania.  
  
     Jeśli użytkownik nie zalogował się, `SaveSettings` wywołania metody <xref:System.Configuration.ApplicationSettingsBase.Save%2A> metody `Settings` klasy generowane we wcześniejszej części tej procedury. Ta metoda może zgłosić <xref:System.Net.WebException> po wygaśnięciu ważności pliku cookie uwierzytelniania. Dzieje się tak tylko wtedy, gdy wybrano **wymagać od użytkowników zalogować się ponownie przy każdym wygasa plik cookie z serwera** w konfiguracji aplikacji. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie usługi aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md). `SaveSettings` Metoda obsługuje datę ważności pliku cookie, wywołując <xref:System.Web.Security.Membership.ValidateUser%2A> Aby wyświetlić okno dialogowe logowania. Jeśli użytkownik loguje się pomyślnie, `SaveSettings` metoda próbuje ponownie zapisać ustawienia, wywołując sam.  
  
     Podobnie jak w poprzednim kodzie `SaveSettings` metoda wyświetla komunikat o błędzie, jeśli usługa zdalna jest niedostępna. Jeśli dostawca ustawień nie może uzyskać dostęp do usługi zdalnej, ustawienia nadal są zapisane w lokalnej pamięci podręcznej i ponownie załadowany po uruchomieniu aplikacji.  
  
     [!code-csharp[ClientApplicationServices#050](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#050)]
     [!code-vb[ClientApplicationServices#050](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#050)]  
  
13. Dodaj następującą metodę w celu klasy Form1.  
  
     Ten kod obsługi <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved?displayProperty=nameWithType> zdarzeń i wyświetla ostrzeżenie, jeśli ustawienia nie można zapisać. <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> Zdarzenie nie występuje, jeśli usługa ustawienia jest niedostępna lub plik cookie uwierzytelniania wygasł. Jednym z przykładów sytuacji, w których <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> zdarzenie wystąpi, jest, jeśli użytkownik zalogował się już. Ten program obsługi zdarzeń można przetestować przez dodanie kodu wylogowania się `SaveSettings` metody bezpośrednio przed <xref:System.Configuration.ApplicationSettingsBase.Save%2A> wywołania metody. W następnej sekcji opisano wylogowania kod, który można użyć.  
  
     [!code-csharp[ClientApplicationServices#090](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#090)]
     [!code-vb[ClientApplicationServices#090](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#090)]  
  
14. Język C#, Dodaj następujący kod na końcu `Form1_Load` metody. Ten kod kojarzy metody dodanym w ostatnim kroku z <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> zdarzeń.  
  
     [!code-csharp[ClientApplicationServices#015](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#015)]  
  
 Aby przetestować aplikację na tym etapie, uruchom go wielokrotnie jako pracowników i menedżera, a następnie wpisz różne wartości w polu tekstowym. Wartości będzie zachowywane między sesjami na poszczególnych użytkowników.  
  
## <a name="implementing-logout"></a>Implementowanie wylogowania  
 Gdy użytkownik wybierze **Zapamiętaj moje** pole wyboru podczas logowania w aplikacji zostanie automatycznie uwierzytelnienia użytkownika w kolejnych uruchomieniach. Następnie będzie automatycznego uwierzytelniania, podczas gdy aplikacja jest w trybie offline lub do momentu wygaśnięcia pliku cookie uwierzytelniania. Czasami jednak wielu użytkowników wymaga dostępu do aplikacji lub pojedynczego użytkownika od czasu do czasu może zalogować się przy użyciu innych poświadczeń. Aby włączyć ten scenariusz, musi implementować funkcji wylogowania, zgodnie z opisem w poniższej procedurze.  
  
#### <a name="to-implement-logout-functionality"></a>Aby zaimplementować funkcji wylogowania  
  
1.  W Projektancie Form1 dodać <xref:System.Windows.Forms.Button> sterowania do formularza z **przybornika**.  
  
2.  W **właściwości** okna, określ **(nazwa)** wartość `logoutButton` i **tekst** wartość **& Wyloguj**.  
  
3.  Kliknij dwukrotnie `logoutButton` do generowania <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń.  
  
     Edytor kodu pojawi się kursor znajduje się w `logoutButton_Click` metody.  
  
4.  Zastąp wygenerowany `logoutButton_Click` metodę z następującym kodem.  
  
     Ten program obsługi zdarzeń najpierw wywołuje `SaveSettings` metody dodanego w poprzedniej sekcji. Następnie wywołuje program obsługi zdarzeń <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A?displayProperty=nameWithType> metody. Jeśli usługa uwierzytelniania jest niedostępny, <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A> metoda zgłosi <xref:System.Net.WebException>. W takim przypadku `logoutButton_Click` metoda wyświetla ostrzeżenie i tymczasowo przełączenie do trybu offline, aby wylogować użytkownika. W następnej sekcji opisano w trybie offline.  
  
     Wyloguj usuwa plik cookie uwierzytelniania lokalnego, że logowanie będzie wymagane po uruchomieniu aplikacji. Po wylogowania program obsługi zdarzeń, uruchamia ponownie aplikację. Wyświetla komunikat powitalny, a następnie okno dialogowe logowania po uruchomieniu aplikacji. Komunikat powitalny sprawia, że wynika, że aplikacja została uruchomiona ponownie. Zapobiega to potencjalnych pomyłek, jeśli użytkownik musi zalogować się do zapisania ustawień, a następnie należy zalogować się ponownie, ponieważ aplikacja została uruchomiona ponownie.  
  
     [!code-csharp[ClientApplicationServices#070](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#070)]
     [!code-vb[ClientApplicationServices#070](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#070)]  
  
 Aby przetestować funkcje wylogowania, uruchom aplikację, a następnie wybierz **Zapamiętaj moje** w oknie dialogowym logowania. Następnie zamknij i ponownie uruchom aplikację, aby upewnić się, że nie masz już do logowania się w. Na koniec należy ponownie uruchomić aplikację, klikając wylogowania.  
  
## <a name="enabling-offline-mode"></a>Włączanie trybu Offline  
 W poniższej procedurze pole wyboru jest dodawanie do formularza, aby umożliwić użytkownikowi przejście do trybu offline. Aplikacja wskazuje w trybie offline przez ustawienie `static` <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A?displayProperty=nameWithType> właściwości `true`. Stan offline jest przechowywany na lokalnym dysku twardym w lokalizacji wskazanej przez <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> właściwości. Oznacza to, że stan offline jest przechowywany na poszczególnych użytkowników, poszczególnych aplikacji, co.  
  
 W trybie offline wszystkie żądania usługi aplikacji klienta pobierać dane z lokalnej pamięci podręcznej, zamiast w trakcie uzyskiwania dostępu do usług. W konfiguracji domyślnej dane lokalne zawierają zaszyfrowane hasło użytkownika. Dzięki temu użytkownikowi na logowanie, podczas gdy aplikacja jest w trybie offline. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie usługi aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
#### <a name="to-enable-offline-mode-in-your-application"></a>Aby włączyć tryb offline w aplikacji  
  
1.  W **Eksploratora rozwiązań**, w projekcie ClientAppServicesDemo wybierz Form1, a następnie wybierz **widoku &#124; Projektant** z [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] menu głównego.  
  
2.  W projektancie, Dodaj <xref:System.Windows.Forms.CheckBox> sterowania do formularza.  
  
3.  W **właściwości** okna, określ **(nazwa)** wartość `workOfflineCheckBox` i **tekst** wartość **& pracy w trybie offline**.  
  
4.  W **właściwości** okna, kliknij przycisk **zdarzenia** przycisku.  
  
5.  Wybierz <xref:System.Windows.Forms.CheckBox.CheckedChanged> zdarzeń, a następnie naciśnij klawisz ENTER, aby wygenerować program obsługi zdarzeń.  
  
6.  Zastąp metodę wygenerowanego następującym kodem.  
  
     Ten kod aktualizacji <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> wartości i dyskretnej revalidates użytkownika, gdy zwracają do trybu online. <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A?displayProperty=nameWithType> — Metoda używa buforowanych poświadczeń, dzięki czemu użytkownik nie ma jawnie zalogowania. Jeśli usługa uwierzytelniania jest niedostępny, zostanie wyświetlone ostrzeżenie, a sama aplikacja pozostaje w trybie offline.  
  
    > [!NOTE]
    >  <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A> Metoda jest jedynie jako udogodnienie. Ponieważ nie ma wartości zwracanej, nie może wskazać, czy ponowna Walidacja nie powiodła się. Ponowna Walidacja może zakończyć się niepowodzeniem, na przykład, jeśli poświadczenia użytkownika zostały zmienione na serwerze. W takim przypadku można dołączać kod jawnie weryfikującą użytkowników po wywołaniu usługi nie powiedzie się. Aby uzyskać więcej informacji zobacz sekcję ustawień dostępu do sieci Web we wcześniejszej części tego przewodnika.  
  
     Po ponownego sprawdzania poprawności, ten kod zapisuje zmiany w ustawieniach lokalnych sieci Web przez wywołanie metody `SaveSettings` metody dodanego wcześniej. Następnie pobiera wszystkie nowe wartości na serwerze przez wywołanie metody <xref:System.Configuration.ApplicationSettingsBase.Reload%2A> metody projektu `Settings` klasy (dostępne jako `Properties.Settings.Default` w języku C# i `My.Settings` w [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).  
  
     [!code-csharp[ClientApplicationServices#080](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#080)]
     [!code-vb[ClientApplicationServices#080](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#080)]  
  
7.  Dodaj następujący kod na końcu `Form1_Load` metody, aby upewnić się, że pole wyboru Wyświetla bieżący stan połączenia.  
  
     [!code-csharp[ClientApplicationServices#014](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#014)]
     [!code-vb[ClientApplicationServices#014](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#014)]  
  
 Na tym kończy się przykładowej aplikacji. Aby przetestować tryb offline, uruchom aplikację, zaloguj się jako pracowników lub manager, a następnie wybierz **pracy w trybie offline**. Zmodyfikuj wartość w polu tekstowym, a następnie zamknij aplikację. Uruchom ponownie aplikację. Przed zalogowaniem się, kliknij prawym przyciskiem myszy ikonę programu ASP.NET Development Server, w obszarze powiadomień na pasku zadań, a następnie kliknij przycisk **zatrzymać**. Następnie zaloguj, takich jak normalnym. Nawet wtedy, gdy serwer nie działa, możesz nadal zalogować. Zmodyfikuj wartość pola tekstowego, exit i uruchom ponownie, aby wyświetlić wartości zmodyfikowanej.  
  
## <a name="summary"></a>Podsumowanie  
 W tym przewodniku przedstawiono sposób włączenia i korzystania z usługi aplikacji klienta w aplikacji formularzy systemu Windows. Po skonfigurowaniu to serwer testowy, dodano kod do aplikacji, do uwierzytelniania użytkowników i pobrać ustawienia aplikacji i ról użytkownika z serwera. Przedstawiono również sposób włączyć w trybie offline, dzięki czemu aplikacja używa pamięci podręcznej danych lokalnych zamiast usługi zdalnego, gdy połączenie jest niedostępny.  
  
## <a name="next-steps"></a>Następne kroki  
 W przypadku aplikacji rzeczywistych będą uzyskiwać dostęp do danych dla wielu użytkowników z serwera zdalnego, który może być niedostępne lub mogą przestaną działać bez uprzedzenia. Aby aplikacja niezawodne, użytkownik musi odpowiedzieć odpowiednio do sytuacji, gdy usługa jest niedostępna. Ten przewodnik zawiera bloki try/catch do wychwytywania <xref:System.Net.WebException> i wyświetlane komunikaty o błędach, gdy usługa jest niedostępna. W kodzie produkcyjnym można obsłużyć tego przypadku przełączania do trybu offline, zamykanie aplikacji lub odmawiania dostępu do określonych funkcji.  
  
 Aby zwiększyć bezpieczeństwo aplikacji, upewnij się, że dokładnie przetestować aplikację i serwera przed przystąpieniem do wdrożenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi aplikacji klienckich](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [Omówienie usług aplikacji klienckich](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [Instrukcje: konfigurowanie usług aplikacji klienckich](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [Narzędzie do administrowania witryną sieci Web ASP.NET](http://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec)  
 [Tworzenie i Konfigurowanie bazy danych usług aplikacji dla programu SQL Server](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)  
 [Wskazówki: Korzystanie z usługi aplikacji platformy ASP.NET](http://msdn.microsoft.com/library/f3f394f0-20d6-4361-aa8f-4b21bf4933eb)
