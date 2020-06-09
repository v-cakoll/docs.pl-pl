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
# <a name="how-to-create-a-security-token-service"></a><span data-ttu-id="5a513-102">Instrukcje: Tworzenie usługi tokenów zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="5a513-102">How to: Create a Security Token Service</span></span>
<span data-ttu-id="5a513-103">Usługa tokenu zabezpieczającego implementuje protokół zdefiniowany w specyfikacji WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="5a513-103">A security token service implements the protocol defined in the WS-Trust specification.</span></span> <span data-ttu-id="5a513-104">Ten protokół definiuje formaty komunikatów i wzorce wymiany komunikatów na potrzeby wydawania, odnawiania, anulowania i weryfikowania tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="5a513-104">This protocol defines message formats and message exchange patterns for issuing, renewing, canceling, and validating security tokens.</span></span> <span data-ttu-id="5a513-105">Dana usługa tokenów zabezpieczających udostępnia co najmniej jedną z tych możliwości.</span><span class="sxs-lookup"><span data-stu-id="5a513-105">A given security token service provides one or more of these capabilities.</span></span> <span data-ttu-id="5a513-106">Ten temat sprawdza się w najbardziej typowym scenariuszu: implementowanie wystawiania tokenów.</span><span class="sxs-lookup"><span data-stu-id="5a513-106">This topic looks at the most common scenario: implementing token issuance.</span></span>  
  
## <a name="issuing-tokens"></a><span data-ttu-id="5a513-107">Wystawianie tokenów</span><span class="sxs-lookup"><span data-stu-id="5a513-107">Issuing Tokens</span></span>  
 <span data-ttu-id="5a513-108">Usługa WS-Trust definiuje formaty komunikatów na podstawie `RequestSecurityToken` elementu schematu definicji schematu XML (XSD) i `RequestSecurityTokenResponse` elementu schematu XSD do wykonywania wystawiania tokenów.</span><span class="sxs-lookup"><span data-stu-id="5a513-108">WS-Trust defines message formats, based on the `RequestSecurityToken` XML Schema definition language (XSD) schema element, and `RequestSecurityTokenResponse` XSD schema element for performing token issuance.</span></span> <span data-ttu-id="5a513-109">Ponadto definiuje skojarzone identyfikatory URI (Uniform Resource Identifier) akcji.</span><span class="sxs-lookup"><span data-stu-id="5a513-109">In addition, it defines the associated Action Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="5a513-110">Identyfikator URI akcji skojarzony z `RequestSecurityToken` komunikatem to `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue` .</span><span class="sxs-lookup"><span data-stu-id="5a513-110">The action URI associated with the `RequestSecurityToken` message is `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`.</span></span> <span data-ttu-id="5a513-111">Identyfikator URI akcji skojarzony z `RequestSecurityTokenResponse` komunikatem to `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue` .</span><span class="sxs-lookup"><span data-stu-id="5a513-111">The action URI associated with the `RequestSecurityTokenResponse` message is   `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`.</span></span>  
  
### <a name="request-message-structure"></a><span data-ttu-id="5a513-112">Struktura komunikatu żądania</span><span class="sxs-lookup"><span data-stu-id="5a513-112">Request Message Structure</span></span>  
 <span data-ttu-id="5a513-113">Struktura komunikatów żądania problemu zwykle składa się z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="5a513-113">The issue request message structure typically consists of the following items:</span></span>  
  
- <span data-ttu-id="5a513-114">Identyfikator URI typu żądania o wartości `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue` .</span><span class="sxs-lookup"><span data-stu-id="5a513-114">A request type URI with a value of `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue`.</span></span>
  
