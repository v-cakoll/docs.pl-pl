---
title: Najlepsze rozwiązania dotyczące zabezpieczeń programu WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- best practices [WCF], security
ms.assetid: 3639de41-1fa7-4875-a1d7-f393e4c8bd69
ms.openlocfilehash: c8c0c084ac3b1cf06fc5f2b3df85fa979744e17b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185418"
---
# <a name="best-practices-for-security-in-wcf"></a>Najlepsze rozwiązania dotyczące zabezpieczeń programu WCF
W poniższych sekcjach przedstawiono najlepsze rozwiązania, które należy wziąć pod uwagę podczas tworzenia bezpiecznych aplikacji przy użyciu programu Windows Communication Foundation (WCF). Aby uzyskać więcej informacji na temat zabezpieczeń, zobacz [Zagadnienia dotyczące zabezpieczeń,](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md) [Zagadnienia dotyczące zabezpieczeń dotyczące danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)i [Zagadnienia dotyczące zabezpieczeń za pomocą metadanych](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md).  
  
## <a name="identify-services-performing-windows-authentication-with-spns"></a>Identyfikowanie usług uwierzytelniania systemu Windows przy użyciu kodów SPN  
 Usługi można identyfikować za pomocą nazw głównych użytkowników (UPN) lub nazw głównych usług (SPN). Usługi uruchomione w ramach kont komputera, takich jak usługa sieciowa, mają tożsamość SPN odpowiadającą uruchomionemu komputerze. Usługi działające na kontach użytkowników mają tożsamość nazwy UPN `setspn` odpowiadającą użytkownikowi, dla którego są uruchomione, chociaż narzędzie może służyć do przypisywania nazwy SPN do konta użytkownika. Konfigurowanie usługi, dzięki czemu można ją zidentyfikować za pośrednictwem nazwy SPN i konfigurowanie klientów łączących się z usługą w celu użycia tej nazwy SPN może utrudnić niektóre ataki. Niniejsze wskazówki dotyczą powiązań przy użyciu protokołu Kerberos lub negocjacji SSPI.  Klienci powinni nadal określać nazwę SPN w przypadku, gdy interfejs SSPI powraca do ntlm.  
  
## <a name="verify-service-identities-in-wsdl"></a>Weryfikowanie tożsamości usługi w WSDL  
 WS-SecurityPolicy umożliwia usługom publikowanie informacji o ich tożsamości w metadanych. Po pobraniu za `svcutil` pośrednictwem <xref:System.ServiceModel.Description.WsdlImporter>lub innych metod, takich jak , te informacje o tożsamości jest tłumaczony do właściwości tożsamości adresów punktu końcowego usługi WCF. Klienci, którzy nie weryfikują, czy te tożsamości usługi są poprawne i prawidłowe skutecznie pomijają uwierzytelnianie usługi. Złośliwa usługa może wykorzystać takich klientów do przekazywania poświadczeń i innych ataków typu "man in the middle", zmieniając tożsamość zgłoszoną w sieci WSDL.  
  
## <a name="use-x509-certificates-instead-of-ntlm"></a>Użyj certyfikatów X509 zamiast NTLM  
 WCF oferuje dwa mechanizmy uwierzytelniania peer-to-peer: certyfikaty X509 (używane przez kanał równorzędny) i uwierzytelnianie systemu Windows, w którym negocjacja SSPI obniża poziom protokołu Kerberos na NTLM.  Uwierzytelnianie oparte na certyfikatach przy użyciu kluczy o rozmiarach 1024 bitów lub większej jest preferowane w przypadku ntlm z kilku powodów:  
  
- dostępność wzajemnego uwierzytelniania,  
  
- stosowanie silniejszych algorytmów kryptograficznych, oraz  
  
- większą trudność wykorzystania przekazanych poświadczeń X509.  

