---
title: 'Instrukcje: Tworzenie dwukierunkowego powiązania federacyjnego'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: e93651ce9fe9dae55c299fcb061da6bdc4b6bc5e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598973"
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="0d54b-102">Instrukcje: Tworzenie dwukierunkowego powiązania federacyjnego</span><span class="sxs-lookup"><span data-stu-id="0d54b-102">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="0d54b-103"><xref:System.ServiceModel.WSFederationHttpBinding>obsługuje tylko kontrakty wymiany dla komunikatów datagram i Request/Reply.</span><span class="sxs-lookup"><span data-stu-id="0d54b-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="0d54b-104">Aby można było korzystać z kontraktu programu Exchange z wiadomościami dwustronnymi, należy utworzyć niestandardowe powiązanie.</span><span class="sxs-lookup"><span data-stu-id="0d54b-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="0d54b-105">Poniższe procedury pokazują, jak to zrobić w konfiguracji, przy użyciu zabezpieczeń trybu komunikatów dla transportów HTTP i TCP oraz przy użyciu zabezpieczeń w trybie mieszanym do transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="0d54b-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="0d54b-106">Przykładowy kod pokazujący wszystkie 3 powiązania znajduje się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="0d54b-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="0d54b-107">Możesz również utworzyć powiązanie w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0d54b-107">You can also create the binding in code.</span></span> <span data-ttu-id="0d54b-108">Opis stosu elementów powiązania do utworzenia znajduje się w temacie [How to: Create a Custom Binding using the elementu SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="0d54b-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="0d54b-109">Aby utworzyć niestandardowe powiązanie federacyjne z protokołem HTTP</span><span class="sxs-lookup"><span data-stu-id="0d54b-109">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="0d54b-110">W [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) węźle pliku konfiguracji Utwórz [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="0d54b-110">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="0d54b-111">Wewnątrz [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) elementu Utwórz [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element z `name` atrybutem ustawionym na `FederationDuplexHttpMessageSecurityBinding` .</span><span class="sxs-lookup"><span data-stu-id="0d54b-111">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="0d54b-112">Wewnątrz [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elementu Utwórz [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element z `authenticationMode` atrybutem ustawionym na `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="0d54b-112">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="0d54b-113">Wewnątrz [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elementu Utwórz [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element z `authenticationMode` atrybutem ustawionym na `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="0d54b-113">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="0d54b-114">Po [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elemencie Utwórz pusty [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element.</span><span class="sxs-lookup"><span data-stu-id="0d54b-114">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="0d54b-115">Po [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) elemencie Utwórz pusty [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element.</span><span class="sxs-lookup"><span data-stu-id="0d54b-115">Following the [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="0d54b-116">Po [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) elemencie Utwórz pusty [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) element.</span><span class="sxs-lookup"><span data-stu-id="0d54b-116">Following the [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="0d54b-117">Aby utworzyć niestandardowe powiązanie federacyjne z trybem zabezpieczeń wiadomości TCP</span><span class="sxs-lookup"><span data-stu-id="0d54b-117">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="0d54b-118">W [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) węźle pliku konfiguracji Utwórz [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="0d54b-118">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="0d54b-119">Wewnątrz [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) elementu Utwórz [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element z `name` atrybutem ustawionym na `FederationDuplexTcpMessageSecurityBinding` .</span><span class="sxs-lookup"><span data-stu-id="0d54b-119">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="0d54b-120">Wewnątrz [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elementu Utwórz [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element z `authenticationMode` atrybutem ustawionym na `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="0d54b-120">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="0d54b-121">Wewnątrz [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elementu Utwórz [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element z `authenticationMode` atrybutem ustawionym na `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="0d54b-121">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="0d54b-122">Po [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elemencie Utwórz pusty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span><span class="sxs-lookup"><span data-stu-id="0d54b-122">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="0d54b-123">Aby utworzyć niestandardowe powiązanie federacyjne z trybem mieszanym protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="0d54b-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="0d54b-124">W [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) węźle pliku konfiguracji Utwórz [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="0d54b-124">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="0d54b-125">Wewnątrz [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) elementu Utwórz [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element z `name` atrybutem ustawionym na `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` .</span><span class="sxs-lookup"><span data-stu-id="0d54b-125">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="0d54b-126">Wewnątrz [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elementu Utwórz [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element z `authenticationMode` atrybutem ustawionym na `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="0d54b-126">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="0d54b-127">Wewnątrz [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elementu Utwórz [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element z `authenticationMode` atrybutem ustawionym na `IssuedTokenForCertificate` lub `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="0d54b-127">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="0d54b-128">Po [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elemencie Utwórz pusty [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span><span class="sxs-lookup"><span data-stu-id="0d54b-128">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="0d54b-129">Po [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) elemencie Utwórz pusty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span><span class="sxs-lookup"><span data-stu-id="0d54b-129">Following the [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="0d54b-130">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="0d54b-130">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="0d54b-131">Przykład z 3 powiązaniami</span><span class="sxs-lookup"><span data-stu-id="0d54b-131">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="0d54b-132">Wstaw następujący kod do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0d54b-132">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="0d54b-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="0d54b-133">Example</span></span>

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
