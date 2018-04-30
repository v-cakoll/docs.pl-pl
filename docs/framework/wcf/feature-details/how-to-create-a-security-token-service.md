---
title: 'Instrukcje: Tworzenie usługi tokenów zabezpieczeń'
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
- WCF, federation
- federation
ms.assetid: 98e82101-4cff-4bb8-a220-f7abed3556e5
caps.latest.revision: 12
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 827fef90a6277387ceac1c8f1d6df00a69a5d612
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-a-security-token-service"></a>Instrukcje: Tworzenie usługi tokenów zabezpieczeń
Usługa tokenu zabezpieczającego implementuje ten protokół zdefiniowane w specyfikacji WS-Trust. Ten protokół definiuje formaty wiadomości i wzorce wymiany wiadomości dla wystawiającego certyfikaty, odnowienie, anulowanie i sprawdzania poprawności tokenów zabezpieczających. Usługi tokenu zabezpieczeń zawiera co najmniej jednego z tych funkcji. W tym temacie wygląda najbardziej typowy scenariusz: Implementowanie wydawania tokenów.  
  
## <a name="issuing-tokens"></a>Wystawianie tokenów  
 WS-Trust definiuje formaty wiadomości, na podstawie `RequestSecurityToken` schematu XML definition language (XSD) schematu elementu i `RequestSecurityTokenResponse` elementu schematu XSD do wykonywania wydawania tokenów. Ponadto definiuje skojarzonych akcji Uniform Resource Identifier (URI). Identyfikator URI skojarzony z akcji `RequestSecurityToken` komunikat http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue. Identyfikator URI skojarzony z akcji `RequestSecurityTokenResponse` komunikat http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue.  
  
### <a name="request-message-structure"></a>Struktura komunikatu żądania  
 Struktura komunikatu żądania problem zwykle składa się z następujących elementów:  
  
-   Żądanie wpisz identyfikator URI przy użyciu wartości http://schemas.xmlsoap.org/ws/2005/02/trust/Issue.  
  
-   Typ tokenu identyfikatora URI. Wartość tego identyfikatora URI dla tokenów zabezpieczeń potwierdzenia Markup Language (SAML) 1.1 jest http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1.  
  
-   Wartość rozmiaru klucza, która wskazuje liczba bitów klucza, który ma być skojarzona z wystawionego tokenu.  
  
-   Typ klucza identyfikatora URI. Wartość tego identyfikatora URI dla kluczy symetrycznych jest http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey.  
  
 Ponadto kilka innych elementów mogą być obecne:  
  
-   Materiał klucza dostarczonych przez klienta.  
  
-   Zakres informacji, która wskazuje usługę obiektu docelowego, który będzie używany wystawionego tokenu z.  
  
 Usługa tokenu zabezpieczającego informacje są używane w komunikacie żądania problem podczas jego tworzy komunikat odpowiedzi problem.  
  
## <a name="response-message-structure"></a>Struktura komunikatu odpowiedzi  
 Struktura komunikat odpowiedzi problem zwykle składa się z następujących elementów;  
  
-   Token zabezpieczeń, na przykład potwierdzenia języka SAML 1.1.  
  
-   Token potwierdzenia skojarzone z tokenu zabezpieczającego. Dla kluczy symetrycznych jest to często zaszyfrowane materiału klucza.  
  
-   Odwołania do tokenu zabezpieczeń. Zazwyczaj usługa tokenu zabezpieczającego zwraca odwołanie, którego można użyć w przypadku wystawiony token pojawia się w kolejnych komunikat wysyłany przez klienta i inny można użyć w przypadku token nie znajduje się w kolejnych komunikatów.  
  
 Ponadto kilka innych elementów mogą być obecne:  
  
-   Materiał klucza dostarczonych przez usługę tokenu zabezpieczającego.  
  
-   Algorytm niezbędne do obliczenia klucza wspólnego.  
  
