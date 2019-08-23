---
title: 'Instrukcje: tworzenie poświadczeń pomocniczych'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 1f95748235aa5238193b8869f8330f0a7fc650d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968896"
---
# <a name="how-to-create-a-supporting-credential"></a><span data-ttu-id="9ab4b-102">Instrukcje: tworzenie poświadczeń pomocniczych</span><span class="sxs-lookup"><span data-stu-id="9ab4b-102">How to: Create a Supporting Credential</span></span>
<span data-ttu-id="9ab4b-103">Istnieje możliwość, że niestandardowy schemat zabezpieczeń wymaga więcej niż jednego poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-103">It is possible to have a custom security scheme that requires more than one credential.</span></span> <span data-ttu-id="9ab4b-104">Na przykład usługa może wymagać od klienta nie tylko nazwy użytkownika i hasła, ale również poświadczenia, które potwierdzają, że klient znajduje się w wieku 18 lat.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-104">For example, a service may demand from the client not just a user name and password, but also a credential that proves the client is over the age of 18.</span></span> <span data-ttu-id="9ab4b-105">Drugie poświadczenie jest *pomocniczą*poświadczeniem.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-105">The second credential is a *supporting credential*.</span></span> <span data-ttu-id="9ab4b-106">W tym temacie wyjaśniono, jak zaimplementować takie poświadczenia w kliencie Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9ab4b-106">This topic explains how to implement such credentials in an Windows Communication Foundation (WCF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ab4b-107">Specyfikacja dla obsługi poświadczeń jest częścią specyfikacji WS-SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-107">The specification for supporting credentials is part of the WS-SecurityPolicy specification.</span></span> <span data-ttu-id="9ab4b-108">Aby uzyskać więcej informacji, zobacz [specyfikacje zabezpieczenia usług w sieci Web](https://go.microsoft.com/fwlink/?LinkId=88537).</span><span class="sxs-lookup"><span data-stu-id="9ab4b-108">For more information, see [Web Services Security Specifications](https://go.microsoft.com/fwlink/?LinkId=88537).</span></span>  
  
## <a name="supporting-tokens"></a><span data-ttu-id="9ab4b-109">Obsługa tokenów</span><span class="sxs-lookup"><span data-stu-id="9ab4b-109">Supporting Tokens</span></span>  
 <span data-ttu-id="9ab4b-110">W przypadku korzystania z zabezpieczeń wiadomości *podstawowe poświadczenia* są zawsze używane do zabezpieczania wiadomości (na przykład certyfikatu X. 509 lub biletu Kerberos).</span><span class="sxs-lookup"><span data-stu-id="9ab4b-110">In brief, when you use message security, a *primary credential* is always used to secure the message (for example, an X.509 certificate or a Kerberos ticket).</span></span>  
  
 <span data-ttu-id="9ab4b-111">Zgodnie ze specyfikacją, powiązanie zabezpieczeń używa tokenów do zabezpieczenia wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-111">As defined by the specification, a security binding uses *tokens* to secure the message exchange.</span></span> <span data-ttu-id="9ab4b-112">*Token* jest reprezentacją poświadczenia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-112">A *token* is a representation of a security credential.</span></span>  
  
 <span data-ttu-id="9ab4b-113">Powiązanie zabezpieczeń używa tokenu podstawowego zidentyfikowanego w zasadzie powiązań zabezpieczeń w celu utworzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-113">The security binding uses a primary token identified in the security binding policy to create a signature.</span></span> <span data-ttu-id="9ab4b-114">Ta sygnatura jest określana jako *sygnatura wiadomości*.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-114">This signature is referred to as the *message signature*.</span></span>  
  
 <span data-ttu-id="9ab4b-115">Dodatkowe tokeny można określić, aby rozszerzyć oświadczenia dostarczone przez token skojarzony z podpisem komunikatu.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-115">Additional tokens can be specified to augment the claims provided by the token associated with the message signature.</span></span>  
  
## <a name="endorsing-signing-and-encrypting"></a><span data-ttu-id="9ab4b-116">Zatwierdzanie, podpisywanie i szyfrowanie</span><span class="sxs-lookup"><span data-stu-id="9ab4b-116">Endorsing, Signing, and Encrypting</span></span>  
 <span data-ttu-id="9ab4b-117">W wyniku obsługi poświadczenie pomocnicze przesyłane w komunikacie jest *obsługiwany token* .</span><span class="sxs-lookup"><span data-stu-id="9ab4b-117">A supporting credential results in a *supporting token* transmitted inside the message.</span></span> <span data-ttu-id="9ab4b-118">Specyfikacja WS-SecurityPolicy definiuje cztery sposoby dołączania tokenu pomocniczego do wiadomości, zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-118">The WS-SecurityPolicy specification defines four ways to attach a supporting token to the message, as described in the following table.</span></span>  
  
|<span data-ttu-id="9ab4b-119">Cel</span><span class="sxs-lookup"><span data-stu-id="9ab4b-119">Purpose</span></span>|<span data-ttu-id="9ab4b-120">Opis</span><span class="sxs-lookup"><span data-stu-id="9ab4b-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ab4b-121">Opatrzon</span><span class="sxs-lookup"><span data-stu-id="9ab4b-121">Signed</span></span>|<span data-ttu-id="9ab4b-122">Token pomocniczy jest zawarty w nagłówku zabezpieczeń i jest podpisany przez sygnaturę wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-122">The supporting token is included in the security header and is signed by the message signature.</span></span>|  
|<span data-ttu-id="9ab4b-123">Indosowania</span><span class="sxs-lookup"><span data-stu-id="9ab4b-123">Endorsing</span></span>|<span data-ttu-id="9ab4b-124">*Token poświadczający* podpisuje sygnaturę wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-124">An *endorsing token* signs the message signature.</span></span>|  
|<span data-ttu-id="9ab4b-125">Podpisywanie i zatwierdzanie</span><span class="sxs-lookup"><span data-stu-id="9ab4b-125">Signed and Endorsing</span></span>|<span data-ttu-id="9ab4b-126">Podpisane, poświadczające tokeny podpisują `ds:Signature` cały element wystawiony na podstawie podpisu wiadomości i są podpisywane przez tę sygnaturę wiadomości; oznacza to, że oba tokeny (token używany dla podpisu wiadomości i podpisany token poświadczający) podpisują siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-126">Signed, endorsing tokens sign the entire `ds:Signature` element produced from the message signature and are themselves signed by that message signature; that is, both tokens (the token used for the message signature and the signed endorsing token) sign each other.</span></span>|  
|<span data-ttu-id="9ab4b-127">Podpisywanie i szyfrowanie</span><span class="sxs-lookup"><span data-stu-id="9ab4b-127">Signed and Encrypting</span></span>|<span data-ttu-id="9ab4b-128">Podpisane, zaszyfrowane tokeny pomocnicze są podpisywane tokeny pomocnicze, które są `wsse:SecurityHeader`również szyfrowane, gdy są wyświetlane w.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-128">Signed, encrypted supporting tokens are signed supporting tokens that are also encrypted when they appear in the `wsse:SecurityHeader`.</span></span>|  
  
## <a name="programming-supporting-credentials"></a><span data-ttu-id="9ab4b-129">Programowanie — poświadczenia pomocnicze</span><span class="sxs-lookup"><span data-stu-id="9ab4b-129">Programming Supporting Credentials</span></span>  
 <span data-ttu-id="9ab4b-130">Aby utworzyć usługę korzystającą z tokenów pomocniczych, należy [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)utworzyć niestandardową >Binding.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-130">To create a service that uses supporting tokens you must create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span> <span data-ttu-id="9ab4b-131">(Aby uzyskać więcej informacji, [zobacz How to: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span><span class="sxs-lookup"><span data-stu-id="9ab4b-131">(For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span></span>  
  
 <span data-ttu-id="9ab4b-132">Pierwszym krokiem podczas tworzenia niestandardowego powiązania jest utworzenie elementu powiązania zabezpieczeń, który może być jednym z trzech typów:</span><span class="sxs-lookup"><span data-stu-id="9ab4b-132">The first step when creating a custom binding is to create a security binding element, which can be one of three types:</span></span>  
  
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="9ab4b-133">Wszystkie klasy dziedziczą z <xref:System.ServiceModel.Channels.SecurityBindingElement>, która obejmuje cztery odpowiednie właściwości:</span><span class="sxs-lookup"><span data-stu-id="9ab4b-133">All classes inherit from the <xref:System.ServiceModel.Channels.SecurityBindingElement>, which includes four relevant properties:</span></span>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a><span data-ttu-id="9ab4b-134">Zakresy</span><span class="sxs-lookup"><span data-stu-id="9ab4b-134">Scopes</span></span>  
 <span data-ttu-id="9ab4b-135">Istnieją dwa zakresy do obsługi poświadczeń:</span><span class="sxs-lookup"><span data-stu-id="9ab4b-135">Two scopes exist for supporting credentials:</span></span>  
  
- <span data-ttu-id="9ab4b-136">*Tokeny obsługujące punkt końcowy* obsługują wszystkie operacje na punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-136">*Endpoint supporting tokens* support all operations of an endpoint.</span></span> <span data-ttu-id="9ab4b-137">Oznacza to, że poświadczenie, którego token pomocniczy reprezentuje, może być używane za każdym razem, gdy zostaną wywołane wszystkie operacje punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-137">That is, the credential that the supporting token represents can be used whenever any endpoint operations are invoked.</span></span>  
  
- <span data-ttu-id="9ab4b-138">*Operacje* obsługujące tokeny obsługują tylko określoną operację punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-138">*Operation supporting tokens* support only a specific endpoint operation.</span></span>  
  
 <span data-ttu-id="9ab4b-139">Jak wskazano nazwy właściwości, obsługa poświadczeń może być wymagana lub opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-139">As indicated by the property names, supporting credentials can be either required or optional.</span></span> <span data-ttu-id="9ab4b-140">Oznacza to, że jeśli jest używane poświadczenie pomocnicze, mimo że nie jest to konieczne, ale uwierzytelnianie nie powiedzie się, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-140">That is, if the supporting credential is used if it is present, although it is not necessary, but the authentication will not fail if it is not present.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="9ab4b-141">Procedury</span><span class="sxs-lookup"><span data-stu-id="9ab4b-141">Procedures</span></span>  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a><span data-ttu-id="9ab4b-142">Tworzenie niestandardowego powiązania zawierającego poświadczenia pomocnicze</span><span class="sxs-lookup"><span data-stu-id="9ab4b-142">To create a custom binding that includes supporting credentials</span></span>  
  
1. <span data-ttu-id="9ab4b-143">Utwórz element powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-143">Create a security binding element.</span></span> <span data-ttu-id="9ab4b-144">Poniższy przykład tworzy <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> `UserNameForCertificate` z trybem uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-144">The example below creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> with the `UserNameForCertificate` authentication mode.</span></span> <span data-ttu-id="9ab4b-145"><xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> Użyj metody.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-145">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> method.</span></span>  
  
2. <span data-ttu-id="9ab4b-146">Dodaj parametr pomocniczy do kolekcji typów zwracanych przez odpowiednią właściwość`Endorsing`(, `Signed`, `SignedEncrypted`lub `SignedEndorsed`).</span><span class="sxs-lookup"><span data-stu-id="9ab4b-146">Add the supporting parameter to the collection of types returned by the appropriate property (`Endorsing`, `Signed`, `SignedEncrypted`, or `SignedEndorsed`).</span></span> <span data-ttu-id="9ab4b-147">Typy w <xref:System.ServiceModel.Security.Tokens> przestrzeni nazw zawierają powszechnie używane typy, takie <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>jak.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-147">The types in the <xref:System.ServiceModel.Security.Tokens> namespace include commonly used types, such as the <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ab4b-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ab4b-148">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9ab4b-149">Opis</span><span class="sxs-lookup"><span data-stu-id="9ab4b-149">Description</span></span>  
 <span data-ttu-id="9ab4b-150">Poniższy przykład tworzy wystąpienie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i dodaje wystąpienie <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> klasy do kolekcji, która zwraca właściwość poświadczający.</span><span class="sxs-lookup"><span data-stu-id="9ab4b-150">The following example creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and adds an instance of the <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> class to the collection the Endorsing property returned.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9ab4b-151">Kod</span><span class="sxs-lookup"><span data-stu-id="9ab4b-151">Code</span></span>  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9ab4b-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ab4b-152">See also</span></span>

- [<span data-ttu-id="9ab4b-153">Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9ab4b-153">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
