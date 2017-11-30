---
title: "Przegląd usług aplikacji klienta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- client application services, classes
- client application services, about client application services
ms.assetid: f0a2da13-e282-4fd7-88a1-f9102c9aeab1
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e5719cf7cfb5ec99f1bfbf952048e98c9465e1fa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="client-application-services-overview"></a>Przegląd usług aplikacji klienta
Usługi aplikacji klienta udostępnienia uproszczony [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] logowania, ról i usług profilu w aplikacjach formularzy systemu Windows i Windows Presentation Foundation (WPF). [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)]usługi aplikacji znajdują się w Microsoft ASP.NET 2.0 AJAX rozszerzeń, które jest dołączana do [!INCLUDE[vs_orcas_long](../../../includes/vs-orcas-long-md.md)] i [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]. Te usługi umożliwiają wielu sieci Web i aplikacji do udostępniania informacji o użytkowniku i funkcje z zakresu zarządzania użytkownika z jednego serwera systemu Windows.  
  
 Usługi aplikacji klienta obejmują dostawców usług klienta, które Podłącz do modelu rozszerzalności usług sieci Web, aby umożliwić następujące funkcje dla aplikacji systemu Windows:  
  
-   Konfiguracja klienta proste. Można włączyć i skonfigurować logowania, ról i usług profilu przy użyciu [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] projektu projektanta lub określając klienta dostawcy usług w pliku App.config projektu. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie usługi aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
-   Proste programowania. Po włączona i skonfigurowana z usługi aplikacji klienta, możesz mają dostęp do dostawcy usług pośrednio przez istniejące [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] członkostwo, role i klasy ustawienia aplikacji. Można również uzyskać dostęp do [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] klas implementujących usługi aplikacji klienta. Jednak w większości przypadków bezpośredniego dostępu jest niepotrzebna. Aby uzyskać więcej informacji na temat klas usługi aplikacji klienta Zobacz sekcję "Klasy usług aplikacji klienta" w tym temacie.  
  
-   Obsługa w trybie offline. Aplikacje systemu Windows często mają działanie w środowiskach od czasu do czasu połączenia. Gdy aplikacja jest w trybie online, dostawców usług klienta będą buforowane wartości pobrany z serwera do użycia, gdy aplikacja jest w trybie offline.  
  
-   Integracja z [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] projektanta ustawień aplikacji. Po dodaniu ustawienia projektu w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], można określić ustawienia, które mają być dostępne za pośrednictwem dostawcy usług ustawienia klienta.  
  
 W poniższych sekcjach opisano te funkcje bardziej szczegółowo. Aby uzyskać więcej informacji na temat [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] usług aplikacji, zobacz [przegląd usług aplikacji ASP.NET](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).  
  
