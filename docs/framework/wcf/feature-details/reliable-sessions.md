---
title: Niezawodne sesje
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 659309ff5560480c423fc9b0adab5e93eac05ce5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-sessions"></a><span data-ttu-id="bfdc6-102">Niezawodne sesje</span><span class="sxs-lookup"><span data-stu-id="bfdc6-102">Reliable Sessions</span></span>

<span data-ttu-id="bfdc6-103">W tej sekcji opisano, co [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] niezawodna sesja jest jego przeznaczenia, jak i kiedy do korzystania z jednego, jakie konfiguracjami powiązań z jego obsługi i wskaźnikami na najlepszych rozwiązaniach dotyczących.</span><span class="sxs-lookup"><span data-stu-id="bfdc6-103">This section describes what a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="bfdc6-104">W poniższej tabeli przedstawiono szczegółowe informacje o podstawowych punktów i Tematy pokrewne w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="bfdc6-104">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="bfdc6-105">Niezawodna sesja [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewnia featrues zapewnienie, że komunikaty wysyłane między punktami końcowymi są transferowane za pośrednictwem pośredników SOAP lub transportu i są dostarczane tylko raz i, opcjonalnie, w tej samej kolejności, w jakiej zostały wysłane.</span><span class="sxs-lookup"><span data-stu-id="bfdc6-105">The reliable session [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides featrues ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="bfdc6-106">Aby użyć niezawodnej sesji z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji, albo użyj jednej z powiązania dostarczane przez system w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] niezawodnej sesji obsługuje, domyślnie lub opcjonalnie lub tworzenia własnego niestandardowego powiązania, który obsługuje sesji.</span><span class="sxs-lookup"><span data-stu-id="bfdc6-106">To use a reliable session with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, either use one of the system-provided bindings in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="bfdc6-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="bfdc6-107">In This Section</span></span>

<span data-ttu-id="bfdc6-108">[Omówienie sesji niezawodnych](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="bfdc6-108">[Reliable Sessions Overview](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) </span></span>  
<span data-ttu-id="bfdc6-109">Opisuje niezawodnej sesji, kiedy należy używać ich różnych powiązań, które obsługuje niezawodnej sesji, i jak działają.</span><span class="sxs-lookup"><span data-stu-id="bfdc6-109">Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="bfdc6-110">[Porady: wymiana komunikatów w ramach niezawodnej sesji](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) </span><span class="sxs-lookup"><span data-stu-id="bfdc6-110">[How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) </span></span>  
<span data-ttu-id="bfdc6-111">Opisuje sposób utworzenia niezawodnej sesji przez protokół HTTP przy użyciu niestandardowego powiązania określony w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bfdc6-111">Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="bfdc6-112">[Porady: Zabezpieczanie komunikatów w sesjach niezawodnych](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="bfdc6-112">[How to: Secure Messages within Reliable Sessions](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) </span></span>  
<span data-ttu-id="bfdc6-113">Opis sposobu zabezpieczania niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="bfdc6-113">Describes how to secure a reliable session.</span></span>

<span data-ttu-id="bfdc6-114">[Porady: tworzenie powiązania niestandardowego niezawodnej sesji z protokołu HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) </span><span class="sxs-lookup"><span data-stu-id="bfdc6-114">[How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) </span></span>  
<span data-ttu-id="bfdc6-115">Opisuje sposób utworzenia niezawodnej sesji przez protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bfdc6-115">Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="bfdc6-116">[Najlepsze rozwiązania dotyczące sesji niezawodnych](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="bfdc6-116">[Best Practices for Reliable Sessions](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) </span></span>  
<span data-ttu-id="bfdc6-117">Opis niektórych najlepszych praktyk związanych z użyciem niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="bfdc6-117">Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="bfdc6-118">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="bfdc6-118">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="bfdc6-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bfdc6-119">See Also</span></span>

<span data-ttu-id="bfdc6-120">[Kolejki i sesje niezawodne](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="bfdc6-120">[Queues and Reliable Sessions](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md) </span></span>  
[<span data-ttu-id="bfdc6-121">Sesje, tworzenie wystąpień i współbieżność</span><span class="sxs-lookup"><span data-stu-id="bfdc6-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
