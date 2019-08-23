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
ms.openlocfilehash: 6e79346a448012255020cc28b6534e734980b1db
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968850"
---
# <a name="delegation-and-impersonation-with-wcf"></a>Delegowanie i personifikacja za pomocą programu WCF
*Personifikacja* jest powszechną techniką używaną przez usługi do ograniczania dostępu klientów do zasobów domeny usługi. Zasoby domeny usługi mogą być zasobami maszynowymi, takimi jak pliki lokalne (personifikacja) lub zasobami na innej maszynie, takimi jak udział plików (delegowanie). Aby uzyskać przykładową aplikację, zobacz [Personifikowanie klienta](../../../../docs/framework/wcf/samples/impersonating-the-client.md). Przykład używania personifikacji można znaleźć w temacie [How to: Personifikuj klienta w usłudze](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md).  
  
> [!IMPORTANT]
> Należy pamiętać, że podczas personifikowania klienta w usłudze Usługa jest uruchamiana przy użyciu poświadczeń klienta, które mogą mieć wyższy poziom uprawnień niż proces serwera.  
  
## <a name="overview"></a>Omówienie  
 Zazwyczaj klienci wywołują usługę, aby usługa mogła wykonać pewne działania w imieniu klienta. Personifikacja pozwala usłudze działać jako klient podczas wykonywania akcji. Delegowanie umożliwia usłudze frontonu przekazanie żądania klienta do usługi zaplecza w taki sposób, że usługa zaplecza może również personifikować klienta. Personifikacja jest najczęściej używana jako sposób sprawdzania, czy klient ma autoryzację do wykonania określonej akcji, podczas gdy Delegowanie jest sposobem przepływania możliwości personifikacji wraz z tożsamością klienta do usługi zaplecza. Delegowanie to funkcja domeny systemu Windows, która może być używana podczas uwierzytelniania opartego na protokole Kerberos. Delegowanie różni się od przepływu tożsamości i, ponieważ delegowanie przenosi możliwość personifikacji klienta bez posiadania hasła klienta, jest to znacznie wyższa uprzywilejowana operacja niż przepływ tożsamości.  
  
 Zarówno personifikacja, jak i delegowanie wymagają, aby klient miał tożsamość systemu Windows. Jeśli klient nie ma tożsamości systemu Windows, jedyną dostępną opcją jest przepływanie tożsamości klienta do drugiej usługi.  
  
## <a name="impersonation-basics"></a>Podstawy personifikacji  
 Windows Communication Foundation (WCF) obsługuje personifikację różnych poświadczeń klienta. W tym temacie opisano obsługę modelu usług na potrzeby personifikacji obiektu wywołującego podczas implementacji metody usługi. Omówione są również typowe scenariusze wdrażania dotyczące personifikacji i zabezpieczeń protokołu SOAP oraz opcji WCF w tych scenariuszach.  
  
 Ten temat koncentruje się na personifikacji i delegowaniu w programie WCF w przypadku korzystania z zabezpieczeń protokołu SOAP. W przypadku korzystania z zabezpieczeń transportu można także użyć personifikacji i delegowania w ramach usługi WCF, jak opisano w temacie [Używanie personifikacji z zabezpieczeniami transportu](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md).  
  
## <a name="two-methods"></a>Dwie metody  
 Zabezpieczenia SOAP WCF mają dwie odrębne metody wykonywania personifikacji. Używana metoda zależy od powiązania. Jeden z nich jest personifikacją od tokenu systemu Windows uzyskanego z interfejsu dostawcy obsługi zabezpieczeń (SSPI) lub uwierzytelniania Kerberos, który jest następnie buforowany w usłudze. Druga jest personifikacją od tokenu systemu Windows uzyskanego z rozszerzeń protokołu Kerberos, zbiorczo o nazwie *Service-for-User* (S4U).  
  
### <a name="cached-token-impersonation"></a>Personifikacja tokenu w pamięci podręcznej  
 Można przeprowadzić personifikację w pamięci podręcznej przy użyciu następujących czynności:  
  
- <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding> i<xref:System.ServiceModel.NetTcpBinding> z poświadczeniem klienta systemu Windows.  
  
- <xref:System.ServiceModel.BasicHttpBinding>z zestawem <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> poświadczeń lub innym powiązaniem standardowym, w którym klient przedstawia poświadczenia nazwy użytkownika, które usługa może zamapować na prawidłowe konto systemu Windows. <xref:System.ServiceModel.BasicHttpSecurityMode>  
  