## <a name="always-revert-after-impersonation"></a>Zawsze powracaj po personifikacji  
 Korzystając z interfejsów API, które umożliwiają personifikacji klienta, należy przywrócić oryginalną tożsamość. Na przykład podczas <xref:System.Security.Principal.WindowsIdentity> korzystania <xref:System.Security.Principal.WindowsImpersonationContext>z i `using` , użyj instrukcji`Using` C# lub Visual Basic instrukcji, jak pokazano w poniższym kodzie. Klasa <xref:System.Security.Principal.WindowsImpersonationContext> implementuje <xref:System.IDisposable> interfejs i dlatego środowisko uruchomieniowe języka wspólnego (CLR) automatycznie powraca do `using` oryginalnej tożsamości, gdy kod opuszcza blok.  
  
 [!code-csharp[c_SecurityBestPractices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securitybestpractices/cs/source.cs#1)]
 [!code-vb[c_SecurityBestPractices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securitybestpractices/vb/source.vb#1)]  
  
## <a name="impersonate-only-as-needed"></a>Personifikuj tylko w razie potrzeby  
 Przy <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> użyciu metody <xref:System.Security.Principal.WindowsIdentity> klasy, można użyć personifikacji w bardzo kontrolowanym zakresie. Jest to w przeciwieństwie <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> do <xref:System.ServiceModel.OperationBehaviorAttribute>korzystania z właściwości , który umożliwia personifikacji dla zakresu całej operacji. Jeśli to możliwe, należy kontrolować zakres personifikacji przy użyciu metody bardziej precyzyjne. <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>  
  
## <a name="obtain-metadata-from-trusted-sources"></a>Uzyskiwanie metadanych z zaufanych źródeł  
 Upewnij się, że ufasz źródła metadanych i upewnij się, że nikt nie sfałszował metadanych. Metadane pobrane przy użyciu protokołu HTTP są wysyłane w postaci zwykłego tekstu i mogą być modyfikowane. Jeśli usługa używa <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> właściwości <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> i, użyj adresu URL dostarczonego przez twórcę usługi, aby pobrać dane przy użyciu protokołu HTTPS.  
  
## <a name="publish-metadata-using-security"></a>Publikowanie metadanych przy użyciu zabezpieczeń  
 Aby zapobiec manipulowaniu opublikowanymi metadanymi usługi, zabezpiecz punkt końcowy wymiany metadanych za pomocą zabezpieczeń na poziomie transportu lub wiadomości. Aby uzyskać więcej informacji, zobacz [Publikowanie punktów końcowych metadanych](../../../../docs/framework/wcf/publishing-metadata-endpoints.md) i [jak: Publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
## <a name="ensure-use-of-local-issuer"></a>Zapewnienie wykorzystania lokalnego emitenta  
 Jeśli adres wystawcy i powiązanie są określone dla danego powiązania, wystawca lokalny nie jest używany dla punktów końcowych, które używają tego powiązania. Klienci, którzy oczekują, że zawsze będą używać wystawcy lokalnego, powinni upewnić się, że nie używają takiego powiązania lub że modyfikują powiązanie w taki sposób, że adres wystawcy ma wartość null.  
  
## <a name="saml-token-size-quotas"></a>Przydziały rozmiaru tokenu SAML  
 Gdy tokeny języka znaczników oświadczeń zabezpieczeń (SAML) są serializowane w wiadomościach, gdy są wystawiane przez usługę tokenu zabezpieczającego (STS) lub gdy klienci prezentują je usługom w ramach uwierzytelniania, maksymalny przydział rozmiaru wiadomości musi być wystarczający aby pomieścić token SAML i inne części wiadomości. W normalnych przypadkach domyślne przydziały rozmiaru wiadomości są wystarczające. Jednak w przypadkach, gdy token SAML jest duży, ponieważ zawiera setki oświadczeń, przydziały powinny zostać zwiększone w celu uwzględnienia tokenu serializowanego. Aby uzyskać więcej informacji na temat przydziałów, zobacz [Zagadnienia dotyczące zabezpieczeń dla danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## <a name="set-securitybindingelementincludetimestamp-to-true-on-custom-bindings"></a>Ustawianie powiązania SecurityBindingElement.IncludeTimestamp na true w przypadku powiązań niestandardowych  
 Podczas tworzenia niestandardowego powiązania należy <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> `true`ustawić na . W przeciwnym <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> razie, `false`jeśli jest ustawiona na , a klient używa tokenu opartego na kluczu asymetrycznym, takiego jak certyfikat X509, wiadomość nie zostanie podpisana.  
  
## <a name="see-also"></a>Zobacz też

- [Zagadnienia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Zagadnienia związane z zabezpieczeniami danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)
- [Zagadnienia dotyczące zabezpieczeń obejmujące metadane](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