## <a name="authentication"></a>Uwierzytelnianie  
 Usługi aplikacji klienta można użyć do zweryfikowania użytkownika za pomocą istniejącej [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] usługi uwierzytelniania. Użytkownika można sprawdzić za pomocą uwierzytelniania systemu Windows lub formularzy. Uwierzytelnianie systemu Windows oznacza, że tożsamość użytkownika podanej przez system operacyjny, po zalogowaniu użytkownika na komputerze lub w domenie. Zwykle użyje uwierzytelniania systemu Windows przy użyciu aplikacji wdrożonych w intranecie firmowym. Uwierzytelnianie formularzy oznacza, że należy umieścić kontrolek logowania w aplikacji i przekazywania poświadczeń nabytych przez niego do dostawcy uwierzytelniania. Będą zwykle używać uwierzytelniania formularzy z aplikacji wdrożone w Internecie.  
  
 Aby sprawdzić poprawność użytkownika, należy wywołać `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metody. Ta metoda uzyskuje dostęp do dostawcy usług klienta skonfigurowanych dla aplikacji i zwraca <xref:System.Boolean> wartość wskazującą, czy użytkownik jest nieprawidłowy. Aby uzyskać więcej informacji, zobacz [porady: Implementowanie logowania użytkownika z usługi aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md).  
  
 Podczas korzystania z uwierzytelniania systemu Windows, należy podać puste ciągi lub `null` jako parametry <xref:System.Web.Security.Membership.ValidateUser%2A> metody. Podczas korzystania z uwierzytelniania systemu Windows, zawsze zwróci wywołanie tej metody `true`.  
  
 Za pomocą uwierzytelniania formularzy <xref:System.Web.Security.Membership.ValidateUser%2A> metoda zwraca wartość wskazującą, czy usługa zdalnego uwierzytelnieniu użytkownika. Jeśli weryfikacja zakończy się pomyślnie, pliku cookie uwierzytelniania są przechowywane na lokalnym dysku twardym. Ten plik cookie jest używany w celu potwierdzenia weryfikacji podczas uzyskiwania dostępu do ról i ustawienia usług.  
  
 Podczas korzystania z uwierzytelniania formularzy, można przekazać nazwę użytkownika i hasło, aby <xref:System.Web.Security.Membership.ValidateUser%2A> metody. Można również przekazać puste ciągi lub `null` jako parametry do używania dostawcy poświadczeń. Dostawca poświadczeń jest klasa, która zapewniają i określ w konfiguracji aplikacji. Klasa dostawcy poświadczeń musi implementować <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> interfejs, który zawiera tylko jedną metodę o nazwie <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A>. Za pomocą dostawcy poświadczeń umożliwia udostępnianie okno dialogowe logowania pojedynczego między wieloma aplikacjami. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie usługi aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
 Po skonfigurowaniu aplikacji do korzystania z dostawcy poświadczeń za pomocą uwierzytelniania formularzy, należy przekazać puste ciągi lub `null` jako parametry <xref:System.Web.Security.Membership.ValidateUser%2A> metody. Następnie wywoła dostawcę usługi programu <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A?displayProperty=nameWithType> implementacji metody. Zazwyczaj będzie zaimplementuj tę metodę, aby wyświetlić okno dialogowe i wrócić wypełnione <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> obiektu.  
  
 Aby uzyskać więcej informacji na temat uwierzytelniania, zobacz [Uwierzytelnianie ASP.NET](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1). Aby uzyskać informacje dotyczące sposobu konfigurowania [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] usługi uwierzytelniania, zobacz [przy użyciu uwierzytelniania formularzy z Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e).  
  
## <a name="roles"></a>Role  
 Usługi aplikacji klienta można użyć do pobierania informacji o roli z istniejącego [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] usługi ról. Aby ustalić, czy obecnie uwierzytelniony użytkownik jest w określonej roli, należy wywołać <xref:System.Security.Principal.IPrincipal.IsInRole%2A> metody <xref:System.Security.Principal.IPrincipal> odwołania są pobierane z `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> właściwości. <xref:System.Security.Principal.IPrincipal.IsInRole%2A> Metoda przyjmuje nazwę roli jako parametr i zwraca <xref:System.Boolean> wartość wskazującą, czy aktualny użytkownik ma określoną rolę. Ta metoda zwróci `false` Jeśli użytkownik nie jest uwierzytelniony, lub nie znajduje się w określonej roli.  
  
 Aby uzyskać informacje dotyczące sposobu konfigurowania [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] usługi ról, zobacz [przy użyciu ról informacji o Microsoft Ajax](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d).  
  
