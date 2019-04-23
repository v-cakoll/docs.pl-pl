---
title: Delegowanie i personifikacja za pomocą programu WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- impersonation [WCF]
- delegation [WCF]
ms.assetid: 110e60f7-5b03-4b69-b667-31721b8e3152
ms.openlocfilehash: ec34c19da9cd642f5de51166bef0264c2e75c58c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345524"
---
# <a name="delegation-and-impersonation-with-wcf"></a>Delegowanie i personifikacja za pomocą programu WCF
*Personifikacja* jest typową techniką, której usługi użyć do ograniczenia dostępu klienta do zasobów w domenie usługi. Zasobów domeny usługi może być zasoby maszyny, takie jak pliki lokalne (dokona personifikacji) lub zasobów na innej maszynie, na przykład do udziału plików (delegowania). Dla przykładowej aplikacji, zobacz [Personifikowanie klienta](../../../../docs/framework/wcf/samples/impersonating-the-client.md). Na przykład jak używać personifikacji zobacz [jak: Personifikowanie klienta w usłudze](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md).  
  
> [!IMPORTANT]
>  Należy pamiętać podczas personifikowania klienta w usłudze, usługa była uruchamiana przy użyciu poświadczeń klienta, które mogą mieć wyższe uprawnienia niż aktualnie proces serwera.  
  
## <a name="overview"></a>Omówienie  
 Zazwyczaj klienci wywołują usługi, aby usługa wykonanie akcji w imieniu klienta. Personifikacja umożliwia usługa do działania jako klienta podczas wykonywania akcji. Delegowanie umożliwia usłudze frontonu przesyła żądanie klienta do usługi zaplecza w taki sposób, że usługa zaplecza może również personifikować klienta. Personifikacja jest najczęściej używana jako sposób sprawdzania, czy klient jest autoryzowany do wykonania określonej akcji, gdy delegowanie to sposób możliwości płynące personifikacji, wraz z tożsamość klienta usługi zaplecza. Delegowanie jest funkcją domeny Windows, które mogą być używane podczas uwierzytelniania Kerberos jest wykonywane. Delegowanie różni się od przepływ tożsamości, a ponieważ delegowania transferów możliwość personifikacji klienta bez posiadania hasła użytkownika, jest znacznie wyższa uprzywilejowaną operacją niż przepływ tożsamości.  
  
 Delegowanie i personifikacja wymaga się, że klient ma tożsamości Windows. Jeśli klient nie posiada tożsamości Windows, jedyną dostępną opcją jest tożsamość klienta do drugiego usługi flow.  
  
## <a name="impersonation-basics"></a>Podstawowe informacje o personifikacji  
 Windows Communication Foundation (WCF) obsługuje personifikacji dla różnych poświadczeń klienta. W tym temacie opisano obsługę modelu usługi personifikacji wywołującego podczas implementacji metody usługi. Omówiono także typowe scenariusze wdrożenia obejmujące personifikacji i zabezpieczeniach SOAP oraz opcje usługi WCF w tych scenariuszach.  
  
 Ten temat koncentruje się na personifikacji i delegowanie w programie WCF, korzystając z zabezpieczeń protokołu SOAP. Umożliwia także personifikacji i delegowanie z programem WCF podczas za pomocą zabezpieczeń transportu, zgodnie z opisem w [przy użyciu personifikacji z zabezpieczeniami transportu](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md).  
  
## <a name="two-methods"></a>Dwie metody  
 WCF SOAP zabezpieczeń ma dwa różne metody służące do wykonywania personifikacji. Metoda używana zależy od powiązania. Jeden jest personifikacji z tokenu Windows uzyskany z uwierzytelniania interfejsu dostawcy obsługi zabezpieczeń (SSPI) i Kerberos, które są zapisane w pamięci podręcznej w usłudze. Drugi to personifikacji z tokenem Windows uzyskany z rozszerzenia protokołu Kerberos, nazywane *Service for User* (S4U).  
  
