---
title: 'Instrukcje: Tworzenie dwukierunkowego powiązania federacyjnego'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 3ecd9e2dbeb30bb255cbf66488b50a9b20219431
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141721"
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="15fb8-102">Instrukcje: Tworzenie dwukierunkowego powiązania federacyjnego</span><span class="sxs-lookup"><span data-stu-id="15fb8-102">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="15fb8-103"><xref:System.ServiceModel.WSFederationHttpBinding> obsługuje tylko kontrakty wymiany dla komunikatów datagram i Request/Reply.</span><span class="sxs-lookup"><span data-stu-id="15fb8-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="15fb8-104">Aby można było korzystać z kontraktu programu Exchange z wiadomościami dwustronnymi, należy utworzyć niestandardowe powiązanie.</span><span class="sxs-lookup"><span data-stu-id="15fb8-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="15fb8-105">Poniższe procedury pokazują, jak to zrobić w konfiguracji, przy użyciu zabezpieczeń trybu komunikatów dla transportów HTTP i TCP oraz przy użyciu zabezpieczeń w trybie mieszanym do transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="15fb8-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="15fb8-106">Przykładowy kod pokazujący wszystkie 3 powiązania znajduje się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="15fb8-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="15fb8-107">Możesz również utworzyć powiązanie w kodzie.</span><span class="sxs-lookup"><span data-stu-id="15fb8-107">You can also create the binding in code.</span></span> <span data-ttu-id="15fb8-108">Opis stosu elementów powiązania do utworzenia znajduje się w temacie [How to: Create a Custom Binding using the elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="15fb8-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="15fb8-109">Aby utworzyć niestandardowe powiązanie federacyjne z protokołem HTTP</span><span class="sxs-lookup"><span data-stu-id="15fb8-109">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="15fb8-110">W węźle [\<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji utwórz element [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="15fb8-110">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="15fb8-111">Wewnątrz elementu [\<custombinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) utwórz element [> powiązania\<](../../configure-apps/file-schema/wcf/bindings.md) z atrybutem `name` ustawionym na `FederationDuplexHttpMessageSecurityBinding`.</span><span class="sxs-lookup"><span data-stu-id="15fb8-111">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="15fb8-112">Wewnątrz elementu [\<binding >](../../configure-apps/file-schema/wcf/bindings.md) utwórz element [\<Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) z atrybutem `authenticationMode` ustawionym na `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="15fb8-112">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="15fb8-113">Wewnątrz elementu [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) utwórz element [\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) z atrybutem `authenticationMode` ustawionym na `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="15fb8-113">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="15fb8-114">Po elemencie [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) utwórz pusty [\<elementu > compositeDuplex](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) .</span><span class="sxs-lookup"><span data-stu-id="15fb8-114">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="15fb8-115">Po elemencie [\<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) utwórz pusty [\<element > oneWay](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) .</span><span class="sxs-lookup"><span data-stu-id="15fb8-115">Following the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="15fb8-116">Po elemencie [\<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) utwórz pusty [\<elementu > httpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) .</span><span class="sxs-lookup"><span data-stu-id="15fb8-116">Following the [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="15fb8-117">Aby utworzyć niestandardowe powiązanie federacyjne z trybem zabezpieczeń wiadomości TCP</span><span class="sxs-lookup"><span data-stu-id="15fb8-117">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="15fb8-118">W węźle [\<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji utwórz element [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="15fb8-118">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="15fb8-119">Wewnątrz elementu [\<custombinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) utwórz element [> powiązania\<](../../configure-apps/file-schema/wcf/bindings.md) z atrybutem `name` ustawionym na `FederationDuplexTcpMessageSecurityBinding`.</span><span class="sxs-lookup"><span data-stu-id="15fb8-119">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="15fb8-120">Wewnątrz elementu [\<binding >](../../configure-apps/file-schema/wcf/bindings.md) utwórz element [\<Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) z atrybutem `authenticationMode` ustawionym na `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="15fb8-120">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="15fb8-121">Wewnątrz elementu [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) utwórz element [\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) z atrybutem `authenticationMode` ustawionym na `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="15fb8-121">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="15fb8-122">Po elemencie [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) utwórz pusty [\<elementu > tcpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) .</span><span class="sxs-lookup"><span data-stu-id="15fb8-122">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="15fb8-123">Aby utworzyć niestandardowe powiązanie federacyjne z trybem mieszanym protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="15fb8-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="15fb8-124">W węźle [\<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji utwórz element [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="15fb8-124">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="15fb8-125">Wewnątrz elementu [\<custombinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) utwórz element [> powiązania\<](../../configure-apps/file-schema/wcf/bindings.md) z atrybutem `name` ustawionym na `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span><span class="sxs-lookup"><span data-stu-id="15fb8-125">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="15fb8-126">Wewnątrz elementu [\<binding >](../../configure-apps/file-schema/wcf/bindings.md) utwórz element [\<Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) z atrybutem `authenticationMode` ustawionym na `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="15fb8-126">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="15fb8-127">Wewnątrz elementu [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) utwórz element [\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) z atrybutem `authenticationMode` ustawionym na `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="15fb8-127">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="15fb8-128">Po elemencie [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) utwórz pusty [\<elementu > sslStreamSecurity](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) .</span><span class="sxs-lookup"><span data-stu-id="15fb8-128">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="15fb8-129">Po elemencie [\<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) Utwórz pusty element [\<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) .</span><span class="sxs-lookup"><span data-stu-id="15fb8-129">Following the [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="15fb8-130">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="15fb8-130">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="15fb8-131">Przykład z 3 powiązaniami</span><span class="sxs-lookup"><span data-stu-id="15fb8-131">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="15fb8-132">Wstaw następujący kod do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="15fb8-132">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="15fb8-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="15fb8-133">Example</span></span>

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
