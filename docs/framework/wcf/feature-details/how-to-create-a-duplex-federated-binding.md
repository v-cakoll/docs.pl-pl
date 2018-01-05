---
title: "Instrukcje: Tworzenie dwukierunkowego powiązania federacyjnego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d40d13ca861cd18cf5f2a72e94d1aca146c2c19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="27e40-102">Instrukcje: Tworzenie dwukierunkowego powiązania federacyjnego</span><span class="sxs-lookup"><span data-stu-id="27e40-102">How to: Create a Duplex Federated Binding</span></span>
<span data-ttu-id="27e40-103"><xref:System.ServiceModel.WSFederationHttpBinding>obsługuje tylko kontraktami wymiany wiadomość datagramu i żądanie/odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="27e40-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="27e40-104">Aby użyć kontraktu dwustronnego wiadomości programu exchange, należy utworzyć niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="27e40-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="27e40-105">Poniższe procedury pokazują, jak to zrobić w konfiguracji przy użyciu wiadomości tryb zabezpieczeń dla transportu HTTP i TCP i zabezpieczeń w trybie mieszanym dla transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="27e40-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="27e40-106">Przykładowy kod, przedstawiający wszystkie powiązania 3 znajduje się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="27e40-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>  
  
 <span data-ttu-id="27e40-107">Można również utworzyć powiązanie w kodzie.</span><span class="sxs-lookup"><span data-stu-id="27e40-107">You can also create the binding in code.</span></span> <span data-ttu-id="27e40-108">Opis stosu powiązania elementów do tworzenia, zobacz [porady: Tworzenie powiązań niestandardowych za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="27e40-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="27e40-109">Aby utworzyć dwukierunkowego powiązania federacyjnego niestandardowych za pomocą protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="27e40-109">To create a duplex federated custom binding with HTTP</span></span>  
  
1.  <span data-ttu-id="27e40-110">W [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) węzła pliku konfiguracji, Utwórz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="27e40-110">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>  
  
2.  <span data-ttu-id="27e40-111">Wewnątrz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu, Utwórz [ \<powiązania >](../../../../docs/framework/misc/binding.md) element z `name` ustawić atrybutu `FederationDuplexHttpMessageSecurityBinding`.</span><span class="sxs-lookup"><span data-stu-id="27e40-111">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>  
  
3.  <span data-ttu-id="27e40-112">Wewnątrz [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu, Utwórz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element z `authenticationMode` ustawić atrybutu `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="27e40-112">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>  
  
4.  <span data-ttu-id="27e40-113">Wewnątrz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, Utwórz [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element z `authenticationMode` ustawić atrybutu `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="27e40-113">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>  
  
5.  <span data-ttu-id="27e40-114">Po [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, Utwórz pustą [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="27e40-114">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>  
  
6.  <span data-ttu-id="27e40-115">Po [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) elementu, Utwórz pustą [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="27e40-115">Following the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element.</span></span>  
  
7.  <span data-ttu-id="27e40-116">Po [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) elementu, Utwórz pustą [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="27e40-116">Following the [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.</span></span>  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="27e40-117">Aby utworzyć dwukierunkowego powiązania federacyjnego niestandardowych za pomocą trybu zabezpieczenia wiadomości TCP</span><span class="sxs-lookup"><span data-stu-id="27e40-117">To create a duplex federated custom binding with TCP message security mode</span></span>  
  
1.  <span data-ttu-id="27e40-118">W [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) węzła pliku konfiguracji, Utwórz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="27e40-118">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>   
  
2.  <span data-ttu-id="27e40-119">Wewnątrz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu, Utwórz [ \<powiązania >](../../../../docs/framework/misc/binding.md) element z `name` ustawić atrybutu `FederationDuplexTcpMessageSecurityBinding`.</span><span class="sxs-lookup"><span data-stu-id="27e40-119">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>  
  
3.  <span data-ttu-id="27e40-120">Wewnątrz [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu, Utwórz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element z `authenticationMode` ustawić atrybutu `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="27e40-120">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>  
  
4.  <span data-ttu-id="27e40-121">Wewnątrz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, Utwórz [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element z `authenticationMode` ustawić atrybutu `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="27e40-121">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>  
  
5.  <span data-ttu-id="27e40-122">Po [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, Utwórz pustą [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="27e40-122">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="27e40-123">Aby utworzyć dupleks federacyjnych niestandardowego powiązania protokołu TCP w trybie mieszanym zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="27e40-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>  
  
1.  <span data-ttu-id="27e40-124">W [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) węzła pliku konfiguracji, Utwórz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="27e40-124">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>   
  
2.  <span data-ttu-id="27e40-125">Wewnątrz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu, Utwórz [ \<powiązania >](../../../../docs/framework/misc/binding.md) element z `name` ustawić atrybutu `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span><span class="sxs-lookup"><span data-stu-id="27e40-125">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>  
  
3.  <span data-ttu-id="27e40-126">Wewnątrz [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu, Utwórz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element z `authenticationMode` ustawić atrybutu `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="27e40-126">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>  
  
4.  <span data-ttu-id="27e40-127">Wewnątrz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, Utwórz [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element z `authenticationMode` ustawić atrybutu `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="27e40-127">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>  
  
5.  <span data-ttu-id="27e40-128">Po [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, Utwórz pustą [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="27e40-128">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>  
  
6.  <span data-ttu-id="27e40-129">Po [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) elementu, Utwórz pustą [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="27e40-129">Following the [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>  
  
## <a name="code-sample"></a><span data-ttu-id="27e40-130">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="27e40-130">Code Sample</span></span>  
  
#### <a name="sample-with-3-bindings"></a><span data-ttu-id="27e40-131">Przykładowe z powiązaniami 3</span><span class="sxs-lookup"><span data-stu-id="27e40-131">Sample with 3 Bindings</span></span>  
  
1.  <span data-ttu-id="27e40-132">Wstaw następujący kod do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="27e40-132">Insert the following code into your configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27e40-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="27e40-133">Example</span></span>  
  
```xml  
<bindings>  
   <customBinding>  
      <binding name="FederationDuplexHttpMessageSecurityBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />  
          </security>  
          <compositeDuplex />  
          <oneWay />  
          <httpTransport />  
       </binding>  
<!-- duplex over https is not supported -->  
       <binding name="FederationDuplexTcpMessageSecurityBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />  
          </security>  
          <tcpTransport />  
       </binding>              
       <binding name="FederationDuplexTcpTransportSecurityWithMessageCredentialsBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenOverTransport" />  
          </security>  
<!-- requireClientCertificate = true or <windowsStreamSecurity /> can be used, but does not make sense for most scenarios -->  
          <sslStreamSecurity />  
          <tcpTransport />  
       </binding>              
    </customBinding>  
</bindings>  
```
