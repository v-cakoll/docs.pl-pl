---
title: 'Instrukcje: konfigurowanie lokalnego wystawcy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
ms.openlocfilehash: 0028a0522447588ee0fb183b5b2f93d334a7b2b2
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972067"
---
# <a name="how-to-configure-a-local-issuer"></a><span data-ttu-id="0d4f6-102">Instrukcje: konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="0d4f6-102">How to: Configure a Local Issuer</span></span>

<span data-ttu-id="0d4f6-103">W tym temacie opisano sposób konfigurowania klienta do używania lokalnego wystawcy dla wystawionych tokenów.</span><span class="sxs-lookup"><span data-stu-id="0d4f6-103">This topic describes how to configure a client to use a local issuer for issued tokens.</span></span>

<span data-ttu-id="0d4f6-104">Często, gdy klient komunikuje się z usługą federacyjną, usługa określa adres usługi tokenu zabezpieczającego, która powinna wydać token używany przez klienta do samodzielnego uwierzytelnienia w usłudze federacyjnej.</span><span class="sxs-lookup"><span data-stu-id="0d4f6-104">Often, when a client communicates with a federated service, the service specifies the address of the security token service that is expected to issue the token the client will use to authenticate itself to the federated service.</span></span> <span data-ttu-id="0d4f6-105">W niektórych sytuacjach klient może być skonfigurowany do korzystania z *lokalnego*wystawcy.</span><span class="sxs-lookup"><span data-stu-id="0d4f6-105">In certain situations, the client may be configured to use a *local issuer*.</span></span>

<span data-ttu-id="0d4f6-106">Windows Communication Foundation (WCF) używa wystawcy lokalnego w przypadkach, gdy adres wystawcy powiązania federacyjnego `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` to `null`lub.</span><span class="sxs-lookup"><span data-stu-id="0d4f6-106">Windows Communication Foundation (WCF) uses a local issuer in cases where the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`.</span></span> <span data-ttu-id="0d4f6-107">W takich przypadkach należy skonfigurować <xref:System.ServiceModel.Description.ClientCredentials> program przy użyciu adresu wystawcy lokalnego i powiązania, które ma być używane do komunikacji z tym wystawcą.</span><span class="sxs-lookup"><span data-stu-id="0d4f6-107">In such cases, you must configure the <xref:System.ServiceModel.Description.ClientCredentials> with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>

> [!NOTE]
> <span data-ttu-id="0d4f6-108">`true`Jeśli właściwość klasy`ClientCredentials` jest ustawiona na, adres wystawcy lokalnego nie zostanie określony [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) , a adres wystawcy określony przez WSFederationHttpBinding > lub inne powiązanie federacyjne to <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` ,`http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, lub jest `null`, używany jest wystawca programu Windows CardSpace.</span><span class="sxs-lookup"><span data-stu-id="0d4f6-108">If the <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> property of the `ClientCredentials` class is set to `true`, a local issuer address is not specified, and the issuer address specified by the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) or other federated binding is `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, or is `null`, then the Windows CardSpace issuer is used.</span></span>

## <a name="to-configure-the-local-issuer-in-code"></a><span data-ttu-id="0d4f6-109">Aby skonfigurować wystawcy lokalnego w kodzie</span><span class="sxs-lookup"><span data-stu-id="0d4f6-109">To configure the local issuer in code</span></span>

1. <span data-ttu-id="0d4f6-110">Utwórz zmienną typu<xref:System.ServiceModel.Security.IssuedTokenClientCredential></span><span class="sxs-lookup"><span data-stu-id="0d4f6-110">Create a variable of type <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>

