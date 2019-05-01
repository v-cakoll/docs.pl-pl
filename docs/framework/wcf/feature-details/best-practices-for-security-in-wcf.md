---
title: Najlepsze rozwiązania dotyczące zabezpieczeń programu WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- best practices [WCF], security
ms.assetid: 3639de41-1fa7-4875-a1d7-f393e4c8bd69
ms.openlocfilehash: f0305807e76ca27e1979aa23bf0797c505fee566
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62048247"
---
# <a name="best-practices-for-security-in-wcf"></a>Najlepsze rozwiązania dotyczące zabezpieczeń programu WCF
W poniższych sekcjach wymieniono najlepsze rozwiązania, należy wziąć pod uwagę podczas tworzenia bezpiecznych aplikacji za pomocą usługi Windows Communication Foundation (WCF). Aby uzyskać więcej informacji na temat zabezpieczeń, zobacz [zagadnienia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md), [zagadnienia dotyczące zabezpieczeń dla danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md), i [zagadnienia dotyczące zabezpieczeń obejmujące metadane](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md).  
  
## <a name="identify-services-performing-windows-authentication-with-spns"></a>Zidentyfikuj usługi uwierzytelniania Windows za pomocą nazw SPN  
 Usługi można zidentyfikować za pomocą nazwy głównej użytkownika (UPN) lub głównej nazwy usługi (SPN). Do usług działających w ramach konta komputera, takie jak Usługa sieciowa ma tożsamością SPN odpowiadające maszynie, na których są one uruchamiane. Usług działających w ramach konta użytkowników mają tożsamością UPN odpowiadający użytkownika, są one uruchamiane jako, mimo że `setspn` narzędzie może służyć do przypisania nazwy SPN na koncie użytkownika. Konfigurowanie usługi, dzięki czemu mogą być identyfikowane przez nazwę SPN i konfigurowanie klientów połączenia z usługą, aby użyć tej nazwy SPN może wykonywać niektórych ataki trudniejsze. Niniejsze wytyczne mają zastosowanie do powiązania przy użyciu negocjacji protokołu Kerberos lub SSPI.  Klienci nadal należy określić nazwę SPN w przypadku, gdy SSPI powraca do NTLM.  
  
## <a name="verify-service-identities-in-wsdl"></a>Sprawdź tożsamości usługi w języka WSDL  
 WS SecurityPolicy umożliwia usługom do publikowania informacji o własną tożsamość w metadanych. Podczas pobierania za pośrednictwem `svcutil` lub innych metod, takich jak <xref:System.ServiceModel.Description.WsdlImporter>, informacje o tożsamości jest tłumaczona na właściwości tożsamości adresy punktów końcowych usługi WCF. Klientów, które sprawdza, czy te tożsamości usługi są poprawne i prawidłowe skutecznie obejście uwierzytelniania usługi. Złośliwe usługi mogą wykorzystać takich klientów można wykonać przekazywania poświadczeń i inne ataki man-in middle", zmieniając tożsamości zgłoszone w jego WSDL.  
  
## <a name="use-x509-certificates-instead-of-ntlm"></a>Użyj X509 certyfikatów zamiast protokołu NTLM  
 Usługi WCF oferuje dwa mechanizmy uwierzytelniania peer-to-peer: X509 certyfikatów (używanych przez kanał elementu równorzędnego) i uwierzytelnianie Windows, gdzie negocjacji interfejsu SSPI obniży z protokołu Kerberos, NTLM.  Uwierzytelnianie oparte na certyfikatach, za pomocą rozmiarów klucza 1024 bity lub więcej jest preferowany NTLM z kilku powodów:  
  
- dostępność wzajemnego uwierzytelniania  
  
- Użycie silniejszych algorytmów kryptograficznych, a  
  
- większa trudności przy użyciu przekazywane X509 poświadczeń.  
   
