---
title: 'Instrukcje: Tworzenie usługi tokenów zabezpieczeń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 98e82101-4cff-4bb8-a220-f7abed3556e5
author: BrucePerlerMS
ms.openlocfilehash: dd2c4f32978107a82ce940e0ef984c70f461b2c3
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48046738"
---
# <a name="how-to-create-a-security-token-service"></a>Instrukcje: Tworzenie usługi tokenów zabezpieczeń
Usługa tokenu zabezpieczającego implementuje protokół zdefiniowane w specyfikacji WS-Trust. Protokół ten definiuje formaty wiadomości i wzorców wymiany wiadomości dla wystawiającego certyfikaty, odnawiania, anulowanie i sprawdzanie poprawności tokenów zabezpieczających. Usługa tokenu zabezpieczającego danego zawiera co najmniej jedną z tych funkcji. W tym temacie wygląda najbardziej typowy scenariusz: Implementowanie wystawiania tokenu.  
  
## <a name="issuing-tokens"></a>Wystawianie tokenów  
 WS-Trust definiuje formaty wiadomości, w oparciu o `RequestSecurityToken` elementu schematu języka (XSD) definicji schematu XML, i `RequestSecurityTokenResponse` elementu schematu XSD do operacji wystawiania tokenów. Ponadto definiuje skojarzonych akcji Uniform Resource Identifier (URI). Akcja identyfikator URI skojarzony z `RequestSecurityToken` komunikat http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue. Akcja identyfikator URI skojarzony z `RequestSecurityTokenResponse` komunikat http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue.  
  
### <a name="request-message-structure"></a>Struktura komunikatu żądania  
 Struktura komunikatu żądania problem zwykle składa się z następujących elementów:  
  
-   Żądanie wpisz identyfikator URI o wartości http://schemas.xmlsoap.org/ws/2005/02/trust/Issue.  
  
-   Typ tokenu identyfikatora URI. Tokeny zabezpieczeń potwierdzenia Markup Language (SAML) 1.1, wartość tego identyfikatora URI jest http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1.  
  
-   Wartość rozmiaru klucza, która wskazuje liczbę bitów w kluczu, który ma zostać skojarzony z wystawiony token.  
  
-   Typ klucza identyfikatora URI. Klucze symetryczne, wartość tego identyfikatora URI jest http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey.  
  
 Ponadto kilka innych elementów mogą być obecne:  
  
-   Materiał klucza dostarczonych przez klienta.  
  
-   Informacje o zakresie, który wskazuje Usługa docelowa, która wystawiony token będą używane z.  
  
 Usługa tokenu zabezpieczającego używa tych informacji w komunikacie żądania problem podczas jego tworzy komunikat odpowiedzi na problem.  
  
## <a name="response-message-structure"></a>Struktura komunikat odpowiedzi  
 Struktura komunikat odpowiedzi problem zwykle składa się z następujących elementów;  
  
-   Token zabezpieczeń, na przykład potwierdzenia języka SAML 1.1.  
  
-   Token potwierdzenia skojarzone z tokenem zabezpieczeń. Dla kluczy symetrycznych to często zaszyfrowanej formie materiału klucza.  
  
-   Odwołania do tokenu zabezpieczeń. Zazwyczaj usługa tokenu zabezpieczającego zwraca odwołania, które mogą być używane podczas wystawiony token, który pojawia się w kolejnych wiadomością wysłaną przez klienta, a drugi, można użyć, gdy token nie znajduje się w kolejnych komunikatów.  
  
 Ponadto kilka innych elementów mogą być obecne:  
  
-   Materiał klucza, dostarczone przez usługę tokenu zabezpieczającego.  
  
-   Algorytm potrzebnych do obliczenia klucza współużytkowanego.  
  
-   Okres istnienia informacje dla wystawiony token.  
  
## <a name="processing-request-messages"></a>Przetwarzanie komunikatów żądań  
 Usługa tokenu zabezpieczającego przetwarza żądanie problem, sprawdzając różnych rodzajów komunikatu żądania i zapewnienie, że może to wystawić tokenu, który spełnia żądanie. Przed jego tworzy token został wystawiony, usługę tokenu zabezpieczającego muszą określić następujące czynności:  
  
-   Żądanie jest naprawdę żądania token został wystawiony.  
  
-   Usługa tokenu zabezpieczającego obsługuje żądanego typu tokenu.  
  
-   Żądający jest uprawniony do utworzenia żądania.  
  
-   Usługa tokenu zabezpieczającego można spełniają oczekiwań żądającego względem materiału klucza.  
  
 Dwie kluczowe części konstruowanie token są określania, jakie klucza do podpisywania tokenu z i jakie klucz w celu zaszyfrowania klucza wstępnego za pomocą. Token musi być podpisany, dzięki czemu gdy klient przedstawia token do docelowej usługi, że usługa może określić, że token został wystawiony przez usługę tokenu zabezpieczającego, które uzna. Materiał klucza musi być szyfrowane w taki sposób, że Usługa docelowa może odszyfrować tego materiału klucza.  
  
 Podpisywanie potwierdzenie SAML obejmuje utworzenie <xref:System.IdentityModel.Tokens.SigningCredentials> wystąpienia. Konstruktor dla tej klasy wykonuje następujące czynności:  
  
-   A <xref:System.IdentityModel.Tokens.SecurityKey> klucz używany do podpisywania dla asercji SAML.  
  
-   Ciąg identyfikujący algorytm podpisu, który ma być używany.  
  
-   Ciąg identyfikujący algorytm tworzenia skrótu.  
  
-   Opcjonalnie <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> określający klucz używany do podpisywania potwierdzenia.  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 Szyfrowanie klucza wstępnego obejmuje pobranie materiału klucza i szyfruje za pomocą klucza usługi docelowej, można użyć do odszyfrowania klucza wstępnego. Zazwyczaj jest używany klucz publiczny usługi docelowej.  
  
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
 Gdy usługę tokenu zabezpieczającego przetwarza żądanie problemu i tworzy token wydaje się wraz z kluczem dowód, komunikat odpowiedzi powinno być zbudowane, w tym co najmniej żądanego tokenu, token potwierdzenia i wystawiony token odwołania. Wystawiony token jest zwykle <xref:System.IdentityModel.Tokens.SamlSecurityToken> utworzone na podstawie <xref:System.IdentityModel.Tokens.SamlAssertion>, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 W przypadku których usługa tokenu zabezpieczającego obsługuje udostępnionego materiału klucza token potwierdzenia jest tworzony przez utworzenie <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 Aby uzyskać więcej informacji o tym, jak utworzyć token potwierdzenia, gdy klient i Usługa tokenu zabezpieczającego zawierają materiału klucza dla klucza współużytkowanego, zobacz [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
 Wystawiony token odwołania są tworzone przez utworzenie wystąpienia <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> klasy.  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 Te różne wartości są następnie serializowany w komunikat odpowiedzi zwracany do klienta.  
  
## <a name="example"></a>Przykład  
 Pełny kod dla usługi tokenu zabezpieczającego, zobacz [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Tokens.SigningCredentials>  
 <xref:System.IdentityModel.Tokens.SecurityKey>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
 <xref:System.IdentityModel.Tokens.SamlAssertion>  
 <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>  
 [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md)
