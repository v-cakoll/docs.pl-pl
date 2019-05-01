---
title: 'Instrukcje: zabezpieczanie komunikatów w sesjach niezawodnych'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: ee35f2a36ca08814423b5a3d0b1432bacd28c2e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973007"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="ade39-102">Instrukcje: zabezpieczanie komunikatów w sesjach niezawodnych</span><span class="sxs-lookup"><span data-stu-id="ade39-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="ade39-103">W tym temacie opisano kroki wymagane w celu umożliwienia zabezpieczenia na poziomie komunikatu dla komunikatów wymienianych w ramach niezawodnej sesji przy użyciu jednej z powiązań dostarczanych przez system, które obsługują sesji programu, ale nie domyślnie.</span><span class="sxs-lookup"><span data-stu-id="ade39-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="ade39-104">Włącz bezpieczne i niezawodne sesji obowiązkowo przy użyciu kodu lub deklaratywnie w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ade39-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="ade39-105">Ta procedura używa plików konfiguracji klienta i usługi, aby umożliwić bezpieczne i niezawodne sesji.</span><span class="sxs-lookup"><span data-stu-id="ade39-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="ade39-106">Ta procedura obejmuje następujące trzy kluczowe zadania:</span><span class="sxs-lookup"><span data-stu-id="ade39-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="ade39-107">Określ, czy klient i usługa wymiana komunikatów w ramach niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="ade39-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="ade39-108">Wymagaj zabezpieczenia na poziomie komunikatu w ramach niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="ade39-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="ade39-109">Określanie typu poświadczeń klienta, który klient musi używać uwierzytelniania za pomocą usługi.</span><span class="sxs-lookup"><span data-stu-id="ade39-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="ade39-110">Jest ważne w pierwszym zadaniu, który zawiera element konfiguracji punktu końcowego `bindingConfiguration` atrybut, który odwołuje się do konfiguracji powiązania o nazwie (w tym przykładzie) `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="ade39-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="ade39-111">[  **\<Powiązania >** ](../../../../docs/framework/misc/binding.md) element konfiguracji odwołuje się następnie tę nazwę, aby włączyć niezawodnej sesji przez ustawienie `enabled` atrybutu [  **\<reliableSession >** ](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) elementu `true`.</span><span class="sxs-lookup"><span data-stu-id="ade39-111">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) element to `true`.</span></span> <span data-ttu-id="ade39-112">Możesz wymagać, że gwarancje dostarczenia uporządkowane są dostępne w ramach sesji niezawodnej, ustawiając `ordered` atrybutu `true`.</span><span class="sxs-lookup"><span data-stu-id="ade39-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="ade39-113">Dla źródła kopii przykładu, na którym opiera się poniższą procedurę konfiguracji, zobacz [sesja niezawodna WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="ade39-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="ade39-114">Podstawowe elementy drugie zadanie podrzędne są realizowane przez ustawienie `mode` atrybutu  **\<zabezpieczeń >** elementów znajdujących się w  **\<powiązania >** Element klienta i usługi w celu `Message`.</span><span class="sxs-lookup"><span data-stu-id="ade39-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="ade39-115">Podstawowe elementy trzeci zadania są wykonywane przez ustawienie `clientCredentialType` atrybutu  **\<komunikatu >** elementów znajdujących się w  **\<zabezpieczeń >** Element klienta i usługi w celu `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="ade39-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="ade39-116">Korzystanie z zabezpieczeń komunikatów za pomocą sesji niezawodnych, niezawodną obsługę komunikatów próbuje uwierzytelnić klienta nieuwierzytelnione, dopóki nie zostanie przekroczony limit czasu zamiast zgłaszać wyjątek po pierwszym niepowodzeniu.</span><span class="sxs-lookup"><span data-stu-id="ade39-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="ade39-117">Konfigurowanie usługi przy użyciu WSHttpBinding używać niezawodnej sesji</span><span class="sxs-lookup"><span data-stu-id="ade39-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="ade39-118">Ta procedura jest opisana w [jak: Wymiana komunikatów w ramach sesji niezawodnej](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="ade39-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="ade39-119">Konfigurowanie klienta za pomocą WSHttpBinding używać niezawodnej sesji</span><span class="sxs-lookup"><span data-stu-id="ade39-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="ade39-120">Ta procedura jest opisana w [jak: Wymiana komunikatów w ramach sesji niezawodnej](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="ade39-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="ade39-121">Ustaw tryb i właściwości ClientCredentialType o wartości w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ade39-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="ade39-122">Dodaj odpowiednie powiązanie elementu [  **\<powiązania >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ade39-122">Add an appropriate binding element to the [**\<bindings>**](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="ade39-123">W poniższym przykładzie dodano [  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="ade39-123">The following example adds a [**\<wsHttpBinding>**](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="ade39-124">Dodaj  **\<powiązania >** element i ustaw jego `name` atrybutu do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="ade39-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="ade39-125">W przykładzie użyto nazwy `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="ade39-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="ade39-126">Dodaj  **\<zabezpieczeń >** element i ustaw `mode` atrybutu `Message`.</span><span class="sxs-lookup"><span data-stu-id="ade39-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="ade39-127">W ramach  **\<zabezpieczeń >** elementu Dodawanie  **\<komunikat >** element i ustaw `clientCredentialType` atrybutu `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="ade39-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
