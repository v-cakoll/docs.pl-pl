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
ms.openlocfilehash: 3fd90cde16afdfe32b9bd0533ba04e35928d2706
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920202"
---
# <a name="delegation-and-impersonation-with-wcf"></a>Delegowanie i personifikacja za pomocą programu WCF
*Personifikacja* jest powszechną techniką używaną przez usługi do ograniczania dostępu klientów do zasobów domeny usługi. Zasoby domeny usługi mogą być zasobami maszynowymi, takimi jak pliki lokalne (personifikacja) lub zasobami na innej maszynie, takimi jak udział plików (delegowanie). Aby uzyskać przykładową aplikację, zobacz [Personifikowanie klienta](../../../../docs/framework/wcf/samples/impersonating-the-client.md). Przykład korzystania z personifikacji można znaleźć [w temacie How to: Personifikuj klienta w usłudze](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md).  
  
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
  
- <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>i <xref:System.ServiceModel.NetTcpBinding> z poświadczeniem klienta systemu Windows.  
  
- <xref:System.ServiceModel.BasicHttpBinding> z <xref:System.ServiceModel.BasicHttpSecurityMode>em ustawionym na poświadczenie <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> lub dowolnego innego powiązania standardowego, w którym klient przedstawia poświadczenia nazwy użytkownika, które usługa może zamapować na prawidłowe konto systemu Windows.  
  
- Wszystkie <xref:System.ServiceModel.Channels.CustomBinding> używające poświadczeń klienta systemu Windows z `requireCancellation` ustawionym na `true`. (Właściwość jest dostępna w następujących klasach: <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>, <xref:System.ServiceModel.Security.Tokens.SslSecurityTokenParameters>i <xref:System.ServiceModel.Security.Tokens.SspiSecurityTokenParameters>). Jeśli w powiązaniu jest używana bezpieczna Konwersacja, musi mieć ona również właściwość `requireCancellation` ustawioną na `true`.  
  
- Dowolny <xref:System.ServiceModel.Channels.CustomBinding>, na którym klient przedstawia poświadczenia nazwy użytkownika. Jeśli w powiązaniu jest używana bezpieczna Konwersacja, musi mieć ona również właściwość `requireCancellation` ustawioną na `true`.  
  
### <a name="s4u-based-impersonation"></a>Personifikacja oparta na protokole S4U  
 Personifikację opartą na protokole S4U można wykonać przy użyciu następujących czynności:  
  
- <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>i <xref:System.ServiceModel.NetTcpBinding> z poświadczenia klienta certyfikatu, które usługa może zamapować na prawidłowe konto systemu Windows.  
  
- Wszystkie <xref:System.ServiceModel.Channels.CustomBinding>, które używają poświadczeń klienta systemu Windows z właściwością `requireCancellation` ustawioną na `false`.  
  
- Wszystkie <xref:System.ServiceModel.Channels.CustomBinding> używające nazwy użytkownika lub poświadczeń klienta systemu Windows i bezpiecznej konwersacji z właściwością `requireCancellation` ustawioną na `false`.  
  
 Zakres, w jakim usługa może personifikować klienta, zależy od uprawnień, które są przechowywane w ramach konta usługi podczas próby personifikacji, rodzaju użytego personifikacji, a także zakresu personifikacji, który klient zezwala.  
  
