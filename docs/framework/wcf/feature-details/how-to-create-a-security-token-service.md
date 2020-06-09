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
ms.openlocfilehash: 1cfcca524e5dd2b0c1560eb7600795766e2db1d6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598960"
---
# <a name="how-to-create-a-security-token-service"></a>Instrukcje: Tworzenie usługi tokenów zabezpieczeń
Usługa tokenu zabezpieczającego implementuje protokół zdefiniowany w specyfikacji WS-Trust. Ten protokół definiuje formaty komunikatów i wzorce wymiany komunikatów na potrzeby wydawania, odnawiania, anulowania i weryfikowania tokenów zabezpieczających. Dana usługa tokenów zabezpieczających udostępnia co najmniej jedną z tych możliwości. Ten temat sprawdza się w najbardziej typowym scenariuszu: implementowanie wystawiania tokenów.  
  
## <a name="issuing-tokens"></a>Wystawianie tokenów  
 Usługa WS-Trust definiuje formaty komunikatów na podstawie `RequestSecurityToken` elementu schematu definicji schematu XML (XSD) i `RequestSecurityTokenResponse` elementu schematu XSD do wykonywania wystawiania tokenów. Ponadto definiuje skojarzone identyfikatory URI (Uniform Resource Identifier) akcji. Identyfikator URI akcji skojarzony z `RequestSecurityToken` komunikatem to `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue` . Identyfikator URI akcji skojarzony z `RequestSecurityTokenResponse` komunikatem to `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue` .  
  
### <a name="request-message-structure"></a>Struktura komunikatu żądania  
 Struktura komunikatów żądania problemu zwykle składa się z następujących elementów:  
  
- Identyfikator URI typu żądania o wartości `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue` .
  
- Identyfikator URI typu tokenu. Dla tokenów Security Assertions Language (SAML) 1,1, wartość tego identyfikatora URI to `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` .  
  
- Wartość rozmiaru klucza wskazująca liczbę bitów w kluczu, która ma zostać skojarzona z wystawionym tokenem.  
  
- Identyfikator URI typu klucza. W przypadku kluczy symetrycznych wartością tego identyfikatora URI jest `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey` .  
  
 Ponadto może być obecne kilka innych elementów:  
  
- Materiał klucza dostarczany przez klienta.  
  
- Informacje o zakresie wskazujące usługę docelową, z którą będzie korzystać wystawiony token.  
  
 Usługa tokenu zabezpieczającego używa informacji w komunikacie żądania problemu, gdy konstruuje komunikat odpowiedzi na problem.  
  
## <a name="response-message-structure"></a>Struktura komunikatu odpowiedzi  
 Struktura komunikatów o problemie z odpowiedzią zwykle składa się z następujących elementów:  
  
- Wystawiony token zabezpieczający, na przykład potwierdzenie SAML 1,1.  
  
- Token potwierdzający skojarzony z tokenem zabezpieczającym. W przypadku kluczy symetrycznych jest to często zaszyfrowana postać materiału kluczowego.  
  
- Odwołania do wystawionego tokenu zabezpieczeń. Zazwyczaj usługa tokenu zabezpieczającego zwraca odwołanie, które może być używane, gdy wystawiony token pojawia się w kolejnym komunikacie wysyłanym przez klienta i innym, który może być używany, gdy token nie jest obecny w kolejnych komunikatach.  
  
 Ponadto może być obecne kilka innych elementów:  
  
- Materiał klucza dostarczany przez usługę tokenu zabezpieczającego.  
  
- Algorytm wymagany do obliczenia klucza współużytkowanego.  
  
- Informacje o okresie istnienia wystawionego tokenu.  
  
## <a name="processing-request-messages"></a>Przetwarzanie komunikatów żądań  
 Usługa tokenu zabezpieczającego przetwarza żądanie problemu, sprawdzając różne fragmenty komunikatu żądania i upewniając się, że może wydać token, który spełnia żądanie. Aby można było wystawić token, usługa tokenu zabezpieczającego musi określić następujące elementy:  
  