2. <span data-ttu-id="0d4f6-111">Ustaw zmienną na wystąpienie zwracane z <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> właściwości `ClientCredentials` klasy.</span><span class="sxs-lookup"><span data-stu-id="0d4f6-111">Set the variable to the instance returned from the <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> property of the `ClientCredentials` class.</span></span> <span data-ttu-id="0d4f6-112">To wystąpienie <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> jest zwracane przez właściwość klienta (dziedziczone z <xref:System.ServiceModel.ClientBase%601>) <xref:System.ServiceModel.ChannelFactory>lub <xref:System.ServiceModel.ChannelFactory.Credentials%2A> Właściwość:</span><span class="sxs-lookup"><span data-stu-id="0d4f6-112">That instance is returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the client (inherited from <xref:System.ServiceModel.ClientBase%601>) or the <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property of the <xref:System.ServiceModel.ChannelFactory>:</span></span>

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. <span data-ttu-id="0d4f6-113">Ustaw właściwość na nowe wystąpienie <xref:System.ServiceModel.EndpointAddress>elementu, z adresem wystawcy lokalnego jako argumentem konstruktora. <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A></span><span class="sxs-lookup"><span data-stu-id="0d4f6-113">Set the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> property to a new instance of the <xref:System.ServiceModel.EndpointAddress>, with the address of the local issuer as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     <span data-ttu-id="0d4f6-114">Alternatywnie Utwórz nowe <xref:System.Uri> wystąpienie jako argument konstruktora.</span><span class="sxs-lookup"><span data-stu-id="0d4f6-114">Alternatively, create a new <xref:System.Uri> instance as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     <span data-ttu-id="0d4f6-115">Parametr jest tablicą <xref:System.ServiceModel.Channels.AddressHeader>wystąpień `addressHeaders` , jak pokazano.</span><span class="sxs-lookup"><span data-stu-id="0d4f6-115">The `addressHeaders` parameter is an array of <xref:System.ServiceModel.Channels.AddressHeader> instances, as shown.</span></span>

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. <span data-ttu-id="0d4f6-116">Ustaw powiązanie dla wystawcy lokalnego przy użyciu <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d4f6-116">Set the binding for the local issuer using the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. <span data-ttu-id="0d4f6-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0d4f6-117">Optional.</span></span> <span data-ttu-id="0d4f6-118">Dodaj skonfigurowane zachowania punktu końcowego dla wystawcy lokalnego przez dodanie takich zachowań do kolekcji zwróconej <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> przez właściwość.</span><span class="sxs-lookup"><span data-stu-id="0d4f6-118">Add configured endpoint behaviors for the local issuer by adding such behaviors to the collection returned by the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a><span data-ttu-id="0d4f6-119">Aby skonfigurować wystawcę lokalnego w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0d4f6-119">To configure the local issuer in configuration</span></span>

1. <span data-ttu-id="0d4f6-120">Utwórz element [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) LocalIssuer > jako obiekt podrzędny elementu issuedToken >, który jest samym elementem podrzędnym elementu ClientCredentials > w zachowaniu punktu końcowego. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)</span><span class="sxs-lookup"><span data-stu-id="0d4f6-120">Create a [\<localIssuer>](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) element as a child of the [\<issuedToken>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element that is itself a child of the [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element in an endpoint behavior.</span></span>

2. <span data-ttu-id="0d4f6-121">Ustaw wartość `address` atrybutu na adres wystawcy lokalnego, która będzie akceptować żądania tokenów.</span><span class="sxs-lookup"><span data-stu-id="0d4f6-121">Set the `address` attribute to the address of the local issuer that will accept token requests.</span></span>

3. <span data-ttu-id="0d4f6-122">Ustaw atrybuty `bindingConfiguration` i na wartości, które odwołują się do odpowiedniego powiązania do użycia podczas komunikacji z punktem końcowym wystawcy lokalnego. `binding`</span><span class="sxs-lookup"><span data-stu-id="0d4f6-122">Set the `binding` and `bindingConfiguration` attributes to values that reference the appropriate binding to use when communicating with the local issuer endpoint.</span></span>

4. <span data-ttu-id="0d4f6-123">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0d4f6-123">Optional.</span></span> <span data-ttu-id="0d4f6-124">Ustaw >`localIssuer`tożsamość elementu jako element podrzędny < > elementu i Określ informacje o tożsamości dla wystawcy lokalnego. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)</span><span class="sxs-lookup"><span data-stu-id="0d4f6-124">Set the [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element as a child of the <`localIssuer`> element and specify identity information for the local issuer.</span></span>

5. <span data-ttu-id="0d4f6-125">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0d4f6-125">Optional.</span></span> <span data-ttu-id="0d4f6-126">`localIssuer` [ Ustawnagłówki>elementujakoelementpodrzędny<>elementuiokreśldodatkowenagłówki,któresąwymaganewceluprawidłowegoadresowania\<](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="0d4f6-126">Set the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element as a child of the <`localIssuer`> element and specify additional headers that are required in order to correctly address the local issuer.</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="0d4f6-127">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="0d4f6-127">.NET Framework Security</span></span>

<span data-ttu-id="0d4f6-128">Należy pamiętać, że jeśli dla danego powiązania określono adres wystawcy i powiązanie, wystawcy lokalnego nie jest używany dla punktów końcowych używających tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="0d4f6-128">Note that if an issuer address and binding are specified for a given binding, the local issuer is not used for endpoints that use that binding.</span></span> <span data-ttu-id="0d4f6-129">Klienci, którzy oczekują zawsze używać wystawcy lokalnego, powinni upewnić się, że nie używają takiego powiązania lub że modyfikują powiązanie, tak aby adres `null`wystawcy był.</span><span class="sxs-lookup"><span data-stu-id="0d4f6-129">Clients who expect to always use the local issuer should ensure that they do not use such a binding or that they modify the binding so that the issuer address is `null`.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d4f6-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d4f6-130">See also</span></span>

- [<span data-ttu-id="0d4f6-131">Instrukcje: Konfigurowanie poświadczeń na usługa federacyjna</span><span class="sxs-lookup"><span data-stu-id="0d4f6-131">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="0d4f6-132">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="0d4f6-132">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="0d4f6-133">Instrukcje: Utwórz WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="0d4f6-133">How to: Create a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
