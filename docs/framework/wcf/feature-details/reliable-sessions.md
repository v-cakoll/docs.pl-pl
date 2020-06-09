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
ms.openlocfilehash: 910ad952192243c6aa8a79417ad711d8c2a4ba2e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590543"
---
# <a name="reliable-sessions"></a><span data-ttu-id="4c612-102">Niezawodne sesje</span><span class="sxs-lookup"><span data-stu-id="4c612-102">Reliable Sessions</span></span>

<span data-ttu-id="4c612-103">W tej sekcji opisano, co to jest Niezawodna sesja programu Windows Communication Foundation (WCF), co jest używane przez program, jak i kiedy należy z nich korzystać, jakie konfiguracje powiązań obsługują i jakie są wskaźniki najlepszych rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="4c612-103">This section describes what a Windows Communication Foundation (WCF) reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="4c612-104">Poniższa tabela zawiera podsumowanie szczegółowych informacji o najważniejszych punktach i powiązanych tematach w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="4c612-104">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="4c612-105">Funkcja WCF dla niezawodnej sesji zapewnia funkcje zapewniające, że komunikaty wysyłane między punktami końcowymi są przesyłane przez wystawcy protokołu SOAP lub transportu i są dostarczane tylko raz i, opcjonalnie, w takiej samej kolejności, w jakiej zostały wysłane.</span><span class="sxs-lookup"><span data-stu-id="4c612-105">The reliable session WCF provides features ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="4c612-106">Aby używać niezawodnej sesji z aplikacją WCF, użyj jednego z powiązań dostarczonych przez system w programie WCF, który domyślnie obsługuje niezawodną sesję lub jako opcję, lub Utwórz własne niestandardowe powiązanie, które obsługuje daną sesję.</span><span class="sxs-lookup"><span data-stu-id="4c612-106">To use a reliable session with a WCF application, either use one of the system-provided bindings in WCF that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4c612-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="4c612-107">In This Section</span></span>

<span data-ttu-id="4c612-108">[Omówienie sesji niezawodnych](reliable-sessions-overview.md) Opisuje niezawodne sesje, gdy ich używać, różne powiązania, które obsługują niezawodne sesje i jak działają.</span><span class="sxs-lookup"><span data-stu-id="4c612-108">[Reliable Sessions Overview](reliable-sessions-overview.md) Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="4c612-109">[Instrukcje: Wymiana komunikatów w ramach niezawodnej sesji](how-to-exchange-messages-within-a-reliable-session.md) Opisuje sposób tworzenia niezawodnej sesji za pośrednictwem protokołu HTTP przy użyciu niestandardowego powiązania określonego w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4c612-109">[How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md) Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="4c612-110">[Instrukcje: Zabezpieczanie komunikatów w ramach sesji niezawodnych](how-to-secure-messages-within-reliable-sessions.md) Opisuje sposób zabezpieczania niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="4c612-110">[How to: Secure Messages within Reliable Sessions](how-to-secure-messages-within-reliable-sessions.md) Describes how to secure a reliable session.</span></span>

<span data-ttu-id="4c612-111">[Instrukcje: Tworzenie niestandardowego powiązania niezawodnej sesji z protokołem HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md) Opisuje sposób tworzenia niezawodnej sesji za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4c612-111">[How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md) Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="4c612-112">[Najlepsze rozwiązania dotyczące niezawodnych sesji](best-practices-for-reliable-sessions.md) W tym artykule opisano niektóre najlepsze rozwiązania związane z używaniem niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="4c612-112">[Best Practices for Reliable Sessions](best-practices-for-reliable-sessions.md) Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="4c612-113">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="4c612-113">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="4c612-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c612-114">See also</span></span>

- [<span data-ttu-id="4c612-115">Kolejki i sesje niezawodne</span><span class="sxs-lookup"><span data-stu-id="4c612-115">Queues and Reliable Sessions</span></span>](queues-and-reliable-sessions.md)
- [<span data-ttu-id="4c612-116">Sesje, tworzenie wystąpień i współbieżność</span><span class="sxs-lookup"><span data-stu-id="4c612-116">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)
