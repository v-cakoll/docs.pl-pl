---
title: 'Instrukcje: Konfigurowanie lokalnego wystawcy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
ms.openlocfilehash: 7da3cd34d0840eea48c9ef0bb89fb6580b87623b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601247"
---
# <a name="how-to-configure-a-local-issuer"></a><span data-ttu-id="7b6bd-102">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="7b6bd-102">How to: Configure a Local Issuer</span></span>

<span data-ttu-id="7b6bd-103">W tym temacie opisano sposób konfigurowania klienta do używania lokalnego wystawcy dla wystawionych tokenów.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-103">This topic describes how to configure a client to use a local issuer for issued tokens.</span></span>

<span data-ttu-id="7b6bd-104">Często, gdy klient komunikuje się z usługą federacyjną, usługa określa adres usługi tokenu zabezpieczającego, która powinna wydać token używany przez klienta do samodzielnego uwierzytelnienia w usłudze federacyjnej.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-104">Often, when a client communicates with a federated service, the service specifies the address of the security token service that is expected to issue the token the client will use to authenticate itself to the federated service.</span></span> <span data-ttu-id="7b6bd-105">W niektórych sytuacjach klient może być skonfigurowany do korzystania z *lokalnego wystawcy*.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-105">In certain situations, the client may be configured to use a *local issuer*.</span></span>

<span data-ttu-id="7b6bd-106">Windows Communication Foundation (WCF) używa wystawcy lokalnego w przypadkach, gdy adres wystawcy powiązania federacyjnego to `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` lub `null` .</span><span class="sxs-lookup"><span data-stu-id="7b6bd-106">Windows Communication Foundation (WCF) uses a local issuer in cases where the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`.</span></span> <span data-ttu-id="7b6bd-107">W takich przypadkach należy skonfigurować <xref:System.ServiceModel.Description.ClientCredentials> program przy użyciu adresu wystawcy lokalnego i powiązania, które ma być używane do komunikacji z tym wystawcą.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-107">In such cases, you must configure the <xref:System.ServiceModel.Description.ClientCredentials> with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>

> [!NOTE]
> <span data-ttu-id="7b6bd-108">Jeśli <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> Właściwość `ClientCredentials` klasy jest ustawiona na `true` , adres wystawcy lokalnego nie zostanie określony, a adres wystawcy określony przez [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) lub inne powiązanie federacyjne to `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` , `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` , lub jest `null` , używany jest wystawca programu Windows CardSpace.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-108">If the <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> property of the `ClientCredentials` class is set to `true`, a local issuer address is not specified, and the issuer address specified by the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) or other federated binding is `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, or is `null`, then the Windows CardSpace issuer is used.</span></span>

## <a name="to-configure-the-local-issuer-in-code"></a><span data-ttu-id="7b6bd-109">Aby skonfigurować wystawcy lokalnego w kodzie</span><span class="sxs-lookup"><span data-stu-id="7b6bd-109">To configure the local issuer in code</span></span>

1. <span data-ttu-id="7b6bd-110">Utwórz zmienną typu<xref:System.ServiceModel.Security.IssuedTokenClientCredential></span><span class="sxs-lookup"><span data-stu-id="7b6bd-110">Create a variable of type <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>

2. <span data-ttu-id="7b6bd-111">Ustaw zmienną na wystąpienie zwracane z <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> właściwości `ClientCredentials` klasy.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-111">Set the variable to the instance returned from the <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> property of the `ClientCredentials` class.</span></span> <span data-ttu-id="7b6bd-112">To wystąpienie jest zwracane przez <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Właściwość klienta (dziedziczone z <xref:System.ServiceModel.ClientBase%601> ) lub <xref:System.ServiceModel.ChannelFactory.Credentials%2A> Właściwość <xref:System.ServiceModel.ChannelFactory> :</span><span class="sxs-lookup"><span data-stu-id="7b6bd-112">That instance is returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the client (inherited from <xref:System.ServiceModel.ClientBase%601>) or the <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property of the <xref:System.ServiceModel.ChannelFactory>:</span></span>

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. <span data-ttu-id="7b6bd-113">Ustaw <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> Właściwość na nowe wystąpienie elementu <xref:System.ServiceModel.EndpointAddress> , z adresem wystawcy lokalnego jako argumentem konstruktora.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-113">Set the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> property to a new instance of the <xref:System.ServiceModel.EndpointAddress>, with the address of the local issuer as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     <span data-ttu-id="7b6bd-114">Alternatywnie Utwórz nowe <xref:System.Uri> wystąpienie jako argument konstruktora.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-114">Alternatively, create a new <xref:System.Uri> instance as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     <span data-ttu-id="7b6bd-115">`addressHeaders`Parametr jest tablicą <xref:System.ServiceModel.Channels.AddressHeader> wystąpień, jak pokazano.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-115">The `addressHeaders` parameter is an array of <xref:System.ServiceModel.Channels.AddressHeader> instances, as shown.</span></span>

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. <span data-ttu-id="7b6bd-116">Ustaw powiązanie dla wystawcy lokalnego przy użyciu <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-116">Set the binding for the local issuer using the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. <span data-ttu-id="7b6bd-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-117">Optional.</span></span> <span data-ttu-id="7b6bd-118">Dodaj skonfigurowane zachowania punktu końcowego dla wystawcy lokalnego przez dodanie takich zachowań do kolekcji zwróconej przez <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-118">Add configured endpoint behaviors for the local issuer by adding such behaviors to the collection returned by the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a><span data-ttu-id="7b6bd-119">Aby skonfigurować wystawcę lokalnego w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7b6bd-119">To configure the local issuer in configuration</span></span>

