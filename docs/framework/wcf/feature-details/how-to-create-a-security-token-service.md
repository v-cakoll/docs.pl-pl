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
ms.openlocfilehash: 5926216135429d235593aaf77ee0d29b0bacd8fa
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143912"
---
# <a name="how-to-create-a-security-token-service"></a><span data-ttu-id="4ef52-102">Instrukcje: Tworzenie usługi tokenów zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="4ef52-102">How to: Create a Security Token Service</span></span>
<span data-ttu-id="4ef52-103">Usługa tokenu zabezpieczającego implementuje protokół zdefiniowane w specyfikacji WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="4ef52-103">A security token service implements the protocol defined in the WS-Trust specification.</span></span> <span data-ttu-id="4ef52-104">Protokół ten definiuje formaty wiadomości i wzorców wymiany wiadomości dla wystawiającego certyfikaty, odnawiania, anulowanie i sprawdzanie poprawności tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="4ef52-104">This protocol defines message formats and message exchange patterns for issuing, renewing, canceling, and validating security tokens.</span></span> <span data-ttu-id="4ef52-105">Usługa tokenu zabezpieczającego danego zawiera co najmniej jedną z tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="4ef52-105">A given security token service provides one or more of these capabilities.</span></span> <span data-ttu-id="4ef52-106">W tym temacie wygląda najbardziej typowy scenariusz: Implementowanie wystawiania tokenu.</span><span class="sxs-lookup"><span data-stu-id="4ef52-106">This topic looks at the most common scenario: implementing token issuance.</span></span>  
  
## <a name="issuing-tokens"></a><span data-ttu-id="4ef52-107">Wystawianie tokenów</span><span class="sxs-lookup"><span data-stu-id="4ef52-107">Issuing Tokens</span></span>  
 <span data-ttu-id="4ef52-108">WS-Trust definiuje formaty wiadomości, w oparciu o `RequestSecurityToken` elementu schematu języka (XSD) definicji schematu XML, i `RequestSecurityTokenResponse` elementu schematu XSD do operacji wystawiania tokenów.</span><span class="sxs-lookup"><span data-stu-id="4ef52-108">WS-Trust defines message formats, based on the `RequestSecurityToken` XML Schema definition language (XSD) schema element, and `RequestSecurityTokenResponse` XSD schema element for performing token issuance.</span></span> <span data-ttu-id="4ef52-109">Ponadto definiuje skojarzonych akcji Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="4ef52-109">In addition, it defines the associated Action Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="4ef52-110">Akcja identyfikator URI skojarzony z `RequestSecurityToken` komunikat `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`.</span><span class="sxs-lookup"><span data-stu-id="4ef52-110">The action URI associated with the `RequestSecurityToken` message is `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`.</span></span> <span data-ttu-id="4ef52-111">Akcja identyfikator URI skojarzony z `RequestSecurityTokenResponse` komunikat `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`.</span><span class="sxs-lookup"><span data-stu-id="4ef52-111">The action URI associated with the `RequestSecurityTokenResponse` message is   `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`.</span></span>  
  
### <a name="request-message-structure"></a><span data-ttu-id="4ef52-112">Struktura komunikatu żądania</span><span class="sxs-lookup"><span data-stu-id="4ef52-112">Request Message Structure</span></span>  
 <span data-ttu-id="4ef52-113">Struktura komunikatu żądania problem zwykle składa się z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="4ef52-113">The issue request message structure typically consists of the following items:</span></span>  
  
-   <span data-ttu-id="4ef52-114">Żądanie wpisz identyfikator URI o wartości `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue`.</span><span class="sxs-lookup"><span data-stu-id="4ef52-114">A request type URI with a value of `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue`.</span></span>
  
-   <span data-ttu-id="4ef52-115">Typ tokenu identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="4ef52-115">A token type URI.</span></span> <span data-ttu-id="4ef52-116">Tokeny zabezpieczeń potwierdzenia Markup Language (SAML) 1.1, wartość tego identyfikatora URI jest `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.</span><span class="sxs-lookup"><span data-stu-id="4ef52-116">For Security Assertions Markup Language (SAML) 1.1 tokens, the value of this URI is `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.</span></span>  
  
-   <span data-ttu-id="4ef52-117">Wartość rozmiaru klucza, która wskazuje liczbę bitów w kluczu, który ma zostać skojarzony z wystawiony token.</span><span class="sxs-lookup"><span data-stu-id="4ef52-117">A key size value that indicates the number of bits in the key to be associated with the issued token.</span></span>  
  