> [!NOTE]
> Gdy klient i usługa są uruchomione na tym samym komputerze, a klient jest uruchomiony na koncie systemowym (na przykład `Local System` lub `Network Service`), nie można spersonifikować klienta w przypadku ustanowienia bezpiecznej sesji z tokenami kontekstu zabezpieczeń stanowych. Aplikacja konsoli lub formularza systemu Windows jest zwykle uruchamiana w ramach aktualnie zalogowanego konta, dzięki czemu konto może być domyślnie personifikowane. Jeśli jednak klient jest stroną ASP.NET, a ta strona jest hostowana w usługach IIS 6,0 lub IIS 7,0, klient uruchamia się domyślnie przy użyciu konta `Network Service`. Wszystkie powiązania dostarczone przez system obsługujące bezpieczne sesje domyślnie korzystają z tokenu bezstanowego kontekstu zabezpieczeń (SCT). Jeśli jednak klient jest stroną ASP.NET i są używane bezpieczne sesje ze stanem SCTs, nie można spersonifikować klienta. Aby uzyskać więcej informacji o używaniu stanowych SCTs w bezpiecznej sesji, zobacz [How to: Create a Security Context token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
## <a name="impersonation-in-a-service-method-declarative-model"></a>Personifikacja w metodzie usługi: model deklaratywny  
 Większość scenariuszy personifikacji obejmuje wykonywanie metody usługi w kontekście obiektu wywołującego. Funkcja WCF udostępnia funkcję personifikacji, która ułatwia wykonywanie tych czynności przez umożliwienie użytkownikowi określenia wymagania personifikacji w atrybucie <xref:System.ServiceModel.OperationBehaviorAttribute>. Na przykład w poniższym kodzie Infrastruktura WCF personifikuje wywołującego przed wykonaniem metody `Hello`. Wszystkie próby dostępu do natywnych zasobów wewnątrz metody `Hello` powiodło się tylko wtedy, gdy lista kontroli dostępu (ACL) zasobu zezwala na uprawnienia dostępu do obiektu wywołującego. Aby włączyć personifikację, ustaw właściwość <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> na jedną z <xref:System.ServiceModel.ImpersonationOption> wartości wyliczenia, <xref:System.ServiceModel.ImpersonationOption.Required?displayProperty=nameWithType> lub <xref:System.ServiceModel.ImpersonationOption.Allowed?displayProperty=nameWithType>, jak pokazano w poniższym przykładzie.  
  
> [!NOTE]
> Jeśli usługa ma wyższe poświadczenia niż Klient zdalny, poświadczenia usługi są używane, jeśli właściwość <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> jest ustawiona na <xref:System.ServiceModel.ImpersonationOption.Allowed>. Oznacza to, że jeśli użytkownik z niskim poziomem uprawnień poda swoje poświadczenia, usługa wyższego uprzywilejowania wykonuje metodę z poświadczeniami usługi i może korzystać z zasobów, które nie będą mogły być używane przez użytkownika z niskim poziomem uprawnień.  
  
 [!code-csharp[c_ImpersonationAndDelegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#1)]
 [!code-vb[c_ImpersonationAndDelegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#1)]  
  
 Infrastruktura WCF może personifikować wywołującego tylko wtedy, gdy obiekt wywołujący jest uwierzytelniany przy użyciu poświadczeń, które mogą być mapowane na konto użytkownika systemu Windows. Jeśli usługa jest skonfigurowana do uwierzytelniania przy użyciu poświadczeń, których nie można zamapować na konto systemu Windows, metoda usługi nie jest wykonywana.  
  
> [!NOTE]
> W systemie Windows XP personifikacja kończy się niepowodzeniem, jeśli zostanie utworzony stanowy SCT, co spowoduje wystąpienie <xref:System.InvalidOperationException>. Aby uzyskać więcej informacji, zobacz [scenariusze nieobsługiwane](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="impersonation-in-a-service-method-imperative-model"></a>Personifikacja w metodzie usługi: model bezwzględny  
 Czasami obiekt wywołujący nie musi personifikować całej metody usługi, aby działała, ale tylko dla jego części. W takim przypadku należy uzyskać tożsamość systemu Windows wywołującego w metodzie usługi i bezwzględnie przeprowadzić personifikację. W tym celu należy użyć właściwości <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> <xref:System.ServiceModel.ServiceSecurityContext>, aby zwrócić wystąpienie klasy <xref:System.Security.Principal.WindowsIdentity> i wywołać metodę <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> przed użyciem wystąpienia.  
  
> [!NOTE]
> Należy pamiętać, aby użyć instrukcji Visual Basic`Using` lub instrukcji C# `using`, aby automatycznie przywrócić akcję personifikacji. Jeśli nie używasz instrukcji lub jeśli używasz języka programowania innego niż Visual Basic lub C#, pamiętaj o odwróceniu poziomu personifikacji. Niewykonanie tej czynności może stanowić podstawę ataku typu "odmowa usługi" i podniesienia poziomu uprawnień.  
  
 [!code-csharp[c_ImpersonationAndDelegation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#2)]
 [!code-vb[c_ImpersonationAndDelegation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#2)]  
  
## <a name="impersonation-for-all-service-methods"></a>Personifikacja dla wszystkich metod usługi  
 W niektórych przypadkach należy wykonać wszystkie metody usługi w kontekście obiektu wywołującego. Zamiast jawnie włączyć tę funkcję dla poszczególnych metod, użyj <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Jak pokazano w poniższym kodzie, ustaw właściwość <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A> na `true`. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> jest pobierana z kolekcji zachowań klasy <xref:System.ServiceModel.ServiceHost>. Należy również zauważyć, że właściwość `Impersonation` <xref:System.ServiceModel.OperationBehaviorAttribute> stosowana do każdej metody musi być również ustawiona na <xref:System.ServiceModel.ImpersonationOption.Allowed> lub <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
 [!code-csharp[c_ImpersonationAndDelegation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#3)]
 [!code-vb[c_ImpersonationAndDelegation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#3)]  
  
 W poniższej tabeli opisano zachowanie WCF dla wszystkich możliwych kombinacji `ImpersonationOption` i `ImpersonateCallerForAllServiceOperations`.  
  
|`ImpersonationOption`|`ImpersonateCallerForAllServiceOperations`|Zachowanie|  
|---------------------------|------------------------------------------------|--------------|  
|Wymagane|n/d|Funkcja WCF personifikuje wywołującego|  
|Występować|{1&gt;false&lt;1}|Funkcja WCF nie personifikuje wywołującego|  
|Występować|true|Funkcja WCF personifikuje wywołującego|  
|NotAllowed|{1&gt;false&lt;1}|Funkcja WCF nie personifikuje wywołującego|  
|NotAllowed|true|Niedozwolone. (Zgłoszono <xref:System.InvalidOperationException>.)|  
  
## <a name="impersonation-level-obtained-from-windows-credentials-and-cached-token-impersonation"></a>Poziom personifikacji uzyskany z poświadczeń systemu Windows i personifikacja tokenu w pamięci podręcznej  
 W niektórych scenariuszach klient ma częściową kontrolę nad poziomem personifikacji wykonywanym przez usługę podczas korzystania z poświadczeń klienta systemu Windows. Jeden scenariusz występuje, gdy klient określi poziom personifikacji anonimowej. Druga dzieje się podczas przeprowadzania personifikacji z buforowanym tokenem. Jest to realizowane przez ustawienie właściwości <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> klasy <xref:System.ServiceModel.Security.WindowsClientCredential>, która jest dostępna jako właściwość klasy generycznej <xref:System.ServiceModel.ChannelFactory%601>.  
  
> [!NOTE]
> Określenie poziomu personifikacji anonimowe powoduje, że klient loguje się do usługi anonimowo. W związku z tym usługa musi zezwalać na Logowanie anonimowe, niezależnie od tego, czy jest wykonywana personifikacja.  
  
 Klient może określić poziom personifikacji jako <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>lub <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Tworzony jest tylko token na określonym poziomie, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_ImpersonationAndDelegation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#4)]
 [!code-vb[c_ImpersonationAndDelegation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#4)]  
  
 W poniższej tabeli określono poziom personifikacji uzyskany przez usługę podczas personifikacji z buforowanego tokenu.  
  
|wartość `AllowedImpersonationLevel`|Usługa ma `SeImpersonatePrivilege`|Usługa i klient mogą przebudować|`ImpersonationLevel` tokenów w pamięci podręcznej|  
|---------------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Anonimowe|Tak|n/d|Personifikacja|  
|Anonimowe|Nie|n/d|Identification|  
|Identification|n/d|n/d|Identification|  
|Personifikacja|Tak|n/d|Personifikacja|  
|Personifikacja|Nie|n/d|Identification|  
|Wierz|Tak|Tak|Wierz|  
|Wierz|Tak|Nie|Personifikacja|  
|Wierz|Nie|n/d|Identification|  
  
## <a name="impersonation-level-obtained-from-user-name-credentials-and-cached-token-impersonation"></a>Poziom personifikacji uzyskany na podstawie poświadczeń nazwy użytkownika i personifikacji tokenu w pamięci podręcznej  
 Przekazując usługę nazwę użytkownika i hasło, klient włącza funkcję WCF do logowania się jako ten użytkownik, który jest równoznaczny z ustawieniem właściwości `AllowedImpersonationLevel` na <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. (`AllowedImpersonationLevel` jest dostępny w klasach <xref:System.ServiceModel.Security.WindowsClientCredential> i <xref:System.ServiceModel.Security.HttpDigestClientCredential>). Poniższa tabela zawiera poziom personifikacji uzyskany, gdy usługa otrzymuje poświadczenia nazwy użytkownika.  
  
|`AllowedImpersonationLevel`|Usługa ma `SeImpersonatePrivilege`|Usługa i klient mogą przebudować|`ImpersonationLevel` tokenów w pamięci podręcznej|  
|---------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|n/d|Tak|Tak|Wierz|  
|n/d|Tak|Nie|Personifikacja|  
|n/d|Nie|n/d|Identification|  
  
## <a name="impersonation-level-obtained-from-s4u-based-impersonation"></a>Poziom personifikacji uzyskany z personifikacji opartej na protokole S4U  
  
|Usługa ma `SeTcbPrivilege`|Usługa ma `SeImpersonatePrivilege`|Usługa i klient mogą przebudować|`ImpersonationLevel` tokenów w pamięci podręcznej|  
|----------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Tak|Tak|n/d|Personifikacja|  
|Tak|Nie|n/d|Identification|  
|Nie|n/d|n/d|Identification|  
  
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
  
```csharp
// Create a binding that sets a certificate as the client credential type.  
WSHttpBinding b = new WSHttpBinding();  
b.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a service host that maps the certificate to a Windows account.  
Uri httpUri = new Uri("http://localhost/Calculator");  
ServiceHost sh = new ServiceHost(typeof(HelloService), httpUri);  
sh.Credentials.ClientCertificate.Authentication.MapClientCertificateToWindowsAccount = true;  
```  
  
## <a name="delegation"></a>Wierz  
 Aby delegować do usługi zaplecza, usługa musi wykonać wieloetapowe uwierzytelnianie Kerberos (SSPI bez powrotu NTLM) lub Kerberos Direct do usługi zaplecza przy użyciu tożsamości systemu Windows klienta. Aby delegować do usługi zaplecza, Utwórz <xref:System.ServiceModel.ChannelFactory%601> i kanał, a następnie przekomunikuj się za pośrednictwem kanału podczas personifikowania klienta. Dzięki tej formie delegowania odległość, z jaką usługa zaplecza może znajdować się w usłudze frontonu, zależy od poziomu personifikacji osiągniętego przez usługę frontonu. Gdy poziom personifikacji to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, usługi frontonu i zaplecza muszą być uruchomione na tym samym komputerze. Gdy poziom personifikacji to <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, usługi frontonu i zaplecza mogą znajdować się na oddzielnych maszynach lub na tym samym komputerze. Włączenie personifikacji na poziomie delegowania wymaga skonfigurowania zasad domeny systemu Windows do zezwalania na delegowanie. Aby uzyskać więcej informacji o konfigurowaniu Active Directory na potrzeby obsługi delegowania, zobacz [Włączanie uwierzytelniania delegowanego](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc780217(v=ws.10)).  
  
> [!NOTE]
> Gdy klient uwierzytelnia się w usłudze frontonu przy użyciu nazwy użytkownika i hasła, które odpowiadają kontu systemu Windows w usłudze zaplecza, usługa frontonu może uwierzytelniać się w usłudze zaplecza przez ponowne użycie nazwy użytkownika i hasła klienta. Jest to szczególnie wydajna postać przepływu tożsamości, ponieważ przekazywanie nazwy użytkownika i hasła do usługi zaplecza umożliwia usłudze zaplecza wykonywanie personifikacji, ale nie stanowi delegowania, ponieważ nie jest używany protokół Kerberos. Kontrolki Active Directory w delegowaniu nie mają zastosowania do uwierzytelniania nazwy użytkownika i hasła.  
  
### <a name="delegation-ability-as-a-function-of-impersonation-level"></a>Możliwość delegowania jako funkcja poziomu personifikacji  
  
|Poziom personifikacji|Usługa może przeprowadzać delegowanie między procesami|Usługa może wykonywać delegowanie między maszynami|  
|-------------------------|---------------------------------------------------|---------------------------------------------------|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Identification>|Nie|Nie|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>|Tak|Nie|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Delegation>|Tak|Tak|  
  
 Poniższy przykład kodu demonstruje sposób korzystania z delegowania.  
  
 [!code-csharp[c_delegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_delegation/cs/source.cs#1)]
 [!code-vb[c_delegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_delegation/vb/source.vb#1)]  
  
### <a name="how-to-configure-an-application-to-use-constrained-delegation"></a>Jak skonfigurować aplikację do korzystania z delegowania ograniczonego  
 Aby można było korzystać z delegowania ograniczonego, należy odpowiednio skonfigurować nadawcę, odbiorcę i kontroler domeny. Poniższa procedura zawiera listę czynności, które umożliwiają delegowanie ograniczone. Aby uzyskać szczegółowe informacje o różnicach między delegowaniem i delegowaniem ograniczonym, zobacz część [rozszerzeń systemu Windows Server 2003 Kerberos](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc738207(v=ws.10)) , które omawiają ograniczone dyskusje.  
  
1. Na kontrolerze domeny wyczyść pole wyboru **konto jest poufne i nie może być delegowane** dla konta, w ramach którego jest uruchomiona aplikacja kliencka.  
  
2. Na kontrolerze domeny zaznacz pole wyboru **konto jest zaufane dla delegowania** dla konta, w ramach którego uruchomiona jest aplikacja kliencka.  
  
3. Na kontrolerze domeny skonfiguruj komputer warstwy środkowej tak, aby był zaufany dla delegowania, klikając opcję **Ufaj komputerowi dla delegowania** .  
  
4. Na kontrolerze domeny skonfiguruj komputer warstwy środkowej do korzystania z delegowania ograniczonego, klikając opcję **Ufaj temu komputerowi w delegowaniu tylko do określonych usług** .  
  
 Aby uzyskać bardziej szczegółowe instrukcje dotyczące konfigurowania delegowania ograniczonego, zobacz [przejście do protokołu Kerberos i delegowanie ograniczone](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc739587(v=ws.10)).
  
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
- [Instrukcje: personifikowanie klienta w usłudze](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)
- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
