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
ms.openlocfilehash: 3fb4577e6a79bc6b42cb0ef6f24648d1b016214f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713253"
---
# <a name="how-to-configure-a-local-issuer"></a><span data-ttu-id="ea351-102">Instrukcje: Konfigurowanie lokalnego wystawcy</span><span class="sxs-lookup"><span data-stu-id="ea351-102">How to: Configure a Local Issuer</span></span>
<span data-ttu-id="ea351-103">W tym temacie opisano sposób konfigurowania klienta do używania wystawcy lokalnego dla wystawionych tokenów.</span><span class="sxs-lookup"><span data-stu-id="ea351-103">This topic describes how to configure a client to use a local issuer for issued tokens.</span></span>  
  
 <span data-ttu-id="ea351-104">Często gdy klient komunikuje się z usługi federacyjnej, usługi Określa adres zabezpieczeń, które usługi tokenu, który oczekuje się, aby wystawić token klient użyje do samodzielnego uwierzytelnienia usługi federacyjnej.</span><span class="sxs-lookup"><span data-stu-id="ea351-104">Often, when a client communicates with a federated service, the service specifies the address of the security token service that is expected to issue the token the client will use to authenticate itself to the federated service.</span></span> <span data-ttu-id="ea351-105">W niektórych przypadkach klient może być skonfigurowany do użycia *wystawcy lokalnego*.</span><span class="sxs-lookup"><span data-stu-id="ea351-105">In certain situations, the client may be configured to use a *local issuer*.</span></span>  
  
 <span data-ttu-id="ea351-106">Windows Communication Foundation (WCF) używa wystawcy lokalnego w przypadkach, gdy jest adres wystawcy powiązania federacyjnego `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` lub `null`.</span><span class="sxs-lookup"><span data-stu-id="ea351-106">Windows Communication Foundation (WCF) uses a local issuer in cases where the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`.</span></span> <span data-ttu-id="ea351-107">W takich przypadkach należy skonfigurować <xref:System.ServiceModel.Description.ClientCredentials> za pomocą adresu lokalnego wystawcy i powiązanie, aby używać do komunikowania się z tym wystawcą.</span><span class="sxs-lookup"><span data-stu-id="ea351-107">In such cases, you must configure the <xref:System.ServiceModel.Description.ClientCredentials> with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea351-108">Jeśli <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> właściwość `ClientCredentials` klasy jest ustawiona na `true`, adres wystawcy lokalnego nie jest określony, i Wystawca adres podany przez [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) lub innych powiązania federacyjnego jest `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, lub `null`, następnie Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] wystawcy jest używany.</span><span class="sxs-lookup"><span data-stu-id="ea351-108">If the <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> property of the `ClientCredentials` class is set to `true`, a local issuer address is not specified, and the issuer address specified by the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) or other federated binding is `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, or is `null`, then the Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] issuer is used.</span></span>  
  
### <a name="to-configure-the-local-issuer-in-code"></a><span data-ttu-id="ea351-109">Aby skonfigurować wystawcy lokalnego w kodzie</span><span class="sxs-lookup"><span data-stu-id="ea351-109">To configure the local issuer in code</span></span>  
  
1.  <span data-ttu-id="ea351-110">Utwórz zmienną typu <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span><span class="sxs-lookup"><span data-stu-id="ea351-110">Create a variable of type <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>  
  
2.  <span data-ttu-id="ea351-111">Ustaw zmienną na wystąpienie zwrócone w wyniku <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> właściwość `ClientCredentials` klasy.</span><span class="sxs-lookup"><span data-stu-id="ea351-111">Set the variable to the instance returned from the <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> property of the `ClientCredentials` class.</span></span> <span data-ttu-id="ea351-112">To wystąpienie jest zwracany przez <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwość klienta (odziedziczone <xref:System.ServiceModel.ClientBase%601>) lub <xref:System.ServiceModel.ChannelFactory.Credentials%2A> właściwość <xref:System.ServiceModel.ChannelFactory>:</span><span class="sxs-lookup"><span data-stu-id="ea351-112">That instance is returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the client (inherited from <xref:System.ServiceModel.ClientBase%601>) or the <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property of the <xref:System.ServiceModel.ChannelFactory>:</span></span>  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
3.  <span data-ttu-id="ea351-113">Ustaw <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> właściwość nowe wystąpienie klasy <xref:System.ServiceModel.EndpointAddress>, przy użyciu adresu wystawcy lokalnego jako argumentu do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="ea351-113">Set the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> property to a new instance of the <xref:System.ServiceModel.EndpointAddress>, with the address of the local issuer as an argument to the constructor.</span></span>  
  
     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]  
  
     <span data-ttu-id="ea351-114">Alternatywnie, Utwórz nową <xref:System.Uri> wystąpienie jako argument do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="ea351-114">Alternatively, create a new <xref:System.Uri> instance as an argument to the constructor.</span></span>  
  
     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]  
  
     <span data-ttu-id="ea351-115">`addressHeaders` Parametr jest tablicą <xref:System.ServiceModel.Channels.AddressHeader> wystąpień, jak pokazano.</span><span class="sxs-lookup"><span data-stu-id="ea351-115">The `addressHeaders` parameter is an array of <xref:System.ServiceModel.Channels.AddressHeader> instances, as shown.</span></span>  
  
     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]  
  
4.  <span data-ttu-id="ea351-116">Ustaw powiązanie wystawcy lokalnego przy użyciu <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ea351-116">Set the binding for the local issuer using the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> property.</span></span>  
  
     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]  
  
5.  <span data-ttu-id="ea351-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="ea351-117">Optional.</span></span> <span data-ttu-id="ea351-118">Dodawanie zachowania punktu końcowego skonfigurowanego dla wystawcy lokalnego, dodając takie zachowania do kolekcji zwróconej przez <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ea351-118">Add configured endpoint behaviors for the local issuer by adding such behaviors to the collection returned by the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> property.</span></span>  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-local-issuer-in-configuration"></a><span data-ttu-id="ea351-119">Konfigurowanie lokalnego wystawcy w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ea351-119">To configure the local issuer in configuration</span></span>  
  
1.  <span data-ttu-id="ea351-120">Tworzenie [ \<localIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) element jako element podrzędny elementu [ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element, który jest elementem podrzędnym [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu w zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ea351-120">Create a [\<localIssuer>](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) element as a child of the [\<issuedToken>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element that is itself a child of the [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element in an endpoint behavior.</span></span>  
  
2.  <span data-ttu-id="ea351-121">Ustaw `address` atrybutu adres wystawcy lokalnego, która będzie akceptować żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="ea351-121">Set the `address` attribute to the address of the local issuer that will accept token requests.</span></span>  
  
3.  <span data-ttu-id="ea351-122">Ustaw `binding` i `bindingConfiguration` atrybuty wartości, które odwołują się odpowiednie powiązanie do użycia przy komunikacji z punktem końcowym wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="ea351-122">Set the `binding` and `bindingConfiguration` attributes to values that reference the appropriate binding to use when communicating with the local issuer endpoint.</span></span>  
  
4.  <span data-ttu-id="ea351-123">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="ea351-123">Optional.</span></span> <span data-ttu-id="ea351-124">Ustaw [ \<tożsamości >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element jako element podrzędny <`localIssuer`> element i określ informacje o tożsamości dla wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="ea351-124">Set the [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element as a child of the <`localIssuer`> element and specify identity information for the local issuer.</span></span>  
  
5.  <span data-ttu-id="ea351-125">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="ea351-125">Optional.</span></span> <span data-ttu-id="ea351-126">Ustaw [ \<nagłówki >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element jako element podrzędny <`localIssuer`> element i określić dodatkowych nagłówków, które są wymagane do prawidłowego adresowania wystawcy lokalnego.</span><span class="sxs-lookup"><span data-stu-id="ea351-126">Set the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element as a child of the <`localIssuer`> element and specify additional headers that are required in order to correctly address the local issuer.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ea351-127">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="ea351-127">.NET Framework Security</span></span>  
 <span data-ttu-id="ea351-128">Należy pamiętać, że jeśli wystawcy adres i powiązanie są określone dla danego powiązania, wystawcy lokalnego nie jest używany dla punktów końcowych, korzystające z tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="ea351-128">Note that if an issuer address and binding are specified for a given binding, the local issuer is not used for endpoints that use that binding.</span></span> <span data-ttu-id="ea351-129">Klienci, którzy oczekują zawsze używaj wystawcy lokalnego należy upewnić się, że nie używaj takiego powiązania lub mogą modyfikować powiązania tak, aby adres wystawcy jest `null`.</span><span class="sxs-lookup"><span data-stu-id="ea351-129">Clients who expect to always use the local issuer should ensure that they do not use such a binding or that they modify the binding so that the issuer address is `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea351-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea351-130">See also</span></span>
- [<span data-ttu-id="ea351-131">Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej</span><span class="sxs-lookup"><span data-stu-id="ea351-131">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="ea351-132">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="ea351-132">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="ea351-133">Instrukcje: Tworzenie elementu WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="ea351-133">How to: Create a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
