---
title: Najlepsze rozwiązania dotyczące zabezpieczeń programu WCF
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
- best practices [WCF], security
ms.assetid: 3639de41-1fa7-4875-a1d7-f393e4c8bd69
caps.latest.revision: 19
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 0545ff40247b7ff86cb6227fa8cf4af8666c3629
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="best-practices-for-security-in-wcf"></a>Najlepsze rozwiązania dotyczące zabezpieczeń programu WCF
W poniższych sekcjach wymieniono najważniejsze wskazówki wziąć pod uwagę podczas tworzenia bezpiecznego aplikacji przy użyciu [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Aby uzyskać więcej informacji o zabezpieczeniach, zobacz [zagadnienia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md), [zagadnienia dotyczące zabezpieczeń dla danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md), i [zagadnienia dotyczące zabezpieczeń obejmujące metadane](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md).  
  
## <a name="identify-services-performing-windows-authentication-with-spns"></a>Identyfikacja usług uwierzytelniania systemu Windows na nazwy SPN  
 Usługi można określić nazwy głównej użytkownika (UPN) lub głównych nazw usług (SPN). Usługi uruchomiony w ramach konta komputera, na przykład usługi sieciowej mają tożsamością SPN odpowiadającego na komputerze, na którym jest na nich uruchomione. Usługi uruchomione na kontach użytkowników ma tożsamością UPN odpowiadający użytkownika nich uruchomiony, mimo że `setspn` narzędzia można przypisać nazwę SPN konta użytkownika. Konfigurowanie usługi, dzięki czemu można zidentyfikować za pomocą głównej nazwy usługi i konfigurowanie klientów połączenie z usługą, aby użyć tej nazwy SPN może upewnić się, ataki trudniejsze. Niniejsze wytyczne mają zastosowanie do wiązania za pomocą negocjowania protokołu Kerberos lub interfejs SSPI.  Klienci nadal należy określić nazwę SPN w przypadku, gdy SSPI powraca do uwierzytelniania NTLM.  
  
## <a name="verify-service-identities-in-wsdl"></a>Sprawdź tożsamości usługi w języku WSDL  
 WS-SecurityPolicy umożliwia usługom do publikowania informacji o własną tożsamość w metadanych. Po pobraniu przez `svcutil` lub innych metod, takich jak <xref:System.ServiceModel.Description.WsdlImporter>, informacje o tożsamości jest translacja do właściwości identity [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] adresy punktów końcowych usługi. Klientów, które sprawdza, czy te tożsamości usługi są poprawne i prawidłowe skutecznego obejścia uwierzytelniania usługi. Złośliwe usługi mogą wykorzystać takich klientów można wykonać przekazywania poświadczeń i innymi atakami "man w środku" przez zmianę tożsamości zastrzeżonego w WSDL.  
  
## <a name="use-x509-certificates-instead-of-ntlm"></a>Użyj X509 certyfikatów zamiast protokołu NTLM  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dostępne są dwa mechanizmy uwierzytelniania peer-to-peer: X509 certyfikatów (używanych przez kanał elementu równorzędnego) i uwierzytelniania systemu Windows, gdy negocjowanie interfejsu SSPI obniży z protokołu Kerberos do uwierzytelniania NTLM.  Uwierzytelnianie oparte na certyfikatach przy użyciu klucza rozmiary najmniej 1024 bity jest preferowana względem NTLM z kilku powodów:  
  
-   dostępność wzajemnego uwierzytelniania  
  
-   Użycie silniejszych algorytmów kryptograficznych, i  
  
-   X509 przekazywane większa trudności przy użyciu poświadczeń.  
  
 Omówienie uwierzytelniania NTLM przekazywania ataków, przejdź do [ http://msdn.microsoft.com/msdnmag/issues/06/09/SecureByDesign/default.aspx ](http://go.microsoft.com/fwlink/?LinkId=109571).  
  
## <a name="always-revert-after-impersonation"></a>Zawsze przywrócić po personifikacji  
 Podczas korzystania z interfejsów API, które umożliwiają personifikacja klienta, pamiętaj powrócić do oryginalnej tożsamości. Na przykład w przypadku korzystania z <xref:System.Security.Principal.WindowsIdentity> i <xref:System.Security.Principal.WindowsImpersonationContext>, użyj C# `using` instrukcji lub Visual Basic`Using` instrukcji, jak pokazano w poniższym kodzie. <xref:System.Security.Principal.WindowsImpersonationContext> Klasa implementuje <xref:System.IDisposable> interfejsu i dlatego środowisko uruchomieniowe języka wspólnego (CLR) automatycznie zostanie przywrócona do oryginalnego tożsamości po kodzie pozostawia `using` bloku.  
  
 [!code-csharp[c_SecurityBestPractices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securitybestpractices/cs/source.cs#1)]
 [!code-vb[c_SecurityBestPractices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securitybestpractices/vb/source.vb#1)]  
  
## <a name="impersonate-only-as-needed"></a>Tylko w razie potrzeby personifikacji  
 Przy użyciu <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metody <xref:System.Security.Principal.WindowsIdentity> klasa, jest możliwe w zakresie bardzo kontrolowane należy używać personifikacji. Dzięki temu nie trzeba przy użyciu <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> właściwość <xref:System.ServiceModel.OperationBehaviorAttribute>, co umożliwia personifikacji dla zakresu całej operacji. Jeśli to możliwe, za pomocą bardziej precyzyjne kontrolowanie zakresu personifikacji <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metody.  
  
## <a name="obtain-metadata-from-trusted-sources"></a>Uzyskiwanie metadanych z zaufanych źródeł  
 Upewnij się zaufania do źródła metadanych i upewnij się, że nikt nie został zmieniony przez niepowołane metadanych. Metadane pobrany przy użyciu protokołu HTTP są wysyłane w postaci zwykłego tekstu i może zostać naruszone. Jeśli usługa używa <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> i <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> właściwości, użyj adresu URL dostarczony przez autora usługi podczas pobierania danych przy użyciu protokołu HTTPS.  
  
## <a name="publish-metadata-using-security"></a>Publikowanie metadanych przy użyciu zabezpieczeń  
 Aby zapobiec modyfikowaniu z metadanymi opublikowane usługi, bezpieczny punkt końcowy wymiany metadanych z transportu lub zabezpieczenia na poziomie wiadomości. Aby uzyskać więcej informacji, zobacz [publikowanie punktów końcowych metadanych](../../../../docs/framework/wcf/publishing-metadata-endpoints.md) i [porady: Publikowanie metadanych dla kodu przy użyciu usługi](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
## <a name="ensure-use-of-local-issuer"></a>Upewnij się, Użyj wystawcy lokalnego  
 Jeśli adres wystawcy i powiązanie zostały określone dla danego powiązania, wystawcy lokalnego nie jest używany dla punktów końcowych, które używają tego powiązania. Klienci, którzy oczekują, że zawsze używaj wystawcy lokalnego powinien upewnij się, że nie używaj takiego powiązania lub ich zmodyfikuj powiązanie w taki sposób, że adres wystawcy jest pusta.  
  
## <a name="saml-token-size-quotas"></a>Przydziały rozmiar tokenu SAML  
 Gdy tokenów zabezpieczeń potwierdzenia Markup Language (SAML) są serializowane w wiadomości, wystawiane przez zabezpieczenia tokenu usługi (STS) lub, gdy klienci je do usług w ramach uwierzytelniania, maksymalny przydział rozmiaru komunikatu musi być wystarczająco duży, aby zmieścił się w tokenie SAML i innych części wiadomości. W przypadku normalnych przydziały rozmiar komunikatu domyślne są wystarczające. Jednak w przypadku, gdy tokenu SAML jest duży, ponieważ zawiera on setki oświadczenia, przydziały powinny być zwiększyć Zserializowany token. Aby uzyskać więcej informacji na temat przydziałów, zobacz [zagadnienia dotyczące zabezpieczeń dla danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## <a name="set-securitybindingelementincludetimestamp-to-true-on-custom-bindings"></a>Ustaw SecurityBindingElement.IncludeTimestamp wartość True na powiązania niestandardowe  
 Podczas tworzenia niestandardowego powiązania, należy ustawić <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> do `true`. W przeciwnym razie, jeśli <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> ma ustawioną wartość `false`, a klient używa asymetrycznego token opartego na kluczach, takich jak X509 certyfikatu, komunikat nie zostanie podpisana.  
  
## <a name="see-also"></a>Zobacz też  
 [Zagadnienia dotyczące bezpieczeństwa](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Zagadnienia związane z zabezpieczeniami danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 [Zagadnienia dotyczące zabezpieczeń obejmujące metadane](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
