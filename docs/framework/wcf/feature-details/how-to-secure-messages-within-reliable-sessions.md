---
title: 'Instrukcje: Zabezpieczanie komunikatów w sesjach niezawodnych'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
author: BrucePerlerMS
ms.openlocfilehash: f3269dc96dee2d534a8dd6677abeb6afae8776bd
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47115102"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="0655f-102">Instrukcje: Zabezpieczanie komunikatów w sesjach niezawodnych</span><span class="sxs-lookup"><span data-stu-id="0655f-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="0655f-103">W tym temacie opisano kroki wymagane w celu umożliwienia zabezpieczenia na poziomie komunikatu dla komunikatów wymienianych w ramach niezawodnej sesji przy użyciu jednej z powiązań dostarczanych przez system, które obsługują sesji programu, ale nie domyślnie.</span><span class="sxs-lookup"><span data-stu-id="0655f-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="0655f-104">Włącz bezpieczne i niezawodne sesji obowiązkowo przy użyciu kodu lub deklaratywnie w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0655f-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="0655f-105">Ta procedura używa plików konfiguracji klienta i usługi, aby umożliwić bezpieczne i niezawodne sesji.</span><span class="sxs-lookup"><span data-stu-id="0655f-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="0655f-106">Ta procedura obejmuje następujące trzy kluczowe zadania:</span><span class="sxs-lookup"><span data-stu-id="0655f-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="0655f-107">Określ, czy klient i usługa wymiana komunikatów w ramach niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="0655f-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="0655f-108">Wymagaj zabezpieczenia na poziomie komunikatu w ramach niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="0655f-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="0655f-109">Określanie typu poświadczeń klienta, który klient musi używać uwierzytelniania za pomocą usługi.</span><span class="sxs-lookup"><span data-stu-id="0655f-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="0655f-110">Jest ważne w pierwszym zadaniu, który zawiera element konfiguracji punktu końcowego `bindingConfiguration` atrybut, który odwołuje się do konfiguracji powiązania o nazwie (w tym przykładzie) `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="0655f-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="0655f-111">[  **\<Powiązania >** ](../../../../docs/framework/misc/binding.md) element konfiguracji odwołuje się następnie tę nazwę, aby włączyć niezawodnej sesji przez ustawienie `enabled` atrybutu [  **\<reliableSession >** ](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) elementu `true`.</span><span class="sxs-lookup"><span data-stu-id="0655f-111">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element to `true`.</span></span> <span data-ttu-id="0655f-112">Możesz wymagać, że gwarancje dostarczenia uporządkowane są dostępne w ramach sesji niezawodnej, ustawiając `ordered` atrybutu `true`.</span><span class="sxs-lookup"><span data-stu-id="0655f-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="0655f-113">Dla źródła kopii przykładu, na którym opiera się poniższą procedurę konfiguracji, zobacz [sesja niezawodna WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="0655f-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="0655f-114">Podstawowe elementy drugie zadanie podrzędne są realizowane przez ustawienie `mode` atrybutu  **\<zabezpieczeń >** elementów znajdujących się w  **\<powiązania >** Element klienta i usługi w celu `Message`.</span><span class="sxs-lookup"><span data-stu-id="0655f-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="0655f-115">Podstawowe elementy trzeci zadania są wykonywane przez ustawienie `clientCredentialType` atrybutu  **\<komunikatu >** elementów znajdujących się w  **\<zabezpieczeń >** Element klienta i usługi w celu `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="0655f-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="0655f-116">Korzystanie z zabezpieczeń komunikatów za pomocą sesji niezawodnych, niezawodną obsługę komunikatów próbuje uwierzytelnić klienta nieuwierzytelnione, dopóki nie zostanie przekroczony limit czasu zamiast zgłaszać wyjątek po pierwszym niepowodzeniu.</span><span class="sxs-lookup"><span data-stu-id="0655f-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="0655f-117">Konfigurowanie usługi przy użyciu WSHttpBinding używać niezawodnej sesji</span><span class="sxs-lookup"><span data-stu-id="0655f-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="0655f-118">Ta procedura jest opisana w [instrukcje: wymiana komunikatów w ramach niezawodnej sesji](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="0655f-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="0655f-119">Konfigurowanie klienta za pomocą WSHttpBinding używać niezawodnej sesji</span><span class="sxs-lookup"><span data-stu-id="0655f-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="0655f-120">Ta procedura jest opisana w [instrukcje: wymiana komunikatów w ramach niezawodnej sesji](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="0655f-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="0655f-121">Ustaw tryb i właściwości ClientCredentialType o wartości w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0655f-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="0655f-122">Dodaj odpowiednie powiązanie elementu [  **\<powiązania >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0655f-122">Add an appropriate binding element to the [**\<bindings>**](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="0655f-123">W poniższym przykładzie dodano [  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="0655f-123">The following example adds a [**\<wsHttpBinding>**](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="0655f-124">Dodaj  **\<powiązania >** element i ustaw jego `name` atrybutu do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="0655f-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="0655f-125">W przykładzie użyto nazwy `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="0655f-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="0655f-126">Dodaj  **\<zabezpieczeń >** element i ustaw `mode` atrybutu `Message`.</span><span class="sxs-lookup"><span data-stu-id="0655f-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="0655f-127">W ramach  **\<zabezpieczeń >** elementu Dodawanie  **\<komunikat >** element i ustaw `clientCredentialType` atrybutu `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="0655f-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