- <span data-ttu-id="5a513-115">Identyfikator URI typu tokenu.</span><span class="sxs-lookup"><span data-stu-id="5a513-115">A token type URI.</span></span> <span data-ttu-id="5a513-116">Dla tokenów Security Assertions Language (SAML) 1,1, wartość tego identyfikatora URI to `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` .</span><span class="sxs-lookup"><span data-stu-id="5a513-116">For Security Assertions Markup Language (SAML) 1.1 tokens, the value of this URI is `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.</span></span>  
  
- <span data-ttu-id="5a513-117">Wartość rozmiaru klucza wskazująca liczbę bitów w kluczu, która ma zostać skojarzona z wystawionym tokenem.</span><span class="sxs-lookup"><span data-stu-id="5a513-117">A key size value that indicates the number of bits in the key to be associated with the issued token.</span></span>  
  
- <span data-ttu-id="5a513-118">Identyfikator URI typu klucza.</span><span class="sxs-lookup"><span data-stu-id="5a513-118">A key type URI.</span></span> <span data-ttu-id="5a513-119">W przypadku kluczy symetrycznych wartością tego identyfikatora URI jest `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey` .</span><span class="sxs-lookup"><span data-stu-id="5a513-119">For symmetric keys, the value of this URI is `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey`.</span></span>  
  
 <span data-ttu-id="5a513-120">Ponadto może być obecne kilka innych elementów:</span><span class="sxs-lookup"><span data-stu-id="5a513-120">In addition, a couple of other items might be present:</span></span>  
  
- <span data-ttu-id="5a513-121">Materiał klucza dostarczany przez klienta.</span><span class="sxs-lookup"><span data-stu-id="5a513-121">Key material provided by the client.</span></span>  
  
- <span data-ttu-id="5a513-122">Informacje o zakresie wskazujące usługę docelową, z którą będzie korzystać wystawiony token.</span><span class="sxs-lookup"><span data-stu-id="5a513-122">Scope information that indicates the target service that the issued token will be used with.</span></span>  
  
 <span data-ttu-id="5a513-123">Usługa tokenu zabezpieczającego używa informacji w komunikacie żądania problemu, gdy konstruuje komunikat odpowiedzi na problem.</span><span class="sxs-lookup"><span data-stu-id="5a513-123">The security token service uses the information in the issue request message when it constructs the Issue Response message.</span></span>  
  
## <a name="response-message-structure"></a><span data-ttu-id="5a513-124">Struktura komunikatu odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="5a513-124">Response Message Structure</span></span>  
 <span data-ttu-id="5a513-125">Struktura komunikatów o problemie z odpowiedzią zwykle składa się z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="5a513-125">The issue response message structure typically consists of the following items;</span></span>  
  
- <span data-ttu-id="5a513-126">Wystawiony token zabezpieczający, na przykład potwierdzenie SAML 1,1.</span><span class="sxs-lookup"><span data-stu-id="5a513-126">The issued security token, for example, a SAML 1.1 assertion.</span></span>  
  
- <span data-ttu-id="5a513-127">Token potwierdzający skojarzony z tokenem zabezpieczającym.</span><span class="sxs-lookup"><span data-stu-id="5a513-127">A proof token associated with the security token.</span></span> <span data-ttu-id="5a513-128">W przypadku kluczy symetrycznych jest to często zaszyfrowana postać materiału kluczowego.</span><span class="sxs-lookup"><span data-stu-id="5a513-128">For symmetric keys, this is often an encrypted form of the key material.</span></span>  
  
- <span data-ttu-id="5a513-129">Odwołania do wystawionego tokenu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5a513-129">References to the issued security token.</span></span> <span data-ttu-id="5a513-130">Zazwyczaj usługa tokenu zabezpieczającego zwraca odwołanie, które może być używane, gdy wystawiony token pojawia się w kolejnym komunikacie wysyłanym przez klienta i innym, który może być używany, gdy token nie jest obecny w kolejnych komunikatach.</span><span class="sxs-lookup"><span data-stu-id="5a513-130">Typically, the security token service returns a reference that can be used when the issued token appears in a subsequent message sent by the client and another that can be used when the token is not present in subsequent messages.</span></span>  
  
 <span data-ttu-id="5a513-131">Ponadto może być obecne kilka innych elementów:</span><span class="sxs-lookup"><span data-stu-id="5a513-131">In addition, a couple of other items might be present:</span></span>  
  
- <span data-ttu-id="5a513-132">Materiał klucza dostarczany przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="5a513-132">Key material provided by the security token service.</span></span>  
  
- <span data-ttu-id="5a513-133">Algorytm wymagany do obliczenia klucza współużytkowanego.</span><span class="sxs-lookup"><span data-stu-id="5a513-133">The algorithm needed to compute the shared key.</span></span>  
  
- <span data-ttu-id="5a513-134">Informacje o okresie istnienia wystawionego tokenu.</span><span class="sxs-lookup"><span data-stu-id="5a513-134">Lifetime information for the issued token.</span></span>  
  
## <a name="processing-request-messages"></a><span data-ttu-id="5a513-135">Przetwarzanie komunikatów żądań</span><span class="sxs-lookup"><span data-stu-id="5a513-135">Processing Request Messages</span></span>  
 <span data-ttu-id="5a513-136">Usługa tokenu zabezpieczającego przetwarza żądanie problemu, sprawdzając różne fragmenty komunikatu żądania i upewniając się, że może wydać token, który spełnia żądanie.</span><span class="sxs-lookup"><span data-stu-id="5a513-136">The security token service processes the issue request by examining the various pieces of the request message and ensuring that it can issue a token that satisfies the request.</span></span> <span data-ttu-id="5a513-137">Aby można było wystawić token, usługa tokenu zabezpieczającego musi określić następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="5a513-137">The security token service must determine the following before it constructs the token to be issued:</span></span>  
  
- <span data-ttu-id="5a513-138">Żądanie naprawdę jest żądaniem wystawienia tokenu.</span><span class="sxs-lookup"><span data-stu-id="5a513-138">The request really is a request for a token to be issued.</span></span>  
  
- <span data-ttu-id="5a513-139">Usługa tokenu zabezpieczającego obsługuje żądany typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="5a513-139">The security token service supports the requested token type.</span></span>  
  
- <span data-ttu-id="5a513-140">Obiekt żądający ma autoryzację w celu zgłoszenia żądania.</span><span class="sxs-lookup"><span data-stu-id="5a513-140">The requester is authorized to make the request.</span></span>  
  
- <span data-ttu-id="5a513-141">Usługa tokenu zabezpieczającego może spełnić oczekiwania żądającego w odniesieniu do materiału klucza.</span><span class="sxs-lookup"><span data-stu-id="5a513-141">The security token service can meet the requester's expectations with respect to key material.</span></span>  
  
 <span data-ttu-id="5a513-142">Dwie istotne części konstruowania tokenu okreolają klucz, w którym ma być podpisywany token, oraz klucz, w którym ma być zaszyfrowany klucz współużytkowany.</span><span class="sxs-lookup"><span data-stu-id="5a513-142">Two vital parts of constructing a token are determining what key to sign the token with and what key to encrypt the shared key with.</span></span> <span data-ttu-id="5a513-143">Token musi być podpisany, aby podczas gdy klient przedstawia token dla usługi docelowej, usługa ta może ustalić, czy token został wystawiony przez usługę tokenu zabezpieczającego, która jest zaufana.</span><span class="sxs-lookup"><span data-stu-id="5a513-143">The token needs to be signed so that when the client presents the token to the target service, that service can determine that the token was issued by a security token service that it trusts.</span></span> <span data-ttu-id="5a513-144">Materiał klucza musi być zaszyfrowany w taki sposób, że usługa docelowa może odszyfrować ten materiał klucza.</span><span class="sxs-lookup"><span data-stu-id="5a513-144">The key material needs to be encrypted in such a way that the target service can decrypt that key material.</span></span>  
  
 <span data-ttu-id="5a513-145">Podpisywanie potwierdzenia SAML obejmuje tworzenie <xref:System.IdentityModel.Tokens.SigningCredentials> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5a513-145">Signing a SAML assertion involves creating a <xref:System.IdentityModel.Tokens.SigningCredentials> instance.</span></span> <span data-ttu-id="5a513-146">Konstruktor dla tej klasy wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5a513-146">The constructor for this class takes the following:</span></span>  
  
- <span data-ttu-id="5a513-147">A <xref:System.IdentityModel.Tokens.SecurityKey> dla klucza używanego do podpisywania potwierdzenia SAML.</span><span class="sxs-lookup"><span data-stu-id="5a513-147">A <xref:System.IdentityModel.Tokens.SecurityKey> for the key to use to sign the SAML assertion.</span></span>  
  
- <span data-ttu-id="5a513-148">Ciąg identyfikujący algorytm podpisu, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="5a513-148">A string identifying the signature algorithm to use.</span></span>  
  
- <span data-ttu-id="5a513-149">Ciąg identyfikujący algorytm szyfrowania, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="5a513-149">A string identifying the digest algorithm to use.</span></span>  
  
- <span data-ttu-id="5a513-150">Opcjonalnie, <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> który identyfikuje klucz do użycia w celu podpisania potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="5a513-150">Optionally, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> that identifies the key to use to sign the assertion.</span></span>  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 <span data-ttu-id="5a513-151">Szyfrowanie klucza współużytkowanego obejmuje pobranie materiału klucza i zaszyfrowanie go za pomocą klucza, którego usługa docelowa może użyć do odszyfrowania klucza współużytkowanego.</span><span class="sxs-lookup"><span data-stu-id="5a513-151">Encrypting the shared key involves taking the key material and encrypting it with a key that the target service can use to decrypt the shared key.</span></span> <span data-ttu-id="5a513-152">Zazwyczaj używany jest klucz publiczny usługi docelowej.</span><span class="sxs-lookup"><span data-stu-id="5a513-152">Typically, the public key of the target service is used.</span></span>  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 <span data-ttu-id="5a513-153">Ponadto <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> wymagany jest klucz szyfrowania klucza.</span><span class="sxs-lookup"><span data-stu-id="5a513-153">In addition, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> for the encrypted key is needed.</span></span>  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 <span data-ttu-id="5a513-154"><xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>Jest on następnie używany do tworzenia `SamlSubject` jako część elementu `SamlToken` .</span><span class="sxs-lookup"><span data-stu-id="5a513-154">This <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> is then used to create a `SamlSubject` as part of the `SamlToken`.</span></span>  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 <span data-ttu-id="5a513-155">Aby uzyskać więcej informacji, zobacz [przykład Federacji](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5a513-155">For more information, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
## <a name="creating-response-messages"></a><span data-ttu-id="5a513-156">Tworzenie komunikatów odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="5a513-156">Creating Response Messages</span></span>  
 <span data-ttu-id="5a513-157">Gdy usługa tokenu zabezpieczeń przetwarza żądanie problemu i konstruuje token, który ma zostać wystawiony wraz z kluczem testowym, należy skonstruować komunikat odpowiedzi, w tym co najmniej żądany token, token potwierdzający oraz odwołania do wystawionych tokenów.</span><span class="sxs-lookup"><span data-stu-id="5a513-157">Once the security token service processes the issue request and constructs the token to be issued along with the proof key, the response message needs to be constructed, including at least the requested token, the proof token, and the issued token references.</span></span> <span data-ttu-id="5a513-158">Wystawiony token jest zwykle <xref:System.IdentityModel.Tokens.SamlSecurityToken> tworzony przy użyciu <xref:System.IdentityModel.Tokens.SamlAssertion> , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5a513-158">The issued token is typically a <xref:System.IdentityModel.Tokens.SamlSecurityToken> created from the <xref:System.IdentityModel.Tokens.SamlAssertion>, as shown in the following example.</span></span>  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 <span data-ttu-id="5a513-159">W przypadku, gdy usługa tokenu zabezpieczającego udostępnia materiał klucza wspólnego, token potwierdzający jest konstruowany przez utworzenie <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken> .</span><span class="sxs-lookup"><span data-stu-id="5a513-159">In the case where the security token service provides the shared key material, the proof token is constructed by creating a <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span></span>  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 <span data-ttu-id="5a513-160">Aby uzyskać więcej informacji o sposobie konstruowania tokenu sprawdzającego, gdy klient i usługa tokenu zabezpieczającego zapewniają kluczowy materiał dla klucza współużytkowanego, zobacz [przykład Federacji](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5a513-160">For more information about how to construct the proof token when the client and the security token service both provide key material for the shared key, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
 <span data-ttu-id="5a513-161">Odwołania do wystawionych tokenów są tworzone przez tworzenie wystąpień <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> klasy.</span><span class="sxs-lookup"><span data-stu-id="5a513-161">The issued token references are constructed by creating instances of the <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> class.</span></span>  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 <span data-ttu-id="5a513-162">Te różne wartości są następnie serializowane do komunikatu odpowiedzi zwróconego do klienta.</span><span class="sxs-lookup"><span data-stu-id="5a513-162">These various values are then serialized into the response message returned to the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a513-163">Przykład</span><span class="sxs-lookup"><span data-stu-id="5a513-163">Example</span></span>  
 <span data-ttu-id="5a513-164">Aby uzyskać pełny kod dla usługi tokenu zabezpieczającego, zobacz [przykład Federacji](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5a513-164">For full code for a security token service, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a513-165">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a513-165">See also</span></span>

- <xref:System.IdentityModel.Tokens.SigningCredentials>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>
- <xref:System.IdentityModel.Tokens.SamlSecurityToken>
- <xref:System.IdentityModel.Tokens.SamlAssertion>
- <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>
- [<span data-ttu-id="5a513-166">Federacja — przykład</span><span class="sxs-lookup"><span data-stu-id="5a513-166">Federation Sample</span></span>](../samples/federation-sample.md)