- Żądanie naprawdę jest żądaniem wystawienia tokenu.  
  
- Usługa tokenu zabezpieczającego obsługuje żądany typ tokenu.  
  
- Obiekt żądający ma autoryzację w celu zgłoszenia żądania.  
  
- Usługa tokenu zabezpieczającego może spełnić oczekiwania żądającego w odniesieniu do materiału klucza.  
  
 Dwie istotne części konstruowania tokenu okreolają klucz, w którym ma być podpisywany token, oraz klucz, w którym ma być zaszyfrowany klucz współużytkowany. Token musi być podpisany, aby podczas gdy klient przedstawia token dla usługi docelowej, usługa ta może ustalić, czy token został wystawiony przez usługę tokenu zabezpieczającego, która jest zaufana. Materiał klucza musi być zaszyfrowany w taki sposób, że usługa docelowa może odszyfrować ten materiał klucza.  
  
 Podpisywanie potwierdzenia SAML obejmuje tworzenie <xref:System.IdentityModel.Tokens.SigningCredentials> wystąpienia. Konstruktor dla tej klasy wykonuje następujące czynności:  
  
- A <xref:System.IdentityModel.Tokens.SecurityKey> dla klucza używanego do podpisywania potwierdzenia SAML.  
  
- Ciąg identyfikujący algorytm podpisu, który ma być używany.  
  
- Ciąg identyfikujący algorytm szyfrowania, który ma być używany.  
  
- Opcjonalnie, <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> który identyfikuje klucz do użycia w celu podpisania potwierdzenia.  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 Szyfrowanie klucza współużytkowanego obejmuje pobranie materiału klucza i zaszyfrowanie go za pomocą klucza, którego usługa docelowa może użyć do odszyfrowania klucza współużytkowanego. Zazwyczaj używany jest klucz publiczny usługi docelowej.  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 Ponadto <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> wymagany jest klucz szyfrowania klucza.  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>Jest on następnie używany do tworzenia `SamlSubject` jako część elementu `SamlToken` .  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 Aby uzyskać więcej informacji, zobacz [przykład Federacji](../samples/federation-sample.md).  
  
## <a name="creating-response-messages"></a>Tworzenie komunikatów odpowiedzi  
 Gdy usługa tokenu zabezpieczeń przetwarza żądanie problemu i konstruuje token, który ma zostać wystawiony wraz z kluczem testowym, należy skonstruować komunikat odpowiedzi, w tym co najmniej żądany token, token potwierdzający oraz odwołania do wystawionych tokenów. Wystawiony token jest zwykle <xref:System.IdentityModel.Tokens.SamlSecurityToken> tworzony przy użyciu <xref:System.IdentityModel.Tokens.SamlAssertion> , jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 W przypadku, gdy usługa tokenu zabezpieczającego udostępnia materiał klucza wspólnego, token potwierdzający jest konstruowany przez utworzenie <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken> .  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 Aby uzyskać więcej informacji o sposobie konstruowania tokenu sprawdzającego, gdy klient i usługa tokenu zabezpieczającego zapewniają kluczowy materiał dla klucza współużytkowanego, zobacz [przykład Federacji](../samples/federation-sample.md).  
  
 Odwołania do wystawionych tokenów są tworzone przez tworzenie wystąpień <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> klasy.  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 Te różne wartości są następnie serializowane do komunikatu odpowiedzi zwróconego do klienta.  
  
## <a name="example"></a>Przykład  
 Aby uzyskać pełny kod dla usługi tokenu zabezpieczającego, zobacz [przykład Federacji](../samples/federation-sample.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IdentityModel.Tokens.SigningCredentials>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>
- <xref:System.IdentityModel.Tokens.SamlSecurityToken>
- <xref:System.IdentityModel.Tokens.SamlAssertion>
- <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>
- [Federacja — przykład](../samples/federation-sample.md)