### <a name="cached-token-impersonation"></a>Buforowany Token personifikacji  
 Możesz wykonać pamięci podręcznej tokenu personifikacji z następujących czynności:  
  
-   <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>, i <xref:System.ServiceModel.NetTcpBinding> przy użyciu poświadczeń klienta Windows.  
  
-   <xref:System.ServiceModel.BasicHttpBinding> za pomocą <xref:System.ServiceModel.BasicHttpSecurityMode> równa <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> poświadczenia lub innych Powiązanie standardowe, gdzie klient przedstawia poświadczenie nazwy użytkownika, że usługa może mapować do prawidłowego konta Windows.  
  
-   Wszelkie <xref:System.ServiceModel.Channels.CustomBinding> , który używa poświadczeń klienta Windows za pomocą `requireCancellation` równa `true`. (Właściwość jest dostępna w następujących klas: <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>, <xref:System.ServiceModel.Security.Tokens.SslSecurityTokenParameters>, i <xref:System.ServiceModel.Security.Tokens.SspiSecurityTokenParameters>.) Jeśli bezpiecznej konwersacji jest używany w wiązaniu, musi mieć również `requireCancellation` właściwością `true`.  
  
-   Wszelkie <xref:System.ServiceModel.Channels.CustomBinding> gdzie klient przedstawia poświadczenie nazwy użytkownika. Jeśli bezpiecznej konwersacji jest używany w wiązaniu, musi mieć również `requireCancellation` właściwością `true`.  
  
### <a name="s4u-based-impersonation"></a>Na podstawie S4U personifikacji  
 Można wykonywać na podstawie S4U personifikacji z następujących czynności:  
  
-   <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>, i <xref:System.ServiceModel.NetTcpBinding> przy użyciu poświadczeń klienta certyfikatu, który usługi można mapować do prawidłowego konta Windows.  
  
-   Wszelkie <xref:System.ServiceModel.Channels.CustomBinding> , który używa poświadczeń klienta Windows za pomocą `requireCancellation` właściwością `false`.  
  
-   Wszelkie <xref:System.ServiceModel.Channels.CustomBinding> które używa nazwy użytkownika lub poświadczeń klienta Windows i bezpiecznej konwersacji z `requireCancellation` właściwością `false`.  
  
 Zakres, do którego usługa może personifikować klienta zależy od uprawnień, który przechowuje konto usługi, podczas prób personifikacji, typ personifikacji używane i prawdopodobnie stopnia personifikacji, który pozwala na kliencie.  
  