-   <span data-ttu-id="4ef52-118">Typ klucza identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="4ef52-118">A key type URI.</span></span> <span data-ttu-id="4ef52-119">Klucze symetryczne, wartość tego identyfikatora URI jest `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="4ef52-119">For symmetric keys, the value of this URI is `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey`.</span></span>  
  
 <span data-ttu-id="4ef52-120">Ponadto kilka innych elementów mogą być obecne:</span><span class="sxs-lookup"><span data-stu-id="4ef52-120">In addition, a couple of other items might be present:</span></span>  
  
-   <span data-ttu-id="4ef52-121">Materiał klucza dostarczonych przez klienta.</span><span class="sxs-lookup"><span data-stu-id="4ef52-121">Key material provided by the client.</span></span>  
  
-   <span data-ttu-id="4ef52-122">Informacje o zakresie, który wskazuje Usługa docelowa, która wystawiony token będą używane z.</span><span class="sxs-lookup"><span data-stu-id="4ef52-122">Scope information that indicates the target service that the issued token will be used with.</span></span>  
  
 <span data-ttu-id="4ef52-123">Usługa tokenu zabezpieczającego używa tych informacji w komunikacie żądania problem podczas jego tworzy komunikat odpowiedzi na problem.</span><span class="sxs-lookup"><span data-stu-id="4ef52-123">The security token service uses the information in the issue request message when it constructs the Issue Response message.</span></span>  
  
## <a name="response-message-structure"></a><span data-ttu-id="4ef52-124">Struktura komunikat odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="4ef52-124">Response Message Structure</span></span>  
 <span data-ttu-id="4ef52-125">Struktura komunikat odpowiedzi problem zwykle składa się z następujących elementów;</span><span class="sxs-lookup"><span data-stu-id="4ef52-125">The issue response message structure typically consists of the following items;</span></span>  
  
-   <span data-ttu-id="4ef52-126">Token zabezpieczeń, na przykład potwierdzenia języka SAML 1.1.</span><span class="sxs-lookup"><span data-stu-id="4ef52-126">The issued security token, for example, a SAML 1.1 assertion.</span></span>  
  
-   <span data-ttu-id="4ef52-127">Token potwierdzenia skojarzone z tokenem zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="4ef52-127">A proof token associated with the security token.</span></span> <span data-ttu-id="4ef52-128">Dla kluczy symetrycznych to często zaszyfrowanej formie materiału klucza.</span><span class="sxs-lookup"><span data-stu-id="4ef52-128">For symmetric keys, this is often an encrypted form of the key material.</span></span>  
  
-   <span data-ttu-id="4ef52-129">Odwołania do tokenu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="4ef52-129">References to the issued security token.</span></span> <span data-ttu-id="4ef52-130">Zazwyczaj usługa tokenu zabezpieczającego zwraca odwołania, które mogą być używane podczas wystawiony token, który pojawia się w kolejnych wiadomością wysłaną przez klienta, a drugi, można użyć, gdy token nie znajduje się w kolejnych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4ef52-130">Typically, the security token service returns a reference that can be used when the issued token appears in a subsequent message sent by the client and another that can be used when the token is not present in subsequent messages.</span></span>  
  
 <span data-ttu-id="4ef52-131">Ponadto kilka innych elementów mogą być obecne:</span><span class="sxs-lookup"><span data-stu-id="4ef52-131">In addition, a couple of other items might be present:</span></span>  
  
-   <span data-ttu-id="4ef52-132">Materiał klucza, dostarczone przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="4ef52-132">Key material provided by the security token service.</span></span>  
  
-   <span data-ttu-id="4ef52-133">Algorytm potrzebnych do obliczenia klucza współużytkowanego.</span><span class="sxs-lookup"><span data-stu-id="4ef52-133">The algorithm needed to compute the shared key.</span></span>  
  
-   <span data-ttu-id="4ef52-134">Okres istnienia informacje dla wystawiony token.</span><span class="sxs-lookup"><span data-stu-id="4ef52-134">Lifetime information for the issued token.</span></span>  
  
## <a name="processing-request-messages"></a><span data-ttu-id="4ef52-135">Przetwarzanie komunikatów żądań</span><span class="sxs-lookup"><span data-stu-id="4ef52-135">Processing Request Messages</span></span>  
 <span data-ttu-id="4ef52-136">Usługa tokenu zabezpieczającego przetwarza żądanie problem, sprawdzając różnych rodzajów komunikatu żądania i zapewnienie, że może to wystawić tokenu, który spełnia żądanie.</span><span class="sxs-lookup"><span data-stu-id="4ef52-136">The security token service processes the issue request by examining the various pieces of the request message and ensuring that it can issue a token that satisfies the request.</span></span> <span data-ttu-id="4ef52-137">Przed jego tworzy token został wystawiony, usługę tokenu zabezpieczającego muszą określić następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4ef52-137">The security token service must determine the following before it constructs the token to be issued:</span></span>  
  
-   <span data-ttu-id="4ef52-138">Żądanie jest naprawdę żądania token został wystawiony.</span><span class="sxs-lookup"><span data-stu-id="4ef52-138">The request really is a request for a token to be issued.</span></span>  
  
-   <span data-ttu-id="4ef52-139">Usługa tokenu zabezpieczającego obsługuje żądanego typu tokenu.</span><span class="sxs-lookup"><span data-stu-id="4ef52-139">The security token service supports the requested token type.</span></span>  
  
-   <span data-ttu-id="4ef52-140">Żądający jest uprawniony do utworzenia żądania.</span><span class="sxs-lookup"><span data-stu-id="4ef52-140">The requester is authorized to make the request.</span></span>  
  
-   <span data-ttu-id="4ef52-141">Usługa tokenu zabezpieczającego można spełniają oczekiwań żądającego względem materiału klucza.</span><span class="sxs-lookup"><span data-stu-id="4ef52-141">The security token service can meet the requester's expectations with respect to key material.</span></span>  
  
 <span data-ttu-id="4ef52-142">Dwie kluczowe części konstruowanie token są określania, jakie klucza do podpisywania tokenu z i jakie klucz w celu zaszyfrowania klucza wstępnego za pomocą.</span><span class="sxs-lookup"><span data-stu-id="4ef52-142">Two vital parts of constructing a token are determining what key to sign the token with and what key to encrypt the shared key with.</span></span> <span data-ttu-id="4ef52-143">Token musi być podpisany, dzięki czemu gdy klient przedstawia token do docelowej usługi, że usługa może określić, że token został wystawiony przez usługę tokenu zabezpieczającego, które uzna.</span><span class="sxs-lookup"><span data-stu-id="4ef52-143">The token needs to be signed so that when the client presents the token to the target service, that service can determine that the token was issued by a security token service that it trusts.</span></span> <span data-ttu-id="4ef52-144">Materiał klucza musi być szyfrowane w taki sposób, że Usługa docelowa może odszyfrować tego materiału klucza.</span><span class="sxs-lookup"><span data-stu-id="4ef52-144">The key material needs to be encrypted in such a way that the target service can decrypt that key material.</span></span>  
  
 <span data-ttu-id="4ef52-145">Podpisywanie potwierdzenie SAML obejmuje utworzenie <xref:System.IdentityModel.Tokens.SigningCredentials> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4ef52-145">Signing a SAML assertion involves creating a <xref:System.IdentityModel.Tokens.SigningCredentials> instance.</span></span> <span data-ttu-id="4ef52-146">Konstruktor dla tej klasy wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4ef52-146">The constructor for this class takes the following:</span></span>  
  
-   <span data-ttu-id="4ef52-147">A <xref:System.IdentityModel.Tokens.SecurityKey> klucz używany do podpisywania dla asercji SAML.</span><span class="sxs-lookup"><span data-stu-id="4ef52-147">A <xref:System.IdentityModel.Tokens.SecurityKey> for the key to use to sign the SAML assertion.</span></span>  
  
-   <span data-ttu-id="4ef52-148">Ciąg identyfikujący algorytm podpisu, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="4ef52-148">A string identifying the signature algorithm to use.</span></span>  
  
-   <span data-ttu-id="4ef52-149">Ciąg identyfikujący algorytm tworzenia skrótu.</span><span class="sxs-lookup"><span data-stu-id="4ef52-149">A string identifying the digest algorithm to use.</span></span>  
  
-   <span data-ttu-id="4ef52-150">Opcjonalnie <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> określający klucz używany do podpisywania potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="4ef52-150">Optionally, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> that identifies the key to use to sign the assertion.</span></span>  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 <span data-ttu-id="4ef52-151">Szyfrowanie klucza wstępnego obejmuje pobranie materiału klucza i szyfruje za pomocą klucza usługi docelowej, można użyć do odszyfrowania klucza wstępnego.</span><span class="sxs-lookup"><span data-stu-id="4ef52-151">Encrypting the shared key involves taking the key material and encrypting it with a key that the target service can use to decrypt the shared key.</span></span> <span data-ttu-id="4ef52-152">Zazwyczaj jest używany klucz publiczny usługi docelowej.</span><span class="sxs-lookup"><span data-stu-id="4ef52-152">Typically, the public key of the target service is used.</span></span>  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 <span data-ttu-id="4ef52-153">Ponadto <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> dla zaszyfrowanego klucza jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="4ef52-153">In addition, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> for the encrypted key is needed.</span></span>  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 <span data-ttu-id="4ef52-154">To <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> jest następnie używany do tworzenia `SamlSubject` jako część `SamlToken`.</span><span class="sxs-lookup"><span data-stu-id="4ef52-154">This <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> is then used to create a `SamlSubject` as part of the `SamlToken`.</span></span>  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 <span data-ttu-id="4ef52-155">Aby uzyskać więcej informacji, zobacz [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="4ef52-155">For more information, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="creating-response-messages"></a><span data-ttu-id="4ef52-156">Tworzenie wiadomości odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="4ef52-156">Creating Response Messages</span></span>  
 <span data-ttu-id="4ef52-157">Gdy usługę tokenu zabezpieczającego przetwarza żądanie problemu i tworzy token wydaje się wraz z kluczem dowód, komunikat odpowiedzi powinno być zbudowane, w tym co najmniej żądanego tokenu, token potwierdzenia i wystawiony token odwołania.</span><span class="sxs-lookup"><span data-stu-id="4ef52-157">Once the security token service processes the issue request and constructs the token to be issued along with the proof key, the response message needs to be constructed, including at least the requested token, the proof token, and the issued token references.</span></span> <span data-ttu-id="4ef52-158">Wystawiony token jest zwykle <xref:System.IdentityModel.Tokens.SamlSecurityToken> utworzone na podstawie <xref:System.IdentityModel.Tokens.SamlAssertion>, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4ef52-158">The issued token is typically a <xref:System.IdentityModel.Tokens.SamlSecurityToken> created from the <xref:System.IdentityModel.Tokens.SamlAssertion>, as shown in the following example.</span></span>  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 <span data-ttu-id="4ef52-159">W przypadku których usługa tokenu zabezpieczającego obsługuje udostępnionego materiału klucza token potwierdzenia jest tworzony przez utworzenie <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span><span class="sxs-lookup"><span data-stu-id="4ef52-159">In the case where the security token service provides the shared key material, the proof token is constructed by creating a <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span></span>  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 <span data-ttu-id="4ef52-160">Aby uzyskać więcej informacji o tym, jak utworzyć token potwierdzenia, gdy klient i Usługa tokenu zabezpieczającego zawierają materiału klucza dla klucza współużytkowanego, zobacz [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="4ef52-160">For more information about how to construct the proof token when the client and the security token service both provide key material for the shared key, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
 <span data-ttu-id="4ef52-161">Wystawiony token odwołania są tworzone przez utworzenie wystąpienia <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> klasy.</span><span class="sxs-lookup"><span data-stu-id="4ef52-161">The issued token references are constructed by creating instances of the <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> class.</span></span>  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 <span data-ttu-id="4ef52-162">Te różne wartości są następnie serializowany w komunikat odpowiedzi zwracany do klienta.</span><span class="sxs-lookup"><span data-stu-id="4ef52-162">These various values are then serialized into the response message returned to the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ef52-163">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ef52-163">Example</span></span>  
 <span data-ttu-id="4ef52-164">Pełny kod dla usługi tokenu zabezpieczającego, zobacz [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="4ef52-164">For full code for a security token service, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ef52-165">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ef52-165">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SigningCredentials>  
 <xref:System.IdentityModel.Tokens.SecurityKey>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
 <xref:System.IdentityModel.Tokens.SamlAssertion>  
 <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>  
 [<span data-ttu-id="4ef52-166">Federacja — przykład</span><span class="sxs-lookup"><span data-stu-id="4ef52-166">Federation Sample</span></span>](../../../../docs/framework/wcf/samples/federation-sample.md)
