---
title: Delegowanie i personifikacja za pomocą programu WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- impersonation [WCF]
- delegation [WCF]
ms.assetid: 110e60f7-5b03-4b69-b667-31721b8e3152
caps.latest.revision: 40
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5c1acfdfdbac2660fd4de7ec391c94b39890f669
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="delegation-and-impersonation-with-wcf"></a>Delegowanie i personifikacja za pomocą programu WCF
*Personifikacja* to technika wspólnego, która usługi umożliwia ograniczenie dostępu klienta do domeny usługi zasobów. Zasoby domeny usługi może być maszyny zasoby, takie jak pliki lokalne (Personifikacja) lub zasobów na innym komputerze, na przykład do udziału plików (delegowanie uprawnień). Przykładową aplikację, zobacz [Personifikowanie klienta](../../../../docs/framework/wcf/samples/impersonating-the-client.md). Na przykład sposobu użycia personifikacji zobacz [porady: personifikowania klienta w usłudze](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md).  
  
> [!IMPORTANT]
>  Należy pamiętać, że w przypadku personifikowania klienta w usłudze, jest uruchomiona usługa przy użyciu poświadczeń klienta, które mogą mieć uprawnienia wyższe niż proces serwera.  
  
## <a name="overview"></a>Omówienie  
 Zazwyczaj klientów wywołanie usługi, aby usługa wykonanie akcji w imieniu klienta. Personifikacja umożliwia usłudze działać jako klient podczas wykonywania akcji. Delegowanie umożliwia usługa frontonu przesłać żądanie klienta do usługi zaplecza w taki sposób, że usługi zaplecza może również personifikować klienta. Personifikacja jest najczęściej używana jako sposób sprawdzania, czy klient jest autoryzowany do wykonania określonej akcji, gdy Delegowanie jest sposób przechodzenia możliwości personifikacji, wraz z tożsamości klienta do usługi zaplecza. Delegowanie jest funkcją domeny systemu Windows, która może być używana podczas uwierzytelniania Kerberos jest wykonywane. Delegowanie różni się od przepływu tożsamości i delegowania przenosi możliwość personifikacji klienta bez posiadania hasła użytkownika, dlatego jest znacznie wyższa uprzywilejowana operacja niż przepływu tożsamości.  
  
 Zarówno personifikacji, jak i delegowanie wymagają, że klient ma tożsamość systemu Windows. Jeśli klient nie posiada tożsamości systemu Windows, jedyną dostępną opcją jest przepływu tożsamości klienta do usługi drugiego.  
  
## <a name="impersonation-basics"></a>Podstawowe informacje o personifikacji  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] obsługuje personifikacji dla różnych poświadczeń klienta. W tym temacie opisano obsługę modelu usługi personifikacji wywołującego podczas wykonania metody usługi. Omówiono także są typowych scenariuszy wdrożeń obejmujących personifikacji i zabezpieczeniach SOAP i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] opcje w tych scenariuszach.  
  
 Ten temat koncentruje się na personifikację i delegowanie w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podczas korzystania z zabezpieczeń protokołu SOAP. Można również użyć personifikacji i delegowanie z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podczas za pomocą zabezpieczeń transportu, zgodnie z opisem w [przy użyciu personifikacji z zabezpieczeniami transportu](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md).  
  
## <a name="two-methods"></a>Dwie metody  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Zabezpieczenia protokołu SOAP ma dwie różne metody wykonywania personifikacji. Używana metoda zależy od powiązania. Jedna jest personifikacji z uzyskane z uwierzytelniania interfejsu dostawcy obsługi zabezpieczeń (SSPI) lub protokołu Kerberos, które następnie są buforowane na usługi tokenu systemu Windows. Drugim jest personifikacji z tokenu Windows uzyskane z rozszerzenia protokołu Kerberos, nazywane *Service for User* (S4U).  
  
### <a name="cached-token-impersonation"></a>Token personifikacji w pamięci podręcznej  
 Można wykonywać w pamięci podręcznej tokenu personifikacji z następujących czynności:  
  
-   <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>, i <xref:System.ServiceModel.NetTcpBinding> z poświadczeń klienta Windows.  
  
-   <xref:System.ServiceModel.BasicHttpBinding> z <xref:System.ServiceModel.BasicHttpSecurityMode> ustawioną <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> poświadczeń lub inne Powiązanie standardowe, gdy klient przedstawia poświadczenie nazwy użytkownika, który usługi można mapować na prawidłowe konto systemu Windows.  
  
