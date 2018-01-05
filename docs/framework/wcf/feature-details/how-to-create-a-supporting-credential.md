---
title: "Instrukcje: Tworzenie poświadczeń pomocniczych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4afad13300e2eb50a9625a5991bc8cb724c21dd6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-supporting-credential"></a><span data-ttu-id="0fabf-102">Instrukcje: Tworzenie poświadczeń pomocniczych</span><span class="sxs-lookup"><span data-stu-id="0fabf-102">How to: Create a Supporting Credential</span></span>
<span data-ttu-id="0fabf-103">Istnieje możliwość schematu niestandardowego zabezpieczeń, która wymaga więcej niż jedno poświadczenie.</span><span class="sxs-lookup"><span data-stu-id="0fabf-103">It is possible to have a custom security scheme that requires more than one credential.</span></span> <span data-ttu-id="0fabf-104">Na przykład usługa może wymagać od klienta nie tylko nazwę użytkownika i hasło, ale również poświadczenia, który gwarantuje klienta znajduje się nad wiek 18.</span><span class="sxs-lookup"><span data-stu-id="0fabf-104">For example, a service may demand from the client not just a user name and password, but also a credential that proves the client is over the age of 18.</span></span> <span data-ttu-id="0fabf-105">Drugi poświadczenie jest *Obsługa poświadczeń*.</span><span class="sxs-lookup"><span data-stu-id="0fabf-105">The second credential is a *supporting credential*.</span></span> <span data-ttu-id="0fabf-106">W tym temacie opisano sposób wykonania tych poświadczeń w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta.</span><span class="sxs-lookup"><span data-stu-id="0fabf-106">This topic explains how to implement such credentials in an [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0fabf-107">Specyfikacja umożliwiającego poświadczeń jest częścią specyfikacji WS-SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="0fabf-107">The specification for supporting credentials is part of the WS-SecurityPolicy specification.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="0fabf-108">[Specyfikacji zabezpieczenia usług sieci web](http://go.microsoft.com/fwlink/?LinkId=88537).</span><span class="sxs-lookup"><span data-stu-id="0fabf-108"> [Web Services Security Specifications](http://go.microsoft.com/fwlink/?LinkId=88537).</span></span>  
  
## <a name="supporting-tokens"></a><span data-ttu-id="0fabf-109">Obsługa tokenów</span><span class="sxs-lookup"><span data-stu-id="0fabf-109">Supporting Tokens</span></span>  
 <span data-ttu-id="0fabf-110">Krótko mówiąc, jeśli używasz zabezpieczenia komunikatów *poświadczenia podstawowego* zawsze jest używany do zabezpieczania komunikatów (na przykład certyfikat X.509 lub biletu protokołu Kerberos).</span><span class="sxs-lookup"><span data-stu-id="0fabf-110">In brief, when you use message security, a *primary credential* is always used to secure the message (for example, an X.509 certificate or a Kerberos ticket).</span></span>  
  
 <span data-ttu-id="0fabf-111">Zdefiniowane przez specyfikację elementu powiązania zabezpieczeń używa *tokenów* do zabezpieczania wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0fabf-111">As defined by the specification, a security binding uses *tokens* to secure the message exchange.</span></span> <span data-ttu-id="0fabf-112">A *tokenu* reprezentacja poświadczeń zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="0fabf-112">A *token* is a representation of a security credential.</span></span>  
  
 <span data-ttu-id="0fabf-113">Powiązanie zabezpieczeń używa token podstawowy określone w zasadach zabezpieczeń powiązania do tworzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="0fabf-113">The security binding uses a primary token identified in the security binding policy to create a signature.</span></span> <span data-ttu-id="0fabf-114">Ta sygnatura jest określany jako *podpisu wiadomości*.</span><span class="sxs-lookup"><span data-stu-id="0fabf-114">This signature is referred to as the *message signature*.</span></span>  
  
 <span data-ttu-id="0fabf-115">Aby rozszerzyć oświadczeń udostępniane przez token skojarzony z sygnaturą komunikat można określić dodatkowe tokeny.</span><span class="sxs-lookup"><span data-stu-id="0fabf-115">Additional tokens can be specified to augment the claims provided by the token associated with the message signature.</span></span>  
  
## <a name="endorsing-signing-and-encrypting"></a><span data-ttu-id="0fabf-116">Wprowadzająca podpisywania i szyfrowania</span><span class="sxs-lookup"><span data-stu-id="0fabf-116">Endorsing, Signing, and Encrypting</span></span>  
 <span data-ttu-id="0fabf-117">Wynikiem poświadczeń pomocniczych *tokenu pomocniczego* przesyłane w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="0fabf-117">A supporting credential results in a *supporting token* transmitted inside the message.</span></span> <span data-ttu-id="0fabf-118">Specyfikacja WS-SecurityPolicy definiuje cztery sposoby dołączenia tokenu pomocniczego do wiadomości, zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="0fabf-118">The WS-SecurityPolicy specification defines four ways to attach a supporting token to the message, as described in the following table.</span></span>  
  
|<span data-ttu-id="0fabf-119">Cel</span><span class="sxs-lookup"><span data-stu-id="0fabf-119">Purpose</span></span>|<span data-ttu-id="0fabf-120">Opis</span><span class="sxs-lookup"><span data-stu-id="0fabf-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0fabf-121">Podpisany</span><span class="sxs-lookup"><span data-stu-id="0fabf-121">Signed</span></span>|<span data-ttu-id="0fabf-122">Token pomocniczy znajduje się w nagłówku zabezpieczeń i jest podpisany przez podpisu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0fabf-122">The supporting token is included in the security header and is signed by the message signature.</span></span>|  
|<span data-ttu-id="0fabf-123">Wprowadzająca</span><span class="sxs-lookup"><span data-stu-id="0fabf-123">Endorsing</span></span>|<span data-ttu-id="0fabf-124">*Indosowania token* podpisuje podpisu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0fabf-124">An *endorsing token* signs the message signature.</span></span>|  
|<span data-ttu-id="0fabf-125">Podpisane i zatwierdzania</span><span class="sxs-lookup"><span data-stu-id="0fabf-125">Signed and Endorsing</span></span>|<span data-ttu-id="0fabf-126">Podpisana, wprowadzająca tokeny logowania całą `ds:Signature` element wyprodukowane z podpisu wiadomości i są same podpisane przez tego podpisu wiadomości; oznacza to, że oba tokeny (tokenu użytego do podpisania wiadomości i podpisany token indosowania) Zarejestruj się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="0fabf-126">Signed, endorsing tokens sign the entire `ds:Signature` element produced from the message signature and are themselves signed by that message signature; that is, both tokens (the token used for the message signature and the signed endorsing token) sign each other.</span></span>|  
|<span data-ttu-id="0fabf-127">Podpisane i szyfrowania</span><span class="sxs-lookup"><span data-stu-id="0fabf-127">Signed and Encrypting</span></span>|<span data-ttu-id="0fabf-128">Są podpisane podpisem, zaszyfrowanych tokenów pomocniczych, Obsługa tokenów, które również są szyfrowane, gdy są one wyświetlane w `wsse:SecurityHeader`.</span><span class="sxs-lookup"><span data-stu-id="0fabf-128">Signed, encrypted supporting tokens are signed supporting tokens that are also encrypted when they appear in the `wsse:SecurityHeader`.</span></span>|  
  
## <a name="programming-supporting-credentials"></a><span data-ttu-id="0fabf-129">Programowanie Obsługa poświadczeń</span><span class="sxs-lookup"><span data-stu-id="0fabf-129">Programming Supporting Credentials</span></span>  
 <span data-ttu-id="0fabf-130">Aby utworzyć usługę, która korzysta z tokenów pomocniczych, należy utworzyć [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="0fabf-130">To create a service that uses supporting tokens you must create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span> <span data-ttu-id="0fabf-131">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Porady: Tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span><span class="sxs-lookup"><span data-stu-id="0fabf-131">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span></span>  
  
 <span data-ttu-id="0fabf-132">Pierwszym krokiem podczas tworzenia niestandardowego powiązania jest można utworzyć elementu powiązania zabezpieczeń, które może być jedną z trzech typów:</span><span class="sxs-lookup"><span data-stu-id="0fabf-132">The first step when creating a custom binding is to create a security binding element, which can be one of three types:</span></span>  
  
-   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="0fabf-133">Wszystkie klasy dziedziczą <xref:System.ServiceModel.Channels.SecurityBindingElement>, która obejmuje cztery odpowiednie właściwości:</span><span class="sxs-lookup"><span data-stu-id="0fabf-133">All classes inherit from the <xref:System.ServiceModel.Channels.SecurityBindingElement>, which includes four relevant properties:</span></span>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a><span data-ttu-id="0fabf-134">Zakresy</span><span class="sxs-lookup"><span data-stu-id="0fabf-134">Scopes</span></span>  
 <span data-ttu-id="0fabf-135">Istnieją dwa zakresy umożliwiającego poświadczeń:</span><span class="sxs-lookup"><span data-stu-id="0fabf-135">Two scopes exist for supporting credentials:</span></span>  
  
-   <span data-ttu-id="0fabf-136">*Punkt końcowy tokenami pomocniczymi* obsługuje wszystkich operacji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0fabf-136">*Endpoint supporting tokens* support all operations of an endpoint.</span></span> <span data-ttu-id="0fabf-137">Oznacza to poświadczenia, który reprezentuje token pomocniczy można używać zawsze, gdy wszystkie operacje punktu końcowego są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="0fabf-137">That is, the credential that the supporting token represents can be used whenever any endpoint operations are invoked.</span></span>  
  
-   <span data-ttu-id="0fabf-138">*Operacja tokenami pomocniczymi* obsługuje tylko operacji określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0fabf-138">*Operation supporting tokens* support only a specific endpoint operation.</span></span>  
  
 <span data-ttu-id="0fabf-139">Wskazywany przez nazwy właściwości, obsługa poświadczeń może być wymagany lub opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0fabf-139">As indicated by the property names, supporting credentials can be either required or optional.</span></span> <span data-ttu-id="0fabf-140">Oznacza to, że jeśli pomocniczy poświadczenie jest używane, jeśli jest obecny, chociaż nie jest konieczne, ale uwierzytelnianie zakończy się niepowodzeniem, jeśli nie jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="0fabf-140">That is, if the supporting credential is used if it is present, although it is not necessary, but the authentication will not fail if it is not present.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="0fabf-141">Procedury</span><span class="sxs-lookup"><span data-stu-id="0fabf-141">Procedures</span></span>  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a><span data-ttu-id="0fabf-142">Aby utworzyć niestandardowego powiązania, które zawiera Obsługa poświadczeń</span><span class="sxs-lookup"><span data-stu-id="0fabf-142">To create a custom binding that includes supporting credentials</span></span>  
  
1.  <span data-ttu-id="0fabf-143">Tworzenie elementu powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="0fabf-143">Create a security binding element.</span></span> <span data-ttu-id="0fabf-144">Poniższy przykład tworzy <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> z `UserNameForCertificate` tryb uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="0fabf-144">The example below creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> with the `UserNameForCertificate` authentication mode.</span></span> <span data-ttu-id="0fabf-145">Użyj <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0fabf-145">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> method.</span></span>  
  
2.  <span data-ttu-id="0fabf-146">Dodaj parametr pomocnicze do kolekcji typy zwracane przez odpowiednie właściwości (`Endorsing`, `Signed`, `SignedEncrypted`, lub `SignedEndorsed`).</span><span class="sxs-lookup"><span data-stu-id="0fabf-146">Add the supporting parameter to the collection of types returned by the appropriate property (`Endorsing`, `Signed`, `SignedEncrypted`, or `SignedEndorsed`).</span></span> <span data-ttu-id="0fabf-147">Typy w <xref:System.ServiceModel.Security.Tokens> przestrzeni nazw obejmują często używanych typów, takie jak <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span><span class="sxs-lookup"><span data-stu-id="0fabf-147">The types in the <xref:System.ServiceModel.Security.Tokens> namespace include commonly used types, such as the <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fabf-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="0fabf-148">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="0fabf-149">Opis</span><span class="sxs-lookup"><span data-stu-id="0fabf-149">Description</span></span>  
 <span data-ttu-id="0fabf-150">Poniższy przykład tworzy wystąpienie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i dodaje wystąpienie <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> klasy do kolekcji właściwości Endorsing zwróconej.</span><span class="sxs-lookup"><span data-stu-id="0fabf-150">The following example creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and adds an instance of the <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> class to the collection the Endorsing property returned.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0fabf-151">Kod</span><span class="sxs-lookup"><span data-stu-id="0fabf-151">Code</span></span>  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0fabf-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0fabf-152">See Also</span></span>  
 [<span data-ttu-id="0fabf-153">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="0fabf-153">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
