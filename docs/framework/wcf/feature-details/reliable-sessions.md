---
title: Niezawodne sesje
ms.date: 03/30/2017
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
ms.openlocfilehash: 9a2cd06c4c5a73d9fb5c4c7f09632e10c3eb0d87
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991162"
---
# <a name="reliable-sessions"></a><span data-ttu-id="db7a1-102">Niezawodne sesje</span><span class="sxs-lookup"><span data-stu-id="db7a1-102">Reliable Sessions</span></span>

<span data-ttu-id="db7a1-103">W tej sekcji opisano, jakie Windows Communication Foundation (WCF) jest niezawodnej sesji, jego przeznaczenie, jak i kiedy Aby użyć jednego, jakie konfiguracje powiązań z jego obsługi, a wskaźników na najlepsze rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="db7a1-103">This section describes what a Windows Communication Foundation (WCF) reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="db7a1-104">W poniższej tabeli przedstawiono szczegółowe informacje o podstawowych punktów i Tematy pokrewne w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="db7a1-104">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="db7a1-105">Sesja niezawodna WCF zapewnia funkcje zagwarantowanie, że komunikaty wysyłane między punktami końcowymi są przenoszone między pośredników SOAP lub transportu i są dostarczane tylko raz i, opcjonalnie, w tej samej kolejności, w jakiej zostały wysłane.</span><span class="sxs-lookup"><span data-stu-id="db7a1-105">The reliable session WCF provides features ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="db7a1-106">Niezawodnej sesji za pomocą aplikacji WCF, użyj jednej z powiązań dostarczanych przez system w usłudze WCF, które obsługują niezawodnej sesji, domyślnie lub jako opcja lub utworzyć własne niestandardowe powiązanie, które obsługuje sesji.</span><span class="sxs-lookup"><span data-stu-id="db7a1-106">To use a reliable session with a WCF application, either use one of the system-provided bindings in WCF that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="db7a1-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="db7a1-107">In This Section</span></span>

<span data-ttu-id="db7a1-108">[Omówienie sesji niezawodnych](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) opisano niezawodne sesje, kiedy należy używać ich różnych powiązań, które obsługuje sesji uwierzytelnianych i sposobie ich działania.</span><span class="sxs-lookup"><span data-stu-id="db7a1-108">[Reliable Sessions Overview](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="db7a1-109">[Instrukcje: Wymiana komunikatów w ramach niezawodnej sesji](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) w tym artykule opisano sposób tworzenia niezawodnej sesji za pośrednictwem protokołu HTTP przy użyciu niestandardowego powiązania, określona w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="db7a1-109">[How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="db7a1-110">[Instrukcje: Zabezpieczanie komunikatów w sesjach niezawodnych](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) w tym artykule opisano sposób zabezpieczania niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="db7a1-110">[How to: Secure Messages within Reliable Sessions](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) Describes how to secure a reliable session.</span></span>

<span data-ttu-id="db7a1-111">[Instrukcje: Tworzenie niestandardowego niezawodnej sesji powiązania przy użyciu protokołu HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) w tym artykule opisano sposób tworzenia niezawodnej sesji za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="db7a1-111">[How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="db7a1-112">[Najlepsze rozwiązania dotyczące sesji niezawodnych](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) opisuje niektóre najlepsze rozwiązania związane z używaniem niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="db7a1-112">[Best Practices for Reliable Sessions](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="db7a1-113">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="db7a1-113">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="db7a1-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db7a1-114">See also</span></span>

- [<span data-ttu-id="db7a1-115">Kolejki i sesje niezawodne</span><span class="sxs-lookup"><span data-stu-id="db7a1-115">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
- [<span data-ttu-id="db7a1-116">Sesje, tworzenie wystąpień i współbieżność</span><span class="sxs-lookup"><span data-stu-id="db7a1-116">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
