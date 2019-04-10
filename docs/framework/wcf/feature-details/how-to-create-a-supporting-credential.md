---
title: 'Instrukcje: tworzenie poświadczeń pomocniczych'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 7c6c4ea777f62541f8ca8fa79fdd024e5f5cf2ad
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326050"
---
# <a name="how-to-create-a-supporting-credential"></a><span data-ttu-id="0b3fb-102">Instrukcje: tworzenie poświadczeń pomocniczych</span><span class="sxs-lookup"><span data-stu-id="0b3fb-102">How to: Create a Supporting Credential</span></span>
<span data-ttu-id="0b3fb-103">Istnieje możliwość schematu niestandardowego zabezpieczeń, która wymaga więcej niż jedno poświadczenie.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-103">It is possible to have a custom security scheme that requires more than one credential.</span></span> <span data-ttu-id="0b3fb-104">Na przykład usługa może wymagać od klienta nie tylko nazwę użytkownika i hasło, ale również poświadczeń, który okazał się klienta znajduje się nad niż 18 lat.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-104">For example, a service may demand from the client not just a user name and password, but also a credential that proves the client is over the age of 18.</span></span> <span data-ttu-id="0b3fb-105">Drugie poświadczenie jest *obsługi poświadczeń*.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-105">The second credential is a *supporting credential*.</span></span> <span data-ttu-id="0b3fb-106">W tym temacie wyjaśniono, jak wdrożyć tych poświadczeń w kliencie programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0b3fb-106">This topic explains how to implement such credentials in an Windows Communication Foundation (WCF) client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b3fb-107">Specyfikacja do obsługi poświadczeń jest częścią specyfikacji WS-SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-107">The specification for supporting credentials is part of the WS-SecurityPolicy specification.</span></span> <span data-ttu-id="0b3fb-108">Aby uzyskać więcej informacji, zobacz [specyfikacji zabezpieczenia usługi sieci Web](https://go.microsoft.com/fwlink/?LinkId=88537).</span><span class="sxs-lookup"><span data-stu-id="0b3fb-108">For more information, see [Web Services Security Specifications](https://go.microsoft.com/fwlink/?LinkId=88537).</span></span>  
  
## <a name="supporting-tokens"></a><span data-ttu-id="0b3fb-109">Obsługa tokenów</span><span class="sxs-lookup"><span data-stu-id="0b3fb-109">Supporting Tokens</span></span>  
 <span data-ttu-id="0b3fb-110">Krótko mówiąc, gdy używasz zabezpieczeń komunikatów *podstawowej credential* zawsze służy do zabezpieczania komunikatu (na przykład certyfikat X.509 lub biletu protokołu Kerberos).</span><span class="sxs-lookup"><span data-stu-id="0b3fb-110">In brief, when you use message security, a *primary credential* is always used to secure the message (for example, an X.509 certificate or a Kerberos ticket).</span></span>  
  
 <span data-ttu-id="0b3fb-111">Zgodnie z definicją w specyfikacji, powiązanie zabezpieczeń używa *tokenów* zabezpieczyć wymianę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-111">As defined by the specification, a security binding uses *tokens* to secure the message exchange.</span></span> <span data-ttu-id="0b3fb-112">A *tokenu* jest reprezentacją poświadczeń zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-112">A *token* is a representation of a security credential.</span></span>  
  
 <span data-ttu-id="0b3fb-113">Powiązanie zabezpieczeń używa token podstawowy określone w zasadach zabezpieczeń powiązania do tworzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-113">The security binding uses a primary token identified in the security binding policy to create a signature.</span></span> <span data-ttu-id="0b3fb-114">Podpis ten jest nazywany *podpisu wiadomości*.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-114">This signature is referred to as the *message signature*.</span></span>  
  
 <span data-ttu-id="0b3fb-115">Można określić dodatkowe tokeny rozszerzyć oświadczenia dostarczane przez tokenu skojarzone z podpisu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-115">Additional tokens can be specified to augment the claims provided by the token associated with the message signature.</span></span>  
  
## <a name="endorsing-signing-and-encrypting"></a><span data-ttu-id="0b3fb-116">Potwierdzających, podpisywanie i szyfrowanie</span><span class="sxs-lookup"><span data-stu-id="0b3fb-116">Endorsing, Signing, and Encrypting</span></span>  
 <span data-ttu-id="0b3fb-117">Pomocnicze poświadczenia skutkuje *token pomocniczy* przekazywane wewnątrz komunikatu.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-117">A supporting credential results in a *supporting token* transmitted inside the message.</span></span> <span data-ttu-id="0b3fb-118">Specyfikacja WS-SecurityPolicy definiuje cztery sposoby dołączenia tokenu pomocniczego do wiadomości, zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-118">The WS-SecurityPolicy specification defines four ways to attach a supporting token to the message, as described in the following table.</span></span>  
  
|<span data-ttu-id="0b3fb-119">Cel</span><span class="sxs-lookup"><span data-stu-id="0b3fb-119">Purpose</span></span>|<span data-ttu-id="0b3fb-120">Opis</span><span class="sxs-lookup"><span data-stu-id="0b3fb-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b3fb-121">Podpisany</span><span class="sxs-lookup"><span data-stu-id="0b3fb-121">Signed</span></span>|<span data-ttu-id="0b3fb-122">Token pomocniczy znajduje się w nagłówku zabezpieczeń i jest podpisany przez podpisu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-122">The supporting token is included in the security header and is signed by the message signature.</span></span>|  
|<span data-ttu-id="0b3fb-123">Wprowadzająca</span><span class="sxs-lookup"><span data-stu-id="0b3fb-123">Endorsing</span></span>|<span data-ttu-id="0b3fb-124">*Zatwierdzania token* podpisuje podpisu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-124">An *endorsing token* signs the message signature.</span></span>|  
|<span data-ttu-id="0b3fb-125">Ze znakiem i zatwierdzania</span><span class="sxs-lookup"><span data-stu-id="0b3fb-125">Signed and Endorsing</span></span>|<span data-ttu-id="0b3fb-126">Podpisana, potwierdzających tokenów logowania całą `ds:Signature` element wyprodukowanych z podpisu wiadomości i są same podpisane przez ten podpis wiadomości; oznacza to, że oba tokeny (tokenu użytego do podpisania komunikatu i podpisany token zatwierdzania) Zaloguj się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-126">Signed, endorsing tokens sign the entire `ds:Signature` element produced from the message signature and are themselves signed by that message signature; that is, both tokens (the token used for the message signature and the signed endorsing token) sign each other.</span></span>|  
|<span data-ttu-id="0b3fb-127">Ze znakiem i szyfrowania</span><span class="sxs-lookup"><span data-stu-id="0b3fb-127">Signed and Encrypting</span></span>|<span data-ttu-id="0b3fb-128">Podpisany, zaszyfrowanych tokenów pomocniczych są podpisane, Obsługa tokenów, które również są szyfrowane, gdy są one wyświetlane w `wsse:SecurityHeader`.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-128">Signed, encrypted supporting tokens are signed supporting tokens that are also encrypted when they appear in the `wsse:SecurityHeader`.</span></span>|  
  
## <a name="programming-supporting-credentials"></a><span data-ttu-id="0b3fb-129">Obsługa poświadczeń programowania</span><span class="sxs-lookup"><span data-stu-id="0b3fb-129">Programming Supporting Credentials</span></span>  
 <span data-ttu-id="0b3fb-130">Aby utworzyć usługę, który używa tokenów pomocniczych, należy utworzyć [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="0b3fb-130">To create a service that uses supporting tokens you must create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span> <span data-ttu-id="0b3fb-131">(Aby uzyskać więcej informacji, zobacz [jak: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span><span class="sxs-lookup"><span data-stu-id="0b3fb-131">(For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span></span>  
  
 <span data-ttu-id="0b3fb-132">Pierwszym krokiem podczas tworzenia niestandardowego powiązania jest utworzyć elementu powiązania zabezpieczeń, który może być jednym z trzech typów:</span><span class="sxs-lookup"><span data-stu-id="0b3fb-132">The first step when creating a custom binding is to create a security binding element, which can be one of three types:</span></span>  
  
-   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="0b3fb-133">Wszystkie klasy dziedziczą z <xref:System.ServiceModel.Channels.SecurityBindingElement>, która obejmuje cztery odpowiednie właściwości:</span><span class="sxs-lookup"><span data-stu-id="0b3fb-133">All classes inherit from the <xref:System.ServiceModel.Channels.SecurityBindingElement>, which includes four relevant properties:</span></span>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a><span data-ttu-id="0b3fb-134">Zakresy</span><span class="sxs-lookup"><span data-stu-id="0b3fb-134">Scopes</span></span>  
 <span data-ttu-id="0b3fb-135">Istnieją dwa zakresy do obsługi poświadczeń:</span><span class="sxs-lookup"><span data-stu-id="0b3fb-135">Two scopes exist for supporting credentials:</span></span>  
  
-   <span data-ttu-id="0b3fb-136">*Punkt końcowy tokenów pomocniczych* obsługuje wszystkie operacje dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-136">*Endpoint supporting tokens* support all operations of an endpoint.</span></span> <span data-ttu-id="0b3fb-137">Oznacza to, że poświadczenie, które reprezentuje token pomocniczy można zawsze wtedy, gdy dowolne operacje punktu końcowego są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-137">That is, the credential that the supporting token represents can be used whenever any endpoint operations are invoked.</span></span>  
  
-   <span data-ttu-id="0b3fb-138">*Obsługa tokenów operacji* obsługuje tylko operacji do określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-138">*Operation supporting tokens* support only a specific endpoint operation.</span></span>  
  
 <span data-ttu-id="0b3fb-139">Obsługa poświadczeń może być wskazane przez nazwy właściwości, wymaganego lub opcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-139">As indicated by the property names, supporting credentials can be either required or optional.</span></span> <span data-ttu-id="0b3fb-140">Oznacza to jeśli pomocnicze poświadczenie jest używane, jeśli jest obecny, chociaż nie jest konieczne, ale uwierzytelnianie zakończy się niepowodzeniem, jeśli nie jest obecny.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-140">That is, if the supporting credential is used if it is present, although it is not necessary, but the authentication will not fail if it is not present.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="0b3fb-141">Procedury</span><span class="sxs-lookup"><span data-stu-id="0b3fb-141">Procedures</span></span>  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a><span data-ttu-id="0b3fb-142">Tworzenie niestandardowego powiązania, które obejmuje pomocnicze poświadczenia</span><span class="sxs-lookup"><span data-stu-id="0b3fb-142">To create a custom binding that includes supporting credentials</span></span>  
  
1. <span data-ttu-id="0b3fb-143">Tworzenie elementu powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-143">Create a security binding element.</span></span> <span data-ttu-id="0b3fb-144">Poniższy przykład tworzy <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> z `UserNameForCertificate` tryb uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-144">The example below creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> with the `UserNameForCertificate` authentication mode.</span></span> <span data-ttu-id="0b3fb-145">Użyj <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-145">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> method.</span></span>  
  
2. <span data-ttu-id="0b3fb-146">Dodaj parametr pomocniczych do kolekcji typów zwracany przez właściwość odpowiednie (`Endorsing`, `Signed`, `SignedEncrypted`, lub `SignedEndorsed`).</span><span class="sxs-lookup"><span data-stu-id="0b3fb-146">Add the supporting parameter to the collection of types returned by the appropriate property (`Endorsing`, `Signed`, `SignedEncrypted`, or `SignedEndorsed`).</span></span> <span data-ttu-id="0b3fb-147">Typy w <xref:System.ServiceModel.Security.Tokens> przestrzeni nazw obejmują często używanych typów, takie jak <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-147">The types in the <xref:System.ServiceModel.Security.Tokens> namespace include commonly used types, such as the <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b3fb-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="0b3fb-148">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="0b3fb-149">Opis</span><span class="sxs-lookup"><span data-stu-id="0b3fb-149">Description</span></span>  
 <span data-ttu-id="0b3fb-150">Poniższy przykład tworzy wystąpienie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i dodaje instancję <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> klasy do kolekcji właściwości Endorsing zwróconej.</span><span class="sxs-lookup"><span data-stu-id="0b3fb-150">The following example creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and adds an instance of the <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> class to the collection the Endorsing property returned.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0b3fb-151">Kod</span><span class="sxs-lookup"><span data-stu-id="0b3fb-151">Code</span></span>  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0b3fb-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b3fb-152">See also</span></span>

- [<span data-ttu-id="0b3fb-153">Instrukcje: tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="0b3fb-153">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