-   Wszelkie <xref:System.ServiceModel.Channels.CustomBinding> korzystającą z poświadczeń klienta Windows `requireCancellation` ustawioną `true`. (Właściwość jest dostępna w następujących klas: <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>, <xref:System.ServiceModel.Security.Tokens.SslSecurityTokenParameters>, i <xref:System.ServiceModel.Security.Tokens.SspiSecurityTokenParameters>.) Użycie bezpiecznej konwersacji w powiązaniu musi mieć również `requireCancellation` ustawioną właściwość `true`.  
  
-   Wszelkie <xref:System.ServiceModel.Channels.CustomBinding> gdzie klient przedstawia poświadczenie nazwy użytkownika. Użycie bezpiecznej konwersacji w powiązaniu musi mieć również `requireCancellation` ustawioną właściwość `true`.  
  
### <a name="s4u-based-impersonation"></a>Na podstawie S4U personifikacji  
 Można wykonywać na podstawie S4U personifikacji z następujących czynności:  
  
-   <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>, i <xref:System.ServiceModel.NetTcpBinding> z poświadczeniami klienta certyfikatu, które usługi można mapować na prawidłowe konto systemu Windows.  
  
-   Wszelkie <xref:System.ServiceModel.Channels.CustomBinding> korzystającą z poświadczeń klienta Windows `requireCancellation` ustawioną właściwość `false`.  
  
-   Wszelkie <xref:System.ServiceModel.Channels.CustomBinding> używającą nazwę użytkownika lub poświadczeń klienta Windows i bezpiecznej konwersacji z `requireCancellation` ustawioną właściwość `false`.  
  
 Zakres, z którym usługa może personifikować klienta zależy od uprawnień, który przechowuje konto usługi podczas prób personifikacji, typ personifikacji używane i prawdopodobnie zakres personifikacji, który pozwala na kliencie.  
  
