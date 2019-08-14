---
title: 'Instrukcje: tworzenie dwukierunkowego wiązania federacyjnego'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 71c970fa45d7d4ccd55fceddb2360d0aa0a768f8
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972060"
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="d4bd3-102">Instrukcje: tworzenie dwukierunkowego wiązania federacyjnego</span><span class="sxs-lookup"><span data-stu-id="d4bd3-102">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="d4bd3-103"><xref:System.ServiceModel.WSFederationHttpBinding>obsługuje tylko kontrakty wymiany dla komunikatów datagram i Request/Reply.</span><span class="sxs-lookup"><span data-stu-id="d4bd3-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="d4bd3-104">Aby można było korzystać z kontraktu programu Exchange z wiadomościami dwustronnymi, należy utworzyć niestandardowe powiązanie.</span><span class="sxs-lookup"><span data-stu-id="d4bd3-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="d4bd3-105">Poniższe procedury pokazują, jak to zrobić w konfiguracji, przy użyciu zabezpieczeń trybu komunikatów dla transportów HTTP i TCP oraz przy użyciu zabezpieczeń w trybie mieszanym do transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="d4bd3-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="d4bd3-106">Przykładowy kod pokazujący wszystkie 3 powiązania znajduje się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d4bd3-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="d4bd3-107">Możesz również utworzyć powiązanie w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d4bd3-107">You can also create the binding in code.</span></span> <span data-ttu-id="d4bd3-108">Opis stosu elementów powiązania do utworzenia znajduje się w temacie [How to: Utwórz niestandardowe powiązanie przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="d4bd3-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="d4bd3-109">Aby utworzyć niestandardowe powiązanie federacyjne z protokołem HTTP</span><span class="sxs-lookup"><span data-stu-id="d4bd3-109">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="d4bd3-110">W węźle powiązania > [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) pliku konfiguracji Utwórz niestandardowy element >Binding. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d4bd3-110">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="d4bd3-111">W elemencie CustomBinding `name` > Utwórz element `FederationDuplexHttpMessageSecurityBinding` [ >powiązaniazatrybutemustawionymna.\<](../../../../docs/framework/misc/binding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="d4bd3-111">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="d4bd3-112">`authenticationMode` `SecureConversation` [ Wewnątrz\<elementu](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ Binding>Utwórzelement>zabezpieczeńz\<](../../../../docs/framework/misc/binding.md) atrybutem ustawionym na.</span><span class="sxs-lookup"><span data-stu-id="d4bd3-112">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="d4bd3-113">`IssuedTokenForCertificate` `authenticationMode` `IssuedTokenForSslNegotiated` [ Wewnątrz\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ elementu>zabezpieczeńUtwórzelement>secureConversationBootstrapzatrybutem\<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) ustawionym na lub.</span><span class="sxs-lookup"><span data-stu-id="d4bd3-113">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="d4bd3-114">Po elemencie [> zabezpieczeńUtwórzpustyelement>compositeDuplex.\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)</span><span class="sxs-lookup"><span data-stu-id="d4bd3-114">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="d4bd3-115">Po elemencie [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) compositeDuplex > Utwórz pusty element > oneWay. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)</span><span class="sxs-lookup"><span data-stu-id="d4bd3-115">Following the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="d4bd3-116">Po elemencie [> oneWayUtwórzpustyelement>httpTransport.\<](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)</span><span class="sxs-lookup"><span data-stu-id="d4bd3-116">Following the [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="d4bd3-117">Aby utworzyć niestandardowe powiązanie federacyjne z trybem zabezpieczeń wiadomości TCP</span><span class="sxs-lookup"><span data-stu-id="d4bd3-117">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="d4bd3-118">W węźle powiązania > [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) pliku konfiguracji Utwórz niestandardowy element >Binding. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d4bd3-118">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="d4bd3-119">W elemencie CustomBinding `name` > Utwórz element `FederationDuplexTcpMessageSecurityBinding` [ >powiązaniazatrybutemustawionymna.\<](../../../../docs/framework/misc/binding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="d4bd3-119">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="d4bd3-120">`authenticationMode` `SecureConversation` [ Wewnątrz\<elementu](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ Binding>Utwórzelement>zabezpieczeńz\<](../../../../docs/framework/misc/binding.md) atrybutem ustawionym na.</span><span class="sxs-lookup"><span data-stu-id="d4bd3-120">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="d4bd3-121">`IssuedTokenForCertificate` `authenticationMode` `IssuedTokenForSslNegotiated` [ Wewnątrz\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ elementu>zabezpieczeńUtwórzelement>secureConversationBootstrapzatrybutem\<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) ustawionym na lub.</span><span class="sxs-lookup"><span data-stu-id="d4bd3-121">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="d4bd3-122">Po elemencie [> zabezpieczeńUtwórzpustyelement>tcpTransport.\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md)</span><span class="sxs-lookup"><span data-stu-id="d4bd3-122">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="d4bd3-123">Aby utworzyć niestandardowe powiązanie federacyjne z trybem mieszanym protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="d4bd3-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="d4bd3-124">W węźle powiązania > [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) pliku konfiguracji Utwórz niestandardowy element >Binding. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d4bd3-124">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="d4bd3-125">W elemencie CustomBinding `name` > Utwórz element `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` [ >powiązaniazatrybutemustawionymna.\<](../../../../docs/framework/misc/binding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="d4bd3-125">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="d4bd3-126">`authenticationMode` `SecureConversation` [ Wewnątrz\<elementu](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ Binding>Utwórzelement>zabezpieczeńz\<](../../../../docs/framework/misc/binding.md) atrybutem ustawionym na.</span><span class="sxs-lookup"><span data-stu-id="d4bd3-126">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="d4bd3-127">`IssuedTokenForCertificate` `authenticationMode` `IssuedTokenForSslNegotiated` [ Wewnątrz\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ elementu>zabezpieczeńUtwórzelement>secureConversationBootstrapzatrybutem\<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) ustawionym na lub.</span><span class="sxs-lookup"><span data-stu-id="d4bd3-127">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="d4bd3-128">Po elemencie [> zabezpieczeńUtwórzpustyelement>sslStreamSecurity.\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</span><span class="sxs-lookup"><span data-stu-id="d4bd3-128">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="d4bd3-129">Po sslStreamSecurity elementu > Utwórz pusty [ \<element tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) . [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</span><span class="sxs-lookup"><span data-stu-id="d4bd3-129">Following the [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="d4bd3-130">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="d4bd3-130">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="d4bd3-131">Przykład z 3 powiązaniami</span><span class="sxs-lookup"><span data-stu-id="d4bd3-131">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="d4bd3-132">Wstaw następujący kod do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d4bd3-132">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="d4bd3-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="d4bd3-133">Example</span></span>

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