> [!NOTE]
>  Gdy klient i usługa są uruchomione na tym samym komputerze i klient jest uruchomiony w ramach konta system (na przykład `Local System` lub `Network Service`), nie można spersonifikować klienta, po nawiązaniu bezpiecznej sesji przy użyciu stanowych kontekstu zabezpieczeń tokeny. Formularz Windows lub konsoli aplikacji jest zazwyczaj uruchamiany przy użyciu aktualnie zalogowanego konta tak, aby konto mogą personalizacji domyślnie. Jednakże, gdy klient jest [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] strony i na tej stronie znajduje się w [!INCLUDE[iis601](../../../../includes/iis601-md.md)] lub [!INCLUDE[iisver](../../../../includes/iisver-md.md)], a następnie uruchom klienta, w obszarze `Network Service` konto domyślne. Domyślnie wszystkie powiązania dostarczane przez system, które obsługują bezpiecznej sesji używają tokenu kontekstu zabezpieczeń o bezstanowa (SCT). Jednakże jeśli klient jest [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] strony i bezpieczne sesje stanowych SCTs są używane, nie można spersonifikować klienta. Aby uzyskać więcej informacji na temat w ramach bezpiecznej sesji przy użyciu stanowych SCTs zobacz [jak: Utwórz kontekst zabezpieczeń tokenu dla bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
## <a name="impersonation-in-a-service-method-declarative-model"></a>Personifikacji w metodzie usług: Deklaratywny Model  
 Większość scenariuszy personifikacji wymagają wykonania metody usługi w kontekście obiektu wywołującego. WCF oferuje funkcję personifikacji, który sprawia, że są to proste, umożliwiając użytkownikowi na określenie wymagań personifikacji w <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutu. Na przykład, poniższy kod, infrastruktura WCF personifikuje obiekt wywołujący przed wykonaniem `Hello` metody. Dowolne próba dostępu do zasobów natywnych wewnątrz `Hello` metoda powiedzie się tylko wtedy, gdy listy kontroli dostępu (ACL) zasobu umożliwia obiektowi wywołującemu przywileje dostępu. Aby włączyć personifikacji, ustaw <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> jedną z właściwości <xref:System.ServiceModel.ImpersonationOption> wartości wyliczenia, albo <xref:System.ServiceModel.ImpersonationOption.Required?displayProperty=nameWithType> lub <xref:System.ServiceModel.ImpersonationOption.Allowed?displayProperty=nameWithType>, jak pokazano w poniższym przykładzie.  
  
> [!NOTE]
>  Gdy usługa poświadczeniami wyższe niż w przypadku zdalnego klienta, są używane poświadczenia usługi, jeśli <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> właściwość jest ustawiona na <xref:System.ServiceModel.ImpersonationOption.Allowed>. Oznacza to jeśli użytkownika o niskich uprawnieniach udostępnia swoje poświadczenia, usługa wyższych uprawnieniach wykonuje metodę przy użyciu poświadczeń usługi i mogą korzystać z niskim poziomem uprawnień użytkownika w przeciwnym razie nie będzie mógł używać zasobów.  
  
 [!code-csharp[c_ImpersonationAndDelegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#1)]
 [!code-vb[c_ImpersonationAndDelegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#1)]  
  
 Infrastruktura WCF można personifikują wywołującego, tylko wtedy, gdy obiekt wywołujący jest uwierzytelniany przy użyciu poświadczeń, które mogą zostać zamapowane na konto użytkownika Windows. Jeśli usługa jest skonfigurowana do uwierzytelniania przy użyciu poświadczeń, które nie mogą być mapowane na konta Windows, metoda usługi nie jest wykonywany.  
  
> [!NOTE]
>  Na [!INCLUDE[wxp](../../../../includes/wxp-md.md)], personifikacji zakończy się niepowodzeniem, jeśli stanowa, SCT jest tworzony z wynikiem <xref:System.InvalidOperationException>. Aby uzyskać więcej informacji, zobacz [nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="impersonation-in-a-service-method-imperative-model"></a>Personifikacji w metodzie usług: Model imperatywne  
 Czasami obiekt wywołujący nie musi dokonać personifikacji metoda całą usługę do funkcji, ale tylko jego części. W tym przypadku uzyskać tożsamość Windows obiektu wywołującego wewnątrz metody usługi i wykonywać obowiązkowo personifikacji. To zrobić za pomocą <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwość <xref:System.ServiceModel.ServiceSecurityContext> do zwrócenia wystąpienia <xref:System.Security.Principal.WindowsIdentity> klasy i wywoływania <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metoda przed rozpoczęciem korzystania z wystąpienia.  
  
> [!NOTE]
>  Należy użyć programu Visual Basic`Using` instrukcji lub C# `using` instrukcję, aby automatycznie przywrócić działanie personifikacji. Nie należy używać instrukcji lub jeśli używasz języka programowania niż Visual Basic lub C#, pamiętaj przywrócić poziom personifikacji. Niewykonanie tej czynności to może stanowić podstawę dla typu odmowa usługi i atakom powodującym podniesienie uprawnień.  
  
 [!code-csharp[c_ImpersonationAndDelegation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#2)]
 [!code-vb[c_ImpersonationAndDelegation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#2)]  
  
## <a name="impersonation-for-all-service-methods"></a>Personifikacji dla wszystkich metod usługi  
 W niektórych przypadkach należy wykonać wszystkie metody usługi w kontekście obiektu wywołującego. Zamiast jawnie włączenie tej funkcji, na podstawie na metodzie, użyj <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Jak pokazano w poniższym kodzie, ustaw <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A> właściwość `true`. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Są pobierane z kolekcji zachowań <xref:System.ServiceModel.ServiceHost> klasy. Należy również zauważyć, że `Impersonation` właściwość <xref:System.ServiceModel.OperationBehaviorAttribute> stosowane do każdej metody również musi być ustawiona na <xref:System.ServiceModel.ImpersonationOption.Allowed> lub <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
 [!code-csharp[c_ImpersonationAndDelegation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#3)]
 [!code-vb[c_ImpersonationAndDelegation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#3)]  
  
 W poniższej tabeli przedstawiono zachowania usługi WCF w przypadku wszystkich możliwych kombinacji `ImpersonationOption` i `ImpersonateCallerForAllServiceOperations`.  
  
|`ImpersonationOption`|`ImpersonateCallerForAllServiceOperations`|Zachowanie|  
|---------------------------|------------------------------------------------|--------------|  
|Wymagane|n/d|Usługi WCF personifikuje obiektu wywołującego|  
|Dozwolone|false|Usługi WCF nie spersonifikować obiektu wywołującego|  
|Dozwolone|true|Usługi WCF personifikuje obiektu wywołującego|  
|NotAllowed|false|Usługi WCF nie spersonifikować obiektu wywołującego|  
|NotAllowed|true|Niedozwolone. ( <xref:System.InvalidOperationException> Zgłaszany.)|  
  
## <a name="impersonation-level-obtained-from-windows-credentials-and-cached-token-impersonation"></a>Poziom personifikacji uzyskanych od Windows poświadczeń i pamięci podręcznej tokenu personifikacji  
 W niektórych przypadkach klient ma częściowa kontrola nad poziomem personifikacji, którego usługa wykonuje stosowania poświadczeń klienta Windows. Jeden scenariusz występuje, gdy klient określa poziom personifikacji anonimowe. Druga występuje podczas przeprowadzania personifikacja za pomocą tokenu z pamięci podręcznej. Jest to realizowane przez ustawienie <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> właściwość <xref:System.ServiceModel.Security.WindowsClientCredential> klasy, który jest dostępny jako właściwość ogólnego <xref:System.ServiceModel.ChannelFactory%601> klasy.  
  
> [!NOTE]
>  Określając poziom personifikacji anonimowe powoduje, że klient anonimowego logowania się do usługi. W związku z tym usługa muszą zezwalać na logowanie anonimowe, niezależnie od tego, czy personifikacja jest wykonywane.  
  
 Klienta można określić poziom personifikacji jako <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, lub <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Jest generowany tylko token na określonym poziomie, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_ImpersonationAndDelegation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#4)]
 [!code-vb[c_ImpersonationAndDelegation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#4)]  
  
 W poniższej tabeli określono poziom personifikacji, którego usługi uzyskuje podczas personifikacji z tokenu z pamięci podręcznej.  
  
|`AllowedImpersonationLevel` Wartość|Usługa ma `SeImpersonatePrivilege`|Usługi i klienta są w stanie delegowania|Tokenu z pamięci podręcznej `ImpersonationLevel`|  
|---------------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Anonimowe|Tak|n/d|Personifikacja|  
|Anonimowe|Nie|n/d|Identyfikacja|  
|Identyfikacja|n/d|n/d|Identyfikacja|  
|Personifikacja|Tak|n/d|Personifikacja|  
|Personifikacja|Nie|n/d|Identyfikacja|  
|Delegowanie|Tak|Tak|Delegowanie|  
|Delegowanie|Yes|Nie|Personifikacja|  
|Delegowanie|Nie|n/d|Identyfikacja|  
  
## <a name="impersonation-level-obtained-from-user-name-credentials-and-cached-token-impersonation"></a>Poziom personifikacji uzyskany z poświadczenia nazwy użytkownika i pamięci podręcznej tokenu personifikacji  
 Przekazując usługi swoją nazwę użytkownika i hasło, klienta umożliwia WCF zalogować się jako ten użytkownik, który jest odpowiednikiem ustawienia `AllowedImpersonationLevel` właściwość <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. ( `AllowedImpersonationLevel` Jest dostępny na <xref:System.ServiceModel.Security.WindowsClientCredential> i <xref:System.ServiceModel.Security.HttpDigestClientCredential> klasy.) W poniższej tabeli przedstawiono personifikacji poziom uzyskane podczas usługa odbiera poświadczenia nazwy użytkownika.  
  
|`AllowedImpersonationLevel`|Usługa ma `SeImpersonatePrivilege`|Usługi i klienta są w stanie delegowania|Tokenu z pamięci podręcznej `ImpersonationLevel`|  
|---------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|n/d|Tak|Tak|Delegowanie|  
|n/d|Tak|Nie|Personifikacja|  
|n/d|Nie|n/d|Identyfikacja|  
  
## <a name="impersonation-level-obtained-from-s4u-based-impersonation"></a>Poziom personifikacji uzyskany z systemem S4U personifikacji  
  
|Usługa ma `SeTcbPrivilege`|Usługa ma `SeImpersonatePrivilege`|Usługi i klienta są w stanie delegowania|Tokenu z pamięci podręcznej `ImpersonationLevel`|  
|----------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Tak|Tak|n/d|Personifikacja|  
|Tak|Nie|n/d|Identyfikacja|  
|Nie|n/d|n/d|Identyfikacja|  
  
## <a name="mapping-a-client-certificate-to-a-windows-account"></a>Mapowanie certyfikatu klienta na konto Windows  
 Istnieje możliwość dla klienta do samodzielnego uwierzytelnienia usługi przy użyciu certyfikatu, a także mieć mapy usługi klienta do istniejącego konta za pośrednictwem usługi Active Directory. Następujący kody XML pokazuje sposób konfigurowania usługi do mapowania certyfikatu.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="MapToWindowsAccount">  
      <serviceCredentials>  
        <clientCertificate>  
          <authentication mapClientCertificateToWindowsAccount="true" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Poniższy kod przedstawia sposób konfigurowania usługi.  
  
```  
// Create a binding that sets a certificate as the client credential type.  
WSHttpBinding b = new WSHttpBinding();  
b.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a service host that maps the certificate to a Windows account.  
Uri httpUri = new Uri("http://localhost/Calculator");  
ServiceHost sh = new ServiceHost(typeof(HelloService), httpUri);  
sh.Credentials.ClientCertificate.Authentication.MapClientCertificateToWindowsAccount = true;  
```  
  
## <a name="delegation"></a>Delegowanie  
 Aby delegować do usługi zaplecza, usługi, należy wykonać Kerberos wielu gałęzi (SSPI bez rezerwowego protokołu NTLM) lub Kerberos bezpośrednie uwierzytelnianie w usłudze zaplecza przy użyciu klienta programu Windows identity. Aby delegować do usługi zaplecza, należy utworzyć <xref:System.ServiceModel.ChannelFactory%601> i kanał, a następnie komunikować się za pośrednictwem kanału podczas personifikacji klienta. Przy użyciu tej formy delegowania odległość, na którym usługa zaplecza można znaleźć usługi frontonu zależy od poziomu personifikacji osiągnięte przez usługi frontonu. Gdy jest poziom personifikacji <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, usługi frontonu i zaplecza, musi być uruchomiona na tym samym komputerze. Gdy jest poziom personifikacji <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, usługi frontonu i zaplecza mogą być na oddzielnych komputerach lub na tym samym komputerze. Włączanie delegowania poziom personifikacji wymaga skonfigurowania zasad domeny Windows Aby umożliwić delegowanie. Aby uzyskać więcej informacji o konfigurowaniu usługi Active Directory do obsługi delegowania, zobacz [Włączanie uwierzytelniania delegowanego](https://go.microsoft.com/fwlink/?LinkId=99690).  
  
> [!NOTE]
>  Klient uwierzytelnia się do usługi frontonu przy użyciu nazwy użytkownika i hasło, które odnoszą się do konta Windows w usłudze zaplecza, usługi frontonu mogą uwierzytelniać w usłudze zaplecza na podstawie nazwy użytkownika i hasła klienta. Jest to szczególnie wydajna formą przepływu tożsamości, ponieważ przekazanie nazwy użytkownika i hasła do usługi zaplecza włącza usługę zaplecza w celu wykonania personifikacji, ale go nie stanowi delegowanie, ponieważ nie jest używany protokół Kerberos. Active Directory kontrole delegowanie nie dotyczą użytkownika nazwy i hasła uwierzytelniania.  
  
### <a name="delegation-ability-as-a-function-of-impersonation-level"></a>Możliwość delegowania w zależności od poziomu personifikacji  
  
|Poziom personifikacji|Usługa może wykonywać delegowanie między procesami|Usługa może wykonywać delegowanie między komputerami|  
|-------------------------|---------------------------------------------------|---------------------------------------------------|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Identification>|Nie|Nie|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>|Yes|Nie|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Delegation>|Yes|Tak|  
  
 Poniższy przykład kodu pokazuje, jak używać delegowania.  
  
 [!code-csharp[c_delegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_delegation/cs/source.cs#1)]
 [!code-vb[c_delegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_delegation/vb/source.vb#1)]  
  
### <a name="how-to-configure-an-application-to-use-constrained-delegation"></a>Jak skonfigurować aplikację do korzystania z delegowania ograniczonego  
 Zanim będzie można Użyj ograniczonego delegowania, nadawca, odbiorca, a kontroler domeny musi być skonfigurowany tak, aby to zrobić. W poniższej procedurze wyszczególniono czynności, które włączyć ograniczone delegowanie. Aby uzyskać szczegółowe informacje o różnicach między delegowanie i ograniczonego delegowania, zobacz część [systemu Windows Server 2003 Kerberos Extensions](https://go.microsoft.com/fwlink/?LinkId=100194) , w tym artykule omówiono ograniczone dyskusji.  
  
1. Na kontrolerze domeny, należy wyczyścić **konto jest poufne i nie może być delegowane** pole wyboru dla konta, w którym aplikacja kliencka jest uruchomiona.  
  
2. Na kontrolerze domeny, wybierz **konto jest zaufany dla celów delegacji** pole wyboru dla konta, w którym aplikacja kliencka jest uruchomiona.  
  
3. Na kontrolerze domeny, skonfiguruj komputer tak, warstwy środkowej, tak aby jest zaufany dla celów delegacji, klikając **zaufania komputerowi w delegowaniu** opcji.  
  
4. Na kontrolerze domeny, skonfiguruj komputer tak warstwy środkowej w taki sposób, aby używały ograniczonego delegowania, klikając **Ufaj temu komputerowi w delegowaniu tylko do określonych usług** opcji.  
  
 Aby uzyskać bardziej szczegółowe instrukcje na temat konfigurowania ograniczonego delegowania zobacz następujące tematy w witrynie MSDN:  
  
-   [Rozwiązywanie problemów z delegowania protokołu Kerberos](https://go.microsoft.com/fwlink/?LinkId=36724)  
  
-   [Protokół Kerberos przejścia i ograniczone delegowanie](https://go.microsoft.com/fwlink/?LinkId=36725)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.OperationBehaviorAttribute>
- <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>
- <xref:System.ServiceModel.ImpersonationOption>
- <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>
- <xref:System.ServiceModel.ServiceSecurityContext>
- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ChannelFactory%601>
- <xref:System.Security.Principal.TokenImpersonationLevel.Identification>
- [Korzystanie z personifikacji z zabezpieczeniami transportu](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)
- [Personifikowanie klienta](../../../../docs/framework/wcf/samples/impersonating-the-client.md)
- [Instrukcje: Personifikowanie klienta w usłudze](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)
- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