> [!NOTE]
>  Gdy klient i usługa są uruchomione na tym samym komputerze i na kliencie jest uruchomiony na koncie systemu (na przykład `Local System` lub `Network Service`), nie można spersonifikować klienta podczas bezpiecznej sesji jest nawiązywane z kontekstu zabezpieczeń stanową tokeny. Aplikacji formularzy systemu Windows lub konsoli zazwyczaj wykonuje w ramach konta aktualnie zalogowanego, dzięki czemu mogą być personifikowani konto domyślne. Jednakże, gdy klient jest [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] i tej strony znajduje się w [!INCLUDE[iis601](../../../../includes/iis601-md.md)] lub [!INCLUDE[iisver](../../../../includes/iisver-md.md)], a następnie klient jest uruchamiany w `Network Service` konto domyślne. Domyślnie wszystkie powiązania dostarczane przez system, które obsługują bezpiecznej sesji używają token kontekstu zabezpieczeń bezstanowej (SCT). Jednak jeśli klient jest [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] strony i bezpieczne sesje z stanowe SCTs są używane, nie można spersonifikować klienta. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] w ramach bezpiecznej sesji przy użyciu SCTs stanowe, zobacz [porady: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
## <a name="impersonation-in-a-service-method-declarative-model"></a>Personifikacja w metodzie usługi: deklaratywne modelu  
 Większość scenariuszy personifikacji obejmują wykonanie metody usługi w kontekście obiektu wywołującego. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oferuje funkcję personifikacji, która ułatwia to zrobić, dzięki czemu użytkownik określić wymaganie personifikacji w <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutu. Na przykład w poniższym kodzie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury personifikuje wywołującego przed wykonaniem `Hello` metody. Próby dostępu do zasobów natywnych wewnątrz `Hello` metody powiedzie się tylko wtedy, gdy obiekt wywołujący umożliwia listy kontroli dostępu (ACL) zasobu poziomy dostępu. Aby włączyć personifikacji, ustaw <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> jedną z właściwości <xref:System.ServiceModel.ImpersonationOption> wartości wyliczenia, albo <xref:System.ServiceModel.ImpersonationOption.Required?displayProperty=nameWithType> lub <xref:System.ServiceModel.ImpersonationOption.Allowed?displayProperty=nameWithType>, jak pokazano w poniższym przykładzie.  
  
> [!NOTE]
>  Gdy usługi ma poświadczenia wyższe niż w przypadku klienta zdalnego, używane są poświadczenia usługi, jeśli <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> właściwość jest ustawiona na <xref:System.ServiceModel.ImpersonationOption.Allowed>. Oznacza to jeśli użytkownik niskich uprawnieniach udostępnia swoje poświadczenia, usługa niskimi uprawnieniami wykonuje metodę przy użyciu poświadczeń usługi i mogą używać zasobów z niskim poziomem uprawnień użytkownika w przeciwnym razie nie będzie mógł używać.  
  
 [!code-csharp[c_ImpersonationAndDelegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#1)]
 [!code-vb[c_ImpersonationAndDelegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#1)]  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Infrastruktury można personifikują wywołującego tylko wtedy, gdy obiekt wywołujący jest uwierzytelniany przy użyciu poświadczeń, które mogą być mapowane na konto użytkownika systemu Windows. Jeśli usługa jest skonfigurowana do uwierzytelniania przy użyciu poświadczeń, które nie mogą być mapowane na konta systemu Windows, metody usługi nie została wykonana.  
  
> [!NOTE]
>  Na [!INCLUDE[wxp](../../../../includes/wxp-md.md)], personifikacja nie powiedzie się, jeśli stanowego SCT jest tworzony, co powoduje <xref:System.InvalidOperationException>. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="impersonation-in-a-service-method-imperative-model"></a>Personifikacja w metodzie usługi: Model Imperatywne  
 Czasami obiekt wywołujący nie musi personifikować metody całej usługi, funkcji, ale tylko części z nich. W takim przypadku uzyskiwania tożsamości wywołującego wewnątrz metody usługi systemu Windows i imperatively wykonania personifikacji. To zrobić przy użyciu <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwość <xref:System.ServiceModel.ServiceSecurityContext> do zwrócenia wystąpienia klasy <xref:System.Security.Principal.WindowsIdentity> klasy i wywoływania <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metody, aby można było używać wystąpienia.  
  
> [!NOTE]
>  Należy użyć programu Visual Basic`Using` instrukcji lub C# `using` instrukcji, aby automatycznie przywrócić personifikacji akcji. Jeśli nie należy używać instrukcji lub jeśli używasz języka programowania innego niż Visual Basic lub C#, należy przywrócić poziom personifikacji. Błąd w tym celu może stanowić podstawę dla odmowa usługi i atakom powodującym podniesienie uprawnień.  
  
 [!code-csharp[c_ImpersonationAndDelegation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#2)]
 [!code-vb[c_ImpersonationAndDelegation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#2)]  
  
## <a name="impersonation-for-all-service-methods"></a>Personifikacji dla wszystkich metod usługi  
 W niektórych przypadkach należy wykonać wszystkie metody usługi w kontekście obiektu wywołującego. Zamiast jawnie włączenie tej funkcji na podstawie-method, użyj <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Jak pokazano w poniższym kodzie, ustaw <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A> właściwości `true`. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Są pobierane z kolekcji zachowań <xref:System.ServiceModel.ServiceHost> klasy. Należy również zauważyć, że `Impersonation` właściwość <xref:System.ServiceModel.OperationBehaviorAttribute> zastosowane do każdej metody musi także być ustawiona jako <xref:System.ServiceModel.ImpersonationOption.Allowed> lub <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
 [!code-csharp[c_ImpersonationAndDelegation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#3)]
 [!code-vb[c_ImpersonationAndDelegation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#3)]  
  
 W poniższej tabeli opisano [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zachowanie dla wszystkich możliwych kombinacji `ImpersonationOption` i `ImpersonateCallerForAllServiceOperations`.  
  
|`ImpersonationOption`|`ImpersonateCallerForAllServiceOperations`|Zachowanie|  
|---------------------------|------------------------------------------------|--------------|  
|Wymagane|n/d|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] personifikuje wywołującego|  
|Dozwolone|false|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie personifikują wywołującego|  
|Dozwolone|true|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] personifikuje wywołującego|  
|NotAllowed|false|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie personifikują wywołującego|  
|NotAllowed|true|Niedozwolone. ( <xref:System.InvalidOperationException> Jest generowany.)|  
  
## <a name="impersonation-level-obtained-from-windows-credentials-and-cached-token-impersonation"></a>Poziom personifikacji uzyskane z poświadczeń systemu Windows i tokenu personifikacji w pamięci podręcznej  
 W niektórych scenariuszach klient ma kontrolę nad poziomem personifikacji, który usługa wykonuje stosowania poświadczeń klienta Windows. Jednym ze scenariuszy występuje, gdy klient określa poziom personifikacji anonimowy. Druga występuje podczas wykonywania personifikacji z pamięci podręcznej tokenu. Odbywa się przez ustawienie <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> właściwość <xref:System.ServiceModel.Security.WindowsClientCredential> klasy, która jest dostępna jako właściwość ogólnego <xref:System.ServiceModel.ChannelFactory%601> klasy.  
  
> [!NOTE]
>  Określanie poziom personifikacji anonimowe powoduje, że klient anonimowego logowania się do usługi. Usługi w związku z tym muszą zezwalać na logowania anonimowego, niezależnie od tego, czy personifikacja jest wykonywana.  
  
 Klient może określić poziom personifikacji jako <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, lub <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Jest generowany tylko token na określonym poziomie, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_ImpersonationAndDelegation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#4)]
 [!code-vb[c_ImpersonationAndDelegation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#4)]  
  
 Poniższa tabela zawiera poziom personifikacji, który uzyskuje usługi podczas personifikacji z pamięci podręcznej tokenu.  
  
|`AllowedImpersonationLevel` Wartość|Usługa ma `SeImpersonatePrivilege`|Usługi i klienta są w stanie delegowania|Buforowany token `ImpersonationLevel`|  
|---------------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Anonimowe|Tak|n/d|Personifikacja|  
|Anonimowe|Nie|n/d|Identyfikacja|  
|Identyfikacja|n/d|n/d|Identyfikacja|  
|Personifikacja|Tak|n/d|Personifikacja|  
|Personifikacja|Nie|n/d|Identyfikacja|  
|Delegowanie|Tak|Tak|Delegowanie|  
|Delegowanie|Tak|Nie|Personifikacja|  
|Delegowanie|Nie|n/d|Identyfikacja|  
  
## <a name="impersonation-level-obtained-from-user-name-credentials-and-cached-token-impersonation"></a>Poziom personifikacji uzyskane z poświadczeń nazwy użytkownika i tokenu personifikacji w pamięci podręcznej  
 Przekazując usługi swoją nazwę użytkownika i hasło, umożliwia klientowi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Zaloguj się jako ten użytkownik, który jest odpowiednikiem ustawienia `AllowedImpersonationLevel` właściwości <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. ( `AllowedImpersonationLevel` Jest dostępna w <xref:System.ServiceModel.Security.WindowsClientCredential> i <xref:System.ServiceModel.Security.HttpDigestClientCredential> klasy.) W poniższej tabeli przedstawiono personifikacji poziomu uzyskane gdy usługa odbiera poświadczenia nazwy użytkownika.  
  
|`AllowedImpersonationLevel`|Usługa ma `SeImpersonatePrivilege`|Usługi i klienta są w stanie delegowania|Buforowany token `ImpersonationLevel`|  
|---------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|n/d|Tak|Tak|Delegowanie|  
|n/d|Tak|Nie|Personifikacja|  
|n/d|Nie|n/d|Identyfikacja|  
  
## <a name="impersonation-level-obtained-from-s4u-based-impersonation"></a>Poziom personifikacji uzyskane z systemem S4U personifikacji  
  
|Usługa ma `SeTcbPrivilege`|Usługa ma `SeImpersonatePrivilege`|Usługi i klienta są w stanie delegowania|Buforowany token `ImpersonationLevel`|  
|----------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Tak|Tak|n/d|Personifikacja|  
|Tak|Nie|n/d|Identyfikacja|  
|Nie|n/d|n/d|Identyfikacja|  
  
## <a name="mapping-a-client-certificate-to-a-windows-account"></a>Mapowanie certyfikatu klienta na konto systemu Windows  
 Istnieje możliwość dla klienta do samodzielnego uwierzytelnienia usługi przy użyciu certyfikatu i poproś go o mapy usług klienta do istniejącego konta za pośrednictwem usługi Active Directory. Następujący kod XML pokazano, jak skonfigurować usługę w celu zmapowania certyfikatu.  
  
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
 Aby delegować do usługi zaplecza, usługi, należy wykonać wieloetapowego protokołu Kerberos (SSPI bez powrotu NTLM) lub protokołu Kerberos bezpośrednio uwierzytelniania w usłudze zaplecza przy użyciu tożsamości klienta systemu Windows. Aby delegować do usługi zaplecza, Utwórz <xref:System.ServiceModel.ChannelFactory%601> i kanał, a następnie komunikować się za pośrednictwem kanału podczas personifikacji klienta. Z tego formularza delegowania odległość, na jaką można zlokalizować usługi frontonu usługi zaplecza zależy od poziomu personifikacji osiągnięte przez usługi frontonu. Gdy jest poziom personifikacji <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, usługi frontonu i zaplecza, musi być uruchomiona na tym samym komputerze. Gdy jest poziom personifikacji <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, usługi frontonu i zaplecza może być na oddzielnych komputerach lub na tym samym komputerze. Włączanie delegowania poziom personifikacji wymaga skonfigurowania zasad domeny systemu Windows, aby umożliwić delegowanie. Aby uzyskać więcej informacji o konfigurowaniu usługi Active Directory do obsługi delegowania, zobacz [Włączanie uwierzytelniania delegowanego](http://go.microsoft.com/fwlink/?LinkId=99690).  
  
> [!NOTE]
>  Podczas uwierzytelniania klienta do usługi frontonu przy użyciu nazwy użytkownika i hasło, które odpowiadają konta systemu Windows w usłudze zaplecza, usługi frontonu można uwierzytelniać na podstawie nazwy użytkownika i hasła klienta do usługi zaplecza. Jest to szczególnie wydajna formę przepływu tożsamości, ponieważ przekazywanie nazwę użytkownika i hasło do usługi zaplecza umożliwia usługi zaplecza do wykonania personifikacji, ale go nie stanowi delegowania, ponieważ nie jest używany protokół Kerberos. Active Directory kontrole delegowania nie dotyczą uwierzytelnianie nazwy i hasła użytkownika.  
  
### <a name="delegation-ability-as-a-function-of-impersonation-level"></a>Możliwość delegowania funkcji poziom personifikacji  
  
|Poziom personifikacji|Usługa może wykonywać delegowanie między procesami|Usługa może wykonywać delegowanie między komputerami|  
|-------------------------|---------------------------------------------------|---------------------------------------------------|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Identification>|Nie|Nie|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>|Tak|Nie|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Delegation>|Tak|Tak|  
  
 Poniższy przykład kodu pokazuje, jak używać delegowania.  
  
 [!code-csharp[c_delegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_delegation/cs/source.cs#1)]
 [!code-vb[c_delegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_delegation/vb/source.vb#1)]  
  
### <a name="how-to-configure-an-application-to-use-constrained-delegation"></a>Jak skonfigurować aplikację do korzystania z delegowania ograniczonego  
 Zanim będzie można Użyj ograniczonego delegowania, nadawcy, odbiorcy, a kontroler domeny musi być skonfigurowany tak, aby to zrobić. W poniższej procedurze wyszczególniono czynności, które umożliwiają ograniczone delegowanie. Aby uzyskać więcej informacji o różnicach między delegowania i ograniczonego delegowania, zobacz część [systemu Windows Server 2003 Kerberos rozszerzenia](http://go.microsoft.com/fwlink/?LinkId=100194) przedstawiono omówienie ograniczonego.  
  
1.  Na kontrolerze domeny, wyczyść **konto jest poufne i nie może być delegowane** pole wyboru dla konta, na którym działa aplikacja kliencka.  
  
2.  Na kontrolerze domeny, wybierz **konto jest zaufany dla celów delegacji** pole wyboru dla konta, na którym działa aplikacja kliencka.  
  
3.  Na kontrolerze domeny, skonfiguruj komputer warstwy środkowej, dzięki czemu jest zaufany dla celów delegacji, klikając **zaufania komputerowi w delegowaniu** opcji.  
  
4.  Na kontrolerze domeny, należy skonfigurować komputer warstwy środkowej, aby używały ograniczonego delegowania, klikając **Ufaj temu komputerowi w delegowaniu tylko do określonych usług** opcji.  
  
 Aby uzyskać bardziej szczegółowe instrukcje dotyczące konfigurowania ograniczonego delegowania zobacz następujące tematy w witrynie MSDN:  
  
-   [Rozwiązywanie problemów z delegowania protokołu Kerberos](http://go.microsoft.com/fwlink/?LinkId=36724)  
  
-   [Protokół Kerberos przejścia i ograniczone delegowanie](http://go.microsoft.com/fwlink/?LinkId=36725)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.OperationBehaviorAttribute>  
 <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>  
 <xref:System.ServiceModel.ImpersonationOption>  
 <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>  
 <xref:System.ServiceModel.ServiceSecurityContext>  
 <xref:System.Security.Principal.WindowsIdentity>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 <xref:System.ServiceModel.ChannelFactory%601>  
 <xref:System.Security.Principal.TokenImpersonationLevel.Identification>  
 [Korzystanie z personifikacji z zabezpieczeniami transportu](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)  
 [Personifikowanie klienta](../../../../docs/framework/wcf/samples/impersonating-the-client.md)  
 [Instrukcje: personifikowanie klienta w usłudze](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)  
 [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