- Wszystkie <xref:System.ServiceModel.Channels.CustomBinding> , które używają poświadczeń klienta systemu Windows `requireCancellation` z ustawionym `true`na. (Właściwość jest dostępna dla następujących klas: <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>, <xref:System.ServiceModel.Security.Tokens.SslSecurityTokenParameters>, i <xref:System.ServiceModel.Security.Tokens.SspiSecurityTokenParameters>.) Jeśli w powiązaniu jest używana bezpieczna Konwersacja, musi ona również mieć `requireCancellation` `true`ustawioną właściwość.  
  
- Dowolna <xref:System.ServiceModel.Channels.CustomBinding> lokalizacja, w której klient przedstawia poświadczenie nazwy użytkownika. Jeśli w powiązaniu jest używana bezpieczna Konwersacja, musi ona również mieć `requireCancellation` `true`ustawioną właściwość.  
  
### <a name="s4u-based-impersonation"></a>Personifikacja oparta na protokole S4U  
 Personifikację opartą na protokole S4U można wykonać przy użyciu następujących czynności:  
  
- <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding> i<xref:System.ServiceModel.NetTcpBinding> z poświadczenia klienta certyfikatu, które usługa może zamapować na prawidłowe konto systemu Windows.  
  
- Wszystkie <xref:System.ServiceModel.Channels.CustomBinding> , które używają poświadczeń klienta systemu Windows `requireCancellation` z właściwością ustawioną na `false`.  
  
- Każdy <xref:System.ServiceModel.Channels.CustomBinding> , który używa nazwy użytkownika lub poświadczeń klienta systemu Windows i bezpiecznej konwersacji `requireCancellation` z właściwością ustawioną na `false`.  
  
 Zakres, w jakim usługa może personifikować klienta, zależy od uprawnień, które są przechowywane w ramach konta usługi podczas próby personifikacji, rodzaju użytego personifikacji, a także zakresu personifikacji, który klient zezwala.  
  