-   Informacje okres istnienia wystawionego tokenu.  
  
## <a name="processing-request-messages"></a>Przetwarzanie komunikatów żądań  
 Usługa tokenu zabezpieczającego przetwarza żądanie problem, sprawdzając różnych części komunikatu żądania i zapewnienie, że mogą wystawiać token, który spełnia żądania. Usługa tokenu zabezpieczającego muszą określić następujące przed jego tworzy token został wystawiony:  
  
-   Żądanie jest naprawdę token zostanie wysłane żądanie.  
  
-   Usługa tokenu zabezpieczającego obsługuje żądanego typu tokenu.  
  
-   Żądający ma autoryzacji do zgłoszenia żądania.  
  
-   Usługa tokenu zabezpieczającego można spełniają oczekiwań żądającego względem materiału klucza.  
  
 Dwie najważniejsze części tworzenia tokenu są określanie, jakie klucza do podpisywania tokenu z i jakie klucza do szyfrowania klucza wspólnego z. Token musi być podpisany, dzięki czemu podczas Klient przedstawia token do usługi docelowej, że usługa może określić, że token został wystawiony przez usługę tokenu zabezpieczającego zaufaną. Materiał klucza musi być szyfrowane w taki sposób, że Usługa docelowa może odszyfrować materiału klucza.  
  
 Podpisywanie potwierdzenia języka SAML obejmuje utworzenie <xref:System.IdentityModel.Tokens.SigningCredentials> wystąpienia. Konstruktor dla tej klasy wykonuje następujące czynności:  
  
-   A <xref:System.IdentityModel.Tokens.SecurityKey> klucza użycia potwierdzenia języka SAML logowania.  
  
-   Ciąg identyfikujący algorytm podpisu, który ma być używany.  
  
-   Ciąg identyfikujący algorytm skrótu używany.  
  
-   Opcjonalnie <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> identyfikującym klucz do podpisania potwierdzenia.  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 Szyfrowanie klucza wspólnego obejmuje biorąc materiału klucza i ich szyfrowanie za pomocą klucza usługi docelowej można użyć do odszyfrowania klucza wspólnego. Zazwyczaj jest używany klucz publiczny usługi docelowej.  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 Ponadto <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> dla zaszyfrowanego klucza jest wymagana.  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 To <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> jest następnie używany do tworzenia `SamlSubject` jako część `SamlToken`.  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 Aby uzyskać więcej informacji, zobacz [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="creating-response-messages"></a>Tworzenie wiadomości odpowiedzi  
 Po usługi tokenu zabezpieczającego przetwarza żądanie problemu i tworzy token zostanie wysłane oraz klucza potwierdzającego, komunikat odpowiedzi musi zostać utworzone, zawierające co najmniej żądanego tokenu, token potwierdzenia i wystawionego tokenu odwołania. Wystawiony token jest zwykle <xref:System.IdentityModel.Tokens.SamlSecurityToken> utworzone na podstawie <xref:System.IdentityModel.Tokens.SamlAssertion>, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 W przypadku których usługi tokenu zabezpieczającego zawiera udostępnionego materiału klucza token potwierdzenia jest tworzony przez utworzenie <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 Aby uzyskać więcej informacji dotyczących sposobu tworzenia token potwierdzenia, gdy klient i Usługa tokenu zabezpieczającego zawierają materiału klucza dla klucza udostępnionego, zobacz [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
 Wystawiony token odwołania są wykonane przez utworzenie wystąpienia <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> klasy.  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 Te wartości różnych są następnie zserializowane do komunikat odpowiedzi zwracany do klienta.  
  
## <a name="example"></a>Przykład  
 Aby uzyskać pełny kod dla usługi tokenu zabezpieczającego, zobacz [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Tokens.SigningCredentials>  
 <xref:System.IdentityModel.Tokens.SecurityKey>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
 <xref:System.IdentityModel.Tokens.SamlAssertion>  
 <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>  
 [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md)