1. <span data-ttu-id="7b6bd-120">Utwórz [\<localIssuer>](../../configure-apps/file-schema/wcf/localissuer.md) element jako obiekt podrzędny [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) elementu, który jest elementem podrzędnym [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) elementu w zachowaniu punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-120">Create a [\<localIssuer>](../../configure-apps/file-schema/wcf/localissuer.md) element as a child of the [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) element that is itself a child of the [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) element in an endpoint behavior.</span></span>

2. <span data-ttu-id="7b6bd-121">Ustaw wartość `address` atrybutu na adres wystawcy lokalnego, która będzie akceptować żądania tokenów.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-121">Set the `address` attribute to the address of the local issuer that will accept token requests.</span></span>

3. <span data-ttu-id="7b6bd-122">Ustaw `binding` atrybuty i `bindingConfiguration` na wartości, które odwołują się do odpowiedniego powiązania do użycia podczas komunikacji z punktem końcowym wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-122">Set the `binding` and `bindingConfiguration` attributes to values that reference the appropriate binding to use when communicating with the local issuer endpoint.</span></span>

4. <span data-ttu-id="7b6bd-123">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-123">Optional.</span></span> <span data-ttu-id="7b6bd-124">Ustaw [\<identity>](../../configure-apps/file-schema/wcf/identity.md) jako element podrzędny <`localIssuer` elementu> i Określ informacje o tożsamości dla wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-124">Set the [\<identity>](../../configure-apps/file-schema/wcf/identity.md) element as a child of the <`localIssuer`> element and specify identity information for the local issuer.</span></span>

5. <span data-ttu-id="7b6bd-125">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-125">Optional.</span></span> <span data-ttu-id="7b6bd-126">Ustaw [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element jako obiekt podrzędny <`localIssuer` elementu> i określ dodatkowe nagłówki, które są wymagane w celu prawidłowego adresowania wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-126">Set the [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element as a child of the <`localIssuer`> element and specify additional headers that are required in order to correctly address the local issuer.</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="7b6bd-127">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="7b6bd-127">.NET Framework Security</span></span>

<span data-ttu-id="7b6bd-128">Należy pamiętać, że jeśli dla danego powiązania określono adres wystawcy i powiązanie, wystawcy lokalnego nie jest używany dla punktów końcowych używających tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="7b6bd-128">Note that if an issuer address and binding are specified for a given binding, the local issuer is not used for endpoints that use that binding.</span></span> <span data-ttu-id="7b6bd-129">Klienci, którzy oczekują zawsze używać wystawcy lokalnego, powinni upewnić się, że nie używają takiego powiązania lub że modyfikują powiązanie, tak aby adres wystawcy był `null` .</span><span class="sxs-lookup"><span data-stu-id="7b6bd-129">Clients who expect to always use the local issuer should ensure that they do not use such a binding or that they modify the binding so that the issuer address is `null`.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b6bd-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b6bd-130">See also</span></span>

- [<span data-ttu-id="7b6bd-131">Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej</span><span class="sxs-lookup"><span data-stu-id="7b6bd-131">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="7b6bd-132">Instrukcje: tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="7b6bd-132">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)
- [<span data-ttu-id="7b6bd-133">Instrukcje: tworzenie elementu WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="7b6bd-133">How to: Create a WSFederationHttpBinding</span></span>](how-to-create-a-wsfederationhttpbinding.md)