> [!NOTE]
> Gdy klient i usługa są uruchomione na tym samym komputerze, a klient jest uruchomiony przy użyciu konta systemowego (na przykład `Local System` lub `Network Service`), nie można spersonifikować klienta w przypadku ustanowienia bezpiecznej sesji z kontekstem zabezpieczeń stanowych żeton. Aplikacja konsoli lub formularza systemu Windows jest zwykle uruchamiana w ramach aktualnie zalogowanego konta, dzięki czemu konto może być domyślnie personifikowane. Jeśli jednak klient jest stroną ASP.NET, a ta strona jest hostowana w usługach IIS 6,0 lub IIS 7,0, klient domyślnie uruchamia się w ramach `Network Service` konta. Wszystkie powiązania dostarczone przez system obsługujące bezpieczne sesje domyślnie korzystają z tokenu bezstanowego kontekstu zabezpieczeń (SCT). Jeśli jednak klient jest stroną ASP.NET i są używane bezpieczne sesje ze stanem SCTs, nie można spersonifikować klienta. Aby uzyskać więcej informacji o używaniu stanowych SCTs w bezpiecznej sesji [, zobacz How to: Utwórz token kontekstu zabezpieczeń dla bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
## <a name="impersonation-in-a-service-method-declarative-model"></a>Personifikacja w metodzie usługi: Model deklaratywny  
 Większość scenariuszy personifikacji obejmuje wykonywanie metody usługi w kontekście obiektu wywołującego. Funkcja WCF zapewnia funkcję personifikacji, która ułatwia wykonywanie tych czynności przez umożliwienie użytkownikowi określenia wymaganego personifikacji w <xref:System.ServiceModel.OperationBehaviorAttribute> atrybucie. Na przykład w poniższym kodzie Infrastruktura WCF personifikuje obiekt wywołujący przed wykonaniem `Hello` metody. Wszelkie próby uzyskania dostępu do natywnych zasobów `Hello` wewnątrz metody powiodło się tylko wtedy, gdy lista kontroli dostępu (ACL) zasobu zezwala na uprawnienia dostępu do obiektu wywołującego. Aby włączyć personifikację, ustaw <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> właściwość na jedną <xref:System.ServiceModel.ImpersonationOption> z wartości <xref:System.ServiceModel.ImpersonationOption.Required?displayProperty=nameWithType> wyliczenia lub <xref:System.ServiceModel.ImpersonationOption.Allowed?displayProperty=nameWithType>, jak pokazano w poniższym przykładzie.  
  
> [!NOTE]
> Jeśli usługa ma wyższe poświadczenia niż Klient zdalny, poświadczenia usługi są używane, jeśli <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> właściwość jest ustawiona na. <xref:System.ServiceModel.ImpersonationOption.Allowed> Oznacza to, że jeśli użytkownik z niskim poziomem uprawnień poda swoje poświadczenia, usługa wyższego uprzywilejowania wykonuje metodę z poświadczeniami usługi i może korzystać z zasobów, które nie będą mogły być używane przez użytkownika z niskim poziomem uprawnień.  
  
 [!code-csharp[c_ImpersonationAndDelegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#1)]
 [!code-vb[c_ImpersonationAndDelegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#1)]  
  
 Infrastruktura WCF może personifikować wywołującego tylko wtedy, gdy obiekt wywołujący jest uwierzytelniany przy użyciu poświadczeń, które mogą być mapowane na konto użytkownika systemu Windows. Jeśli usługa jest skonfigurowana do uwierzytelniania przy użyciu poświadczeń, których nie można zamapować na konto systemu Windows, metoda usługi nie jest wykonywana.  
  
> [!NOTE]
> W [!INCLUDE[wxp](../../../../includes/wxp-md.md)]systemie personifikacja nie powiedzie się, jeśli zostanie utworzony stanowy <xref:System.InvalidOperationException>SCT, co spowoduje wystąpienie elementu. Aby uzyskać więcej informacji, zobacz [scenariusze nieobsługiwane](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="impersonation-in-a-service-method-imperative-model"></a>Personifikacja w metodzie usługi: Model bezwzględny  
 Czasami obiekt wywołujący nie musi personifikować całej metody usługi, aby działała, ale tylko dla jego części. W takim przypadku należy uzyskać tożsamość systemu Windows wywołującego w metodzie usługi i bezwzględnie przeprowadzić personifikację. W tym celu należy użyć <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwości, <xref:System.ServiceModel.ServiceSecurityContext> aby <xref:System.Security.Principal.WindowsIdentity> zwrócić wystąpienie klasy i wywołać <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metodę przed użyciem wystąpienia.  
  
> [!NOTE]
> Należy pamiętać, aby użyć instrukcji`Using` Visual Basic lub instrukcji C# `using` , aby automatycznie przywrócić akcję personifikacji. Jeśli nie używasz instrukcji lub jeśli używasz języka programowania innego niż Visual Basic lub C#, pamiętaj o odwróceniu poziomu personifikacji. Niewykonanie tej czynności może stanowić podstawę ataku typu "odmowa usługi" i podniesienia poziomu uprawnień.  
  
 [!code-csharp[c_ImpersonationAndDelegation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#2)]
 [!code-vb[c_ImpersonationAndDelegation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#2)]  
  
## <a name="impersonation-for-all-service-methods"></a>Personifikacja dla wszystkich metod usługi  
 W niektórych przypadkach należy wykonać wszystkie metody usługi w kontekście obiektu wywołującego. Zamiast jawnie włączyć tę funkcję dla poszczególnych metod, użyj <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Jak pokazano w poniższym kodzie, ustaw <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A> właściwość na. `true` Jest pobierany z kolekcji zachowań <xref:System.ServiceModel.ServiceHost> klasy. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Należy również zauważyć, `Impersonation` że właściwość <xref:System.ServiceModel.OperationBehaviorAttribute> zastosowana do każdej metody musi również mieć ustawioną wartość <xref:System.ServiceModel.ImpersonationOption.Allowed> lub <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
 [!code-csharp[c_ImpersonationAndDelegation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#3)]
 [!code-vb[c_ImpersonationAndDelegation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#3)]  
  
 W poniższej tabeli opisano zachowanie WCF dla wszystkich możliwych kombinacji `ImpersonationOption` i. `ImpersonateCallerForAllServiceOperations`  
  
|`ImpersonationOption`|`ImpersonateCallerForAllServiceOperations`|Zachowanie|  
|---------------------------|------------------------------------------------|--------------|  
|Wymagane|n/d|Funkcja WCF personifikuje wywołującego|  
|Występować|false|Funkcja WCF nie personifikuje wywołującego|  
|Występować|true|Funkcja WCF personifikuje wywołującego|  
|NotAllowed|false|Funkcja WCF nie personifikuje wywołującego|  
|NotAllowed|true|Niedozwolone. (Zgłoszono element <xref:System.InvalidOperationException> ).|  
  
## <a name="impersonation-level-obtained-from-windows-credentials-and-cached-token-impersonation"></a>Poziom personifikacji uzyskany z poświadczeń systemu Windows i personifikacja tokenu w pamięci podręcznej  
 W niektórych scenariuszach klient ma częściową kontrolę nad poziomem personifikacji wykonywanym przez usługę podczas korzystania z poświadczeń klienta systemu Windows. Jeden scenariusz występuje, gdy klient określi poziom personifikacji anonimowej. Druga dzieje się podczas przeprowadzania personifikacji z buforowanym tokenem. Jest to realizowane przez ustawienie <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> właściwości <xref:System.ServiceModel.Security.WindowsClientCredential> klasy, która jest używana jako właściwość klasy generycznej <xref:System.ServiceModel.ChannelFactory%601> .  
  
> [!NOTE]
> Określenie poziomu personifikacji anonimowe powoduje, że klient loguje się do usługi anonimowo. W związku z tym usługa musi zezwalać na Logowanie anonimowe, niezależnie od tego, czy jest wykonywana personifikacja.  
  
 Klient może określić <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>poziom personifikacji jako, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, lub <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Tworzony jest tylko token na określonym poziomie, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_ImpersonationAndDelegation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#4)]
 [!code-vb[c_ImpersonationAndDelegation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#4)]  
  
 W poniższej tabeli określono poziom personifikacji uzyskany przez usługę podczas personifikacji z buforowanego tokenu.  
  
|`AllowedImpersonationLevel`wartościami|Usługa ma`SeImpersonatePrivilege`|Usługa i klient mogą przebudować|Token pamięci podręcznej`ImpersonationLevel`|  
|---------------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Anonimowe|Tak|n/d|Personifikacja|  
|Anonimowe|Nie|n/d|Identyfikatora|  
|Identyfikatora|n/d|n/d|Identyfikatora|  
|Personifikacja|Tak|n/d|Personifikacja|  
|Personifikacja|Nie|n/d|Identyfikatora|  
|Wierz|Tak|Tak|Wierz|  
|Wierz|Tak|Nie|Personifikacja|  
|Wierz|Nie|n/d|Identyfikatora|  
  
## <a name="impersonation-level-obtained-from-user-name-credentials-and-cached-token-impersonation"></a>Poziom personifikacji uzyskany na podstawie poświadczeń nazwy użytkownika i personifikacji tokenu w pamięci podręcznej  
 Przekazując usługę nazwę użytkownika i hasło, klient programu może zalogować się jako ten użytkownik, który jest odpowiednikiem ustawienia `AllowedImpersonationLevel` właściwości na. <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> (Jest dostępny <xref:System.ServiceModel.Security.WindowsClientCredential> w klasach i <xref:System.ServiceModel.Security.HttpDigestClientCredential> .) `AllowedImpersonationLevel` Poniższa tabela zawiera poziom personifikacji uzyskany, gdy usługa otrzymuje poświadczenia nazwy użytkownika.  
  
|`AllowedImpersonationLevel`|Usługa ma`SeImpersonatePrivilege`|Usługa i klient mogą przebudować|Token pamięci podręcznej`ImpersonationLevel`|  
|---------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|n/d|Tak|Tak|Wierz|  
|n/d|Tak|Nie|Personifikacja|  
|n/d|Nie|n/d|Identyfikatora|  
  
## <a name="impersonation-level-obtained-from-s4u-based-impersonation"></a>Poziom personifikacji uzyskany z personifikacji opartej na protokole S4U  
  
|Usługa ma`SeTcbPrivilege`|Usługa ma`SeImpersonatePrivilege`|Usługa i klient mogą przebudować|Token pamięci podręcznej`ImpersonationLevel`|  
|----------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Tak|Tak|n/d|Personifikacja|  
|Tak|Nie|n/d|Identyfikatora|  
|Nie|n/d|n/d|Identyfikatora|  
  
## <a name="mapping-a-client-certificate-to-a-windows-account"></a>Mapowanie certyfikatu klienta na konto systemu Windows  
 Klient może uwierzytelniać się w usłudze przy użyciu certyfikatu, a Usługa mapuje klienta na istniejące konto za pośrednictwem Active Directory. Poniższy kod XML przedstawia sposób konfigurowania usługi do mapowania certyfikatu.  
  
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
  
## <a name="delegation"></a>Wierz  
 Aby delegować do usługi zaplecza, usługa musi wykonać wieloetapowe uwierzytelnianie Kerberos (SSPI bez powrotu NTLM) lub Kerberos Direct do usługi zaplecza przy użyciu tożsamości systemu Windows klienta. Aby delegować do usługi zaplecza, Utwórz <xref:System.ServiceModel.ChannelFactory%601> i kanał, a następnie przekomunikuj się za pośrednictwem kanału podczas personifikacji klienta. Dzięki tej formie delegowania odległość, z jaką usługa zaplecza może znajdować się w usłudze frontonu, zależy od poziomu personifikacji osiągniętego przez usługę frontonu. Gdy poziom personifikacji to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, usługi frontonu i zaplecza muszą być uruchomione na tym samym komputerze. Gdy poziom personifikacji to <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, usługi frontonu i zaplecza mogą znajdować się na oddzielnych maszynach lub na tym samym komputerze. Włączenie personifikacji na poziomie delegowania wymaga skonfigurowania zasad domeny systemu Windows do zezwalania na delegowanie. Aby uzyskać więcej informacji o konfigurowaniu Active Directory na potrzeby obsługi delegowania, zobacz [Włączanie uwierzytelniania delegowanego](https://go.microsoft.com/fwlink/?LinkId=99690).  
  
> [!NOTE]
> Gdy klient uwierzytelnia się w usłudze frontonu przy użyciu nazwy użytkownika i hasła, które odpowiadają kontu systemu Windows w usłudze zaplecza, usługa frontonu może uwierzytelniać się w usłudze zaplecza przez ponowne użycie nazwy użytkownika i hasła klienta. Jest to szczególnie wydajna postać przepływu tożsamości, ponieważ przekazywanie nazwy użytkownika i hasła do usługi zaplecza umożliwia usłudze zaplecza wykonywanie personifikacji, ale nie stanowi delegowania, ponieważ nie jest używany protokół Kerberos. Kontrolki Active Directory w delegowaniu nie mają zastosowania do uwierzytelniania nazwy użytkownika i hasła.  
  
### <a name="delegation-ability-as-a-function-of-impersonation-level"></a>Możliwość delegowania jako funkcja poziomu personifikacji  
  
|Poziom personifikacji|Usługa może przeprowadzać delegowanie między procesami|Usługa może wykonywać delegowanie między maszynami|  
|-------------------------|---------------------------------------------------|---------------------------------------------------|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Identification>|Nie|Nie|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>|Yes|Nie|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Delegation>|Yes|Tak|  
  
 Poniższy przykład kodu demonstruje sposób korzystania z delegowania.  
  
 [!code-csharp[c_delegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_delegation/cs/source.cs#1)]
 [!code-vb[c_delegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_delegation/vb/source.vb#1)]  
  
### <a name="how-to-configure-an-application-to-use-constrained-delegation"></a>Jak skonfigurować aplikację do korzystania z delegowania ograniczonego  
 Aby można było korzystać z delegowania ograniczonego, należy odpowiednio skonfigurować nadawcę, odbiorcę i kontroler domeny. Poniższa procedura zawiera listę czynności, które umożliwiają delegowanie ograniczone. Aby uzyskać szczegółowe informacje o różnicach między delegowaniem i delegowaniem ograniczonym, zobacz część [rozszerzeń systemu Windows Server 2003 Kerberos](https://go.microsoft.com/fwlink/?LinkId=100194) , które omawiają ograniczone dyskusje.  
  
1. Na kontrolerze domeny wyczyść pole wyboru **konto jest poufne i nie może być delegowane** dla konta, w ramach którego jest uruchomiona aplikacja kliencka.  
  
2. Na kontrolerze domeny zaznacz pole wyboru **konto jest zaufane dla delegowania** dla konta, w ramach którego uruchomiona jest aplikacja kliencka.  
  
3. Na kontrolerze domeny skonfiguruj komputer warstwy środkowej tak, aby był zaufany dla delegowania, klikając opcję **Ufaj komputerowi dla delegowania** .  
  
4. Na kontrolerze domeny skonfiguruj komputer warstwy środkowej do korzystania z delegowania ograniczonego, klikając opcję **Ufaj temu komputerowi w delegowaniu tylko do określonych usług** .  
  
 Aby uzyskać bardziej szczegółowe instrukcje dotyczące konfigurowania delegowania ograniczonego, zobacz następujące tematy w witrynie MSDN:  
  
- [Rozwiązywanie problemów z delegowaniem protokołu Kerberos](https://go.microsoft.com/fwlink/?LinkId=36724)  
  
- [Przejście protokołu Kerberos i ograniczone delegowanie](https://go.microsoft.com/fwlink/?LinkId=36725)  
  
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