## <a name="always-revert-after-impersonation"></a>Zawsze wracają po personifikacji  
 Korzystając z interfejsów API pozwalających na korzystanie z personifikacji klienta, pamiętaj przywrócić oryginalną tożsamość. Na przykład w przypadku korzystania z <xref:System.Security.Principal.WindowsIdentity> i <xref:System.Security.Principal.WindowsImpersonationContext>, używaj języka C# `using` instrukcji lub Visual Basic`Using` instrukcji, jak pokazano w poniższym kodzie. <xref:System.Security.Principal.WindowsImpersonationContext> Klasy implementuje <xref:System.IDisposable> interfejsu i w związku z tym środowisko uruchomieniowe języka wspólnego (CLR) zostanie automatycznie przywrócona do oryginalnego tożsamości po opuszczeniu kod `using` bloku.  
  
 [!code-csharp[c_SecurityBestPractices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securitybestpractices/cs/source.cs#1)]
 [!code-vb[c_SecurityBestPractices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securitybestpractices/vb/source.vb#1)]  
  
## <a name="impersonate-only-as-needed"></a>Personifikuj tylko zgodnie z potrzebami  
 Za pomocą <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metody <xref:System.Security.Principal.WindowsIdentity> klasy, jest możliwe, należy używać personifikacji w zakresie bardzo kontrolowany. Dzięki temu nie trzeba za pomocą <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> właściwość <xref:System.ServiceModel.OperationBehaviorAttribute>, co umożliwia personifikacji dla zakresu całej operacji. Jeśli to możliwe, kontrolować zakres personalizacji, przy użyciu bardziej precyzyjne <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metody.  
  
## <a name="obtain-metadata-from-trusted-sources"></a>Uzyskiwanie metadanych z zaufanych źródeł  
 Pamiętaj, pochodzi z zaufanego źródła metadanych i upewnij się, że nikt nie ingerował metadanych. Metadane pobrany przy użyciu protokołu HTTP są wysyłane w postaci zwykłego tekstu i może zostać zmieniony. Jeśli usługa używa <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> i <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> właściwości, użyj adres URL podany przez twórcę usługi podczas pobierania danych przy użyciu protokołu HTTPS.  
  
## <a name="publish-metadata-using-security"></a>Publikowanie metadanych przy użyciu zabezpieczeń  
 Aby zapobiec modyfikowaniu metadanymi opublikowanej usługi, należy zabezpieczyć punkt końcowy wymiany metadanych za pomocą transportu lub zabezpieczenia na poziomie komunikatu. Aby uzyskać więcej informacji, zobacz [publikowanie punktów końcowych metadanych](../../../../docs/framework/wcf/publishing-metadata-endpoints.md) i [jak: Publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
## <a name="ensure-use-of-local-issuer"></a>Upewnij się, Użyj lokalnego wystawcy  
 Wystawca adres i powiązanie są określone dla danego powiązania, wystawcy lokalnego nie jest używana dla punktów końcowych, korzystające z tego wiązania. Klienci, którzy oczekują zawsze używaj wystawcy lokalnego należy upewnić się, że nie używaj takiego powiązania lub mogą modyfikować powiązania taki sposób, że adres wystawca ma wartość null.  
  
## <a name="saml-token-size-quotas"></a>Przydziały rozmiar tokenu SAML  
 Tokeny zabezpieczeń potwierdzenia Markup Language (SAML) są serializowane w wiadomości, wystawiane przez Usługa tokenu zabezpieczającego (STS) lub, gdy klienci je do usług w ramach uwierzytelniania, maksymalny przydział rozmiaru komunikatu musi być wystarczająco duża, aby uwzględnić w tokenie języka SAML i inne części wiadomości. W warunkach normalnych domyślne limity przydziału rozmiaru wiadomości są wystarczające. Jednak w przypadku, gdy SAML token jest duże, ponieważ zawiera ona setki oświadczenia, limity przydziału należy zwiększyć Zserializowany token. Aby uzyskać więcej informacji na temat limitów przydziału, zobacz [zagadnienia dotyczące zabezpieczeń dla danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## <a name="set-securitybindingelementincludetimestamp-to-true-on-custom-bindings"></a>Ustaw SecurityBindingElement.IncludeTimestamp wartość True na powiązań niestandardowych  
 Podczas tworzenia niestandardowego powiązania, należy ustawić <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> do `true`. W przeciwnym razie, jeśli <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> jest ustawiona na `false`, a klient używa asymetrycznego token opartego na kluczach, takich jak X509 certyfikatu, komunikat nie zostanie ona podpisana.  
  
## <a name="see-also"></a>Zobacz także

- [Zagadnienia dotyczące bezpieczeństwa](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Zagadnienia związane z zabezpieczeniami danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)
- [Zagadnienia dotyczące zabezpieczeń obejmujące metadane](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
