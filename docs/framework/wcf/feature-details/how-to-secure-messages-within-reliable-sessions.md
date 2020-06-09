---
title: 'Instrukcje: Zabezpieczanie komunikatów w sesjach niezawodnych'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: 306d0f96b5163fe5c24d270b4b9a7c1d3f499e7e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596958"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="cab65-102">Instrukcje: Zabezpieczanie komunikatów w sesjach niezawodnych</span><span class="sxs-lookup"><span data-stu-id="cab65-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="cab65-103">W tym temacie opisano kroki wymagane do włączenia zabezpieczeń na poziomie komunikatów dla komunikatów wymienianych w ramach niezawodnej sesji przy użyciu jednego z powiązań dostarczonych przez system, które obsługują taką sesję, ale nie domyślnie.</span><span class="sxs-lookup"><span data-stu-id="cab65-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="cab65-104">W razie potrzeby Włącz bezpieczną, niezawodną sesję przy użyciu kodu lub deklaratywnie w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cab65-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="cab65-105">Ta procedura powoduje użycie plików konfiguracji klienta i usługi w celu włączenia bezpiecznej, niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="cab65-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="cab65-106">Ta procedura obejmuje następujące trzy kluczowe zadania:</span><span class="sxs-lookup"><span data-stu-id="cab65-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="cab65-107">Określ, że komunikaty programu Exchange klienta i usługi będą należeć do niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="cab65-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="cab65-108">Wymagaj zabezpieczeń na poziomie wiadomości w ramach niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="cab65-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="cab65-109">Określ typ poświadczeń klienta, który ma być używany przez klienta do uwierzytelniania w usłudze.</span><span class="sxs-lookup"><span data-stu-id="cab65-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="cab65-110">Ważne jest, aby najpierw wykonać pierwsze zadanie, że element konfiguracji punktu końcowego zawiera `bindingConfiguration` atrybut odwołujący się do konfiguracji powiązania o nazwie (w tym przykładzie) `MessageSecurity` .</span><span class="sxs-lookup"><span data-stu-id="cab65-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="cab65-111">[**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Element Configuration następnie odwołuje się do tej nazwy, aby umożliwić niezawodne sesje przez ustawienie `enabled` atrybutu [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) elementu na `true` .</span><span class="sxs-lookup"><span data-stu-id="cab65-111">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) element to `true`.</span></span> <span data-ttu-id="cab65-112">Można wymagać, aby uporządkowane gwarancje dostarczania były dostępne w ramach niezawodnej sesji przez ustawienie `ordered` atrybutu na `true` .</span><span class="sxs-lookup"><span data-stu-id="cab65-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="cab65-113">Aby uzyskać kopię źródłową przykładowej procedury konfiguracji, zobacz [sesja niezawodna WS](../samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="cab65-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="cab65-114">Najważniejsze elementy drugiego zadania są wykonywane przez ustawienie `mode` atrybutu **\<security>** elementu zawartego w **\<binding>** elemencie klienta i usługi do `Message` .</span><span class="sxs-lookup"><span data-stu-id="cab65-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="cab65-115">Najważniejsze elementy trzeciego zadania są realizowane przez ustawienie `clientCredentialType` atrybutu **\<message>** elementu zawartego w **\<security>** elemencie klienta i usługi do `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="cab65-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="cab65-116">W przypadku korzystania z zabezpieczeń komunikatów z niezawodnymi sesjami niezawodna komunikacja próbuje uwierzytelnić nieuwierzytelniony klient do momentu wystąpienia limitu czasu, zamiast zgłaszać wyjątek przy pierwszym błędzie.</span><span class="sxs-lookup"><span data-stu-id="cab65-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="cab65-117">Konfigurowanie usługi za pomocą WSHttpBinding do korzystania z niezawodnej sesji</span><span class="sxs-lookup"><span data-stu-id="cab65-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="cab65-118">Ta procedura została opisana w artykule [How to: Exchange messages w niezawodnej sesji](how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="cab65-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="cab65-119">Konfigurowanie klienta z WSHttpBinding do korzystania z niezawodnej sesji</span><span class="sxs-lookup"><span data-stu-id="cab65-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="cab65-120">Ta procedura została opisana w artykule [How to: Exchange messages w niezawodnej sesji](how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="cab65-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="cab65-121">Ustawianie trybu i wartości ClientCredentialtype w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="cab65-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="cab65-122">Dodaj odpowiedni element powiązania do elementu w [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cab65-122">Add an appropriate binding element to the [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="cab65-123">Poniższy przykład dodaje [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="cab65-123">The following example adds a [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="cab65-124">Dodaj **\<binding>** element i ustaw jego `name` atrybut na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="cab65-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="cab65-125">W przykładzie używa się nazwy `MessageSecurity` .</span><span class="sxs-lookup"><span data-stu-id="cab65-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="cab65-126">Dodaj **\<security>** element i ustaw `mode` atrybut na `Message` .</span><span class="sxs-lookup"><span data-stu-id="cab65-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="cab65-127">W **\<security>** elemencie Dodaj **\<message>** element i ustaw `clientCredentialType` atrybut na `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="cab65-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
