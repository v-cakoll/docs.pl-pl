---
title: Najlepsze rozwiązania dotyczące zabezpieczeń programu WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- best practices [WCF], security
ms.assetid: 3639de41-1fa7-4875-a1d7-f393e4c8bd69
ms.openlocfilehash: c99ab5e1e72aefc688df1692091e60caf930d5e4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597621"
---
# <a name="best-practices-for-security-in-wcf"></a>Najlepsze rozwiązania dotyczące zabezpieczeń programu WCF
W poniższych sekcjach przedstawiono najlepsze rozwiązania, które należy wziąć pod uwagę podczas tworzenia bezpiecznych aplikacji przy użyciu Windows Communication Foundation (WCF). Aby uzyskać więcej informacji na temat zabezpieczeń, zobacz [zagadnienia dotyczące zabezpieczeń](security-considerations-in-wcf.md), [zagadnienia](security-considerations-for-data.md)dotyczące zabezpieczeń danych i [kwestie dotyczące zabezpieczeń w przypadku metadanych](security-considerations-with-metadata.md).  
  
## <a name="identify-services-performing-windows-authentication-with-spns"></a>Identyfikowanie usług przeprowadzających uwierzytelnianie systemu Windows przy użyciu nazw SPN  
 Usługi mogą być identyfikowane za pomocą nazw głównych użytkowników (UPN) lub głównych nazw usług (SPN). Usługi działające w ramach kont komputerów, takich jak usługa sieciowa, mają tożsamość SPN odpowiadającą maszynie, z której są uruchomione. Usługi działające na kontach użytkowników mają tożsamość UPN odpowiadającą użytkownikowi, na którym są uruchamiane, chociaż `setspn` Narzędzie może służyć do przypisywania nazwy SPN do konta użytkownika. Skonfigurowanie usługi w taki sposób, aby mogła być identyfikowana za pośrednictwem nazwy SPN i skonfigurowanie klientów łączących się z usługą w celu użycia tej nazwy SPN może utrudnić pewne ataki. Te wskazówki dotyczą powiązań przy użyciu protokołu Kerberos lub negocjacji interfejsu SSPI.  Klienci powinni nadal określić nazwę SPN w przypadku, gdy SSPI powraca do protokołu NTLM.  
  
## <a name="verify-service-identities-in-wsdl"></a>Weryfikowanie tożsamości usług w języku WSDL  
 Usługa WS-SecurityPolicy umożliwia usługom publikowanie informacji o ich tożsamościach w metadanych. Po pobraniu za pośrednictwem `svcutil` lub innych metod, takich jak <xref:System.ServiceModel.Description.WsdlImporter> , informacje o tożsamości są tłumaczone na właściwości tożsamości adresów punktów końcowych usługi WCF. Klienci, którzy nie sprawdzają, czy te tożsamości usługi są poprawne i skutecznie omijają uwierzytelnianie usługi. Złośliwa usługa może wykorzystać tych klientów do wykonywania przekazywania poświadczeń i innych ataków typu "man in the middle", zmieniając tożsamość zażądaną w jej języku WSDL.  
  
## <a name="use-x509-certificates-instead-of-ntlm"></a>Używaj certyfikatów x509 zamiast protokołu NTLM  
 Usługa WCF oferuje dwa mechanizmy uwierzytelniania równorzędnego: certyfikaty x509 (używane przez kanał równorzędny) i uwierzytelnianie systemu Windows, w przypadku których negocjowanie protokołu SSPI obniży poziom uwierzytelniania Kerberos do NTLM.  Uwierzytelnianie oparte na certyfikatach przy użyciu kluczy o rozmiarze 1024 bitów lub większej jest preferowane do NTLM z kilku powodów:  
  
- dostępność wzajemnego uwierzytelniania,  
  
- Użycie silniejszych algorytmów kryptograficznych i  
  
- im większa jest liczba problemów z przekazywaniem przesyłanych dalej poświadczeń x509.  