## <a name="settings"></a>Ustawienia  
 Usługi aplikacji klienta można użyć do pobierania ustawień aplikacji użytkownika z istniejącego [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profilu usługi. Usługi aplikacji klienta funkcja ustawień sieci Web integruje się z funkcją ustawień aplikacji dostępnych w [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)]. Aby pobrać ustawienia sieci Web, należy najpierw Generowanie `Settings` klasy (dostępne jako `Properties.Settings.Default` w języku C# i `My.Settings` w [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) projektu za pomocą **ustawienia** na karcie [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] projektanta projektu. Na **ustawienia** kartę, można użyć **ustawień sieci Web obciążenia** przycisk, aby pobrać ustawienia sieci Web i dodaj je do wygenerowanej `Settings` klasy. Można użyć ustawień sieci Web skonfigurowana do użycia przez wszystkich użytkowników uwierzytelnionych lub wszyscy użytkownicy anonimowi.  
  
 Aby uzyskać więcej informacji na temat ustawień aplikacji, zobacz [Przegląd ustawień aplikacji](../../../docs/framework/winforms/advanced/application-settings-overview.md). Informacje na temat implementowania własne ustawienia klasy zamiast generowania w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], zobacz [porady: Tworzenie ustawień aplikacji](../../../docs/framework/winforms/advanced/how-to-create-application-settings.md). Aby uzyskać informacje dotyczące sposobu konfigurowania [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profilu usługi, zobacz [przy użyciu informacji o profilu z Microsoft Ajax](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61).  
  
## <a name="client-application-services-classes"></a>Klasy usługi aplikacji klienta  
 W poniższej tabeli opisano klasy, które implementują funkcji usług aplikacji klienta.  
  
 Aplikacje używające tylko podstawowego uwierzytelniania, ról i funkcji ustawienia nie będzie miał dostęp do tych klas bezpośrednio. Zamiast tego takich aplikacji będą uzyskiwać dostęp do dostawcy usług aplikacji klienta pośrednio przy użyciu konfiguracji aplikacji i interfejsów API, opisanych w poprzednich sekcjach. Będą uzyskiwać dostęp do tych klas bezpośrednio, aby zaimplementować dodatkowe funkcje, takie jak wylogowania użytkownika i możliwości w trybie offline.  
  
> [!NOTE]
>  Usługi aplikacji klienta wszystkie interfejsy API są synchroniczne. Usługi aplikacji klienta nie obsługują bezpośrednio zachowanie asynchronicznego.  
  
 Dostawcy usług aplikacji klienta implementuje lub rozszerzyć standard [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] typów, gdy nie implementuje każdy element członkowski i funkcji zdefiniowanych przez te typy. Na przykład nie można użyć dostawcy usług aplikacji klienta do wdrożenia aplikacji do zarządzania użytkownika do tworzenia nowych użytkowników i zarządzania członkostwem w rolach. Aby zaimplementować tę funkcję, należy użyć obecnie kod po stronie serwera i aplikacji sieci Web. Aby określić, elementów członkowskich, które nie są zaimplementowane, zobacz dokumentacja odwołania, które są dostępne linki w tej tabeli.  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.Web.ClientServices.ClientFormsIdentity>|Ta klasa zarządza użytkownik uwierzytelnianie i tożsamość pliki cookie uwierzytelniania formularzy.<br /><br /> Podstawowym powodem bezpośredni dostęp do tej klasy jest wywołanie <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A> metodę, która w trybie dyskretnym revalidates użytkownika (na przykład podczas przełączania z trybu offline do trybu online).<br /><br /> Po uwierzytelnieniu użytkownika przy użyciu uwierzytelniania formularzy można pobrać wystąpienia tej klasy przy użyciu <xref:System.Security.Principal.IPrincipal.Identity%2A> właściwość <xref:System.Security.Principal.IPrincipal> odwołania pobierane w drodze `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> właściwości.|  
|<xref:System.Web.ClientServices.ClientRolePrincipal>|Ta klasa zarządza ról użytkownika.<br /><br /> Ta klasa nie ma żadnych elementów członkowskich, których nie można uzyskać dostępu bezpośrednio. Jednak po uwierzytelnieniu użytkownika są dostępne wystąpienia tej klasy przy użyciu `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> właściwości.|  
|<xref:System.Web.ClientServices.ConnectivityStatus>|Ta klasa udostępnia `static` <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> właściwość, która umożliwia przełączanie aplikacji do trybu offline.|  
|<xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>|Ta klasa reprezentuje poświadczeń użytkownika.<br /><br /> Ta klasa będzie używany tylko jako typ zwracanej wartości <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> metody podczas implementowania <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> interfejsu.|  
|<xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider>|Ta klasa zarządza dostępem do usługi uwierzytelniania zdalnego uwierzytelniania formularzy.<br /><br /> Podstawowym powodem bezpośredni dostęp do tej klasy jest użycie jej <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A> i <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.UserValidated> elementów członkowskich, które nie zostały zaimplementowane przez podstawę <xref:System.Web.Security.MembershipProvider> klasy. Można również ustawić lokalizacji usługi programowo przy użyciu <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.ServiceUri%2A> właściwości.<br /><br /> Można pobrać wystąpienia tej klasy przy użyciu `static` <xref:System.Web.Security.Membership.Provider%2A?displayProperty=nameWithType> właściwości.|  
|<xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider>|Ta klasa zarządza uwierzytelniania systemu Windows.<br /><br /> Podstawowym powodem bezpośredni dostęp do tej klasy jest wywołać jej <xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider.Logout%2A> metody. Po wylogowania użytkownik nadal będzie można uwierzytelnić dla systemu Windows, ale nie będzie można uzyskać dostępu do usług aplikacji zdalnej.<br /><br /> Można pobrać wystąpienia tej klasy przy użyciu `static` <xref:System.Web.Security.Membership.Provider%2A?displayProperty=nameWithType> właściwości.|  
|<xref:System.Web.ClientServices.Providers.ClientRoleProvider>|Ta klasa zarządza dostępem do usługi ról zdalnego.<br /><br /> Podstawowym powodem uzyskiwanie dostępu do tej klasy jest wywołać jej <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> metody. Może to być przydatne, jeśli aplikacja jest skonfigurowana do używania wartość limitu czasu pamięci podręcznej usługi roli inną niż zero. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie usługi aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md). Można również ustawić lokalizacji usługi programowo przy użyciu <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ServiceUri%2A> właściwości.<br /><br /> Można pobrać wystąpienia tej klasy przy użyciu `static` <xref:System.Web.Security.Roles.Provider%2A?displayProperty=nameWithType> właściwości.|  
|<xref:System.Web.ClientServices.Providers.ClientSettingsProvider>|Ta klasa zarządza dostępem do zdalnej usługi ustawień sieci Web.<br /><br /> Podstawowym powodem uzyskiwanie dostępu do tej klasy jest obsługa <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> zdarzeń. Można również ustawić lokalizacji usługi programowo przy użyciu <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.ServiceUri%2A> właściwości.|  
|<xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>|Ten interfejs umożliwia pośrednie dla aplikacji można uzyskać poświadczeń użytkownika do weryfikacji, zgodnie z wcześniejszym opisem w sekcji uwierzytelniania w tym temacie. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie usługi aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).|  
|<xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs>|Ta klasa udostępnia <xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs.FailedSettingsList%2A> właściwości do użycia w ramach <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved?displayProperty=nameWithType> programu obsługi zdarzeń.|  
|<xref:System.Web.ClientServices.Providers.UserValidatedEventArgs>|Ta klasa udostępnia <xref:System.Web.ClientServices.Providers.UserValidatedEventArgs.UserName%2A> właściwości do użycia w ramach <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.UserValidated> programu obsługi zdarzeń.|  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi aplikacji klienta](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [Porady: Konfigurowanie usług aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [Porady: Implementowanie logowania użytkownika z usługi aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 [Wskazówki: Korzystanie z usługi aplikacji klienta](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [Przegląd ustawień aplikacji](../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [Przegląd usług aplikacji ASP.NET](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [Korzystanie z uwierzytelniania formularzy z Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [Przy użyciu ról informacji o Microsoft Ajax](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [Przy użyciu informacji o profilu z Microsoft Ajax](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [Uwierzytelnianie ASP.NET](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 [Zarządzanie autoryzację za pomocą ról](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)  
 [Tworzenie i Konfigurowanie bazy danych usług aplikacji dla programu SQL Server](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)