## <a name="always-revert-after-impersonation"></a>Zawsze przywracaj po personifikacji  
 W przypadku korzystania z interfejsów API, które umożliwiają personifikację klienta, należy przywrócić oryginalną tożsamość. Na przykład podczas korzystania z <xref:System.Security.Principal.WindowsIdentity> i <xref:System.Security.Principal.WindowsImpersonationContext> , użyj instrukcji języka C# `using` lub `Using` instrukcji Visual Basic, jak pokazano w poniższym kodzie. <xref:System.Security.Principal.WindowsImpersonationContext>Klasa implementuje <xref:System.IDisposable> interfejs, a w związku z tym środowisko uruchomieniowe języka wspólnego (CLR) automatycznie przywraca oryginalną tożsamość, gdy kod opuszcza `using` blok.  
  
 [!code-csharp[c_SecurityBestPractices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securitybestpractices/cs/source.cs#1)]
 [!code-vb[c_SecurityBestPractices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securitybestpractices/vb/source.vb#1)]  
  
## <a name="impersonate-only-as-needed"></a>Personifikuj tylko w razie konieczności  
 Korzystając z <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metody <xref:System.Security.Principal.WindowsIdentity> klasy, można użyć personifikacji w bardzo kontrolowanym zakresie. Jest to w przeciwieństwie do użycia <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> właściwości <xref:System.ServiceModel.OperationBehaviorAttribute> , która umożliwia personifikację zakresu całej operacji. Jeśli to możliwe, należy kontrolować zakres personifikacji przy użyciu bardziej precyzyjnej <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metody.  
  
## <a name="obtain-metadata-from-trusted-sources"></a>Uzyskiwanie metadanych z zaufanych źródeł  
 Upewnij się, że ufasz źródłu metadanych, i upewnij się, że żaden z nich nie został naruszony przez metadane. Metadane pobrane przy użyciu protokołu HTTP są wysyłane w postaci zwykłego tekstu i mogą być modyfikowane przez program. Jeśli usługa używa <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> właściwości i, użyj adresu URL dostarczonego przez twórcę usługi, aby pobrać dane przy użyciu protokołu HTTPS.  
  
## <a name="publish-metadata-using-security"></a>Publikowanie metadanych przy użyciu zabezpieczeń  
 Aby uniemożliwić manipulowanie metadanymi opublikowanymi w usłudze, Zabezpiecz punkt końcowy wymiany metadanych przy użyciu transportu lub zabezpieczeń na poziomie wiadomości. Aby uzyskać więcej informacji, zobacz [Publikowanie punktów końcowych metadanych](../publishing-metadata-endpoints.md) i [instrukcje: Publikowanie metadanych dla usługi przy użyciu kodu](how-to-publish-metadata-for-a-service-using-code.md).  
  
## <a name="ensure-use-of-local-issuer"></a>Upewnij się, że wystawcy lokalnego  
 Jeśli dla danego powiązania określono adres wystawcy i powiązanie, wystawca lokalnego nie jest używany dla punktów końcowych używających tego powiązania. Klienci, którzy oczekują zawsze używać wystawcy lokalnego, powinni upewnić się, że nie używają takiego powiązania lub że modyfikują powiązanie, tak że adres wystawcy ma wartość null.  
  
## <a name="saml-token-size-quotas"></a>Limity przydziału rozmiaru tokenu SAML  
 Gdy tokeny języka SAML (Security Assertions Markup Language) są serializowane w komunikatach, gdy są wystawiane przez usługę tokenu zabezpieczającego (STS) lub gdy klienci składają je do usług w ramach uwierzytelniania, maksymalny przydział rozmiaru komunikatu musi być wystarczająco duży, aby pomieścić token SAML i inne części komunikatów. W normalnych przypadkach domyślne limity przydziału rozmiaru wiadomości są wystarczające. Jednak w przypadkach, gdy token SAML jest duży, ponieważ zawiera setki oświadczeń, limity przydziału należy zwiększyć, aby uwzględnić serializowany token. Aby uzyskać więcej informacji na temat przydziałów, zobacz [zagadnienia dotyczące zabezpieczeń danych](security-considerations-for-data.md).  
  
## <a name="set-securitybindingelementincludetimestamp-to-true-on-custom-bindings"></a>Ustaw elementu SecurityBindingElement. IncludeTimestamp na true w powiązaniach niestandardowych  
 Podczas tworzenia niestandardowego powiązania należy ustawić wartość <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> `true` . W przeciwnym razie, jeśli <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> jest ustawiona na `false` , a klient korzysta z tokenu klucza asymetrycznego, takiego jak certyfikat x509, komunikat nie zostanie podpisany.  
  
## <a name="see-also"></a>Zobacz też

- [Zagadnienia dotyczące zabezpieczeń](security-considerations-in-wcf.md)
- [Zagadnienia związane z zabezpieczeniami danych](security-considerations-for-data.md)
- [Zagadnienia dotyczące zabezpieczeń obejmujące metadane](security-considerations-with-metadata.md)
