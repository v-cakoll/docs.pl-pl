---
title: "4802 — DiscoveryClientProtocolExceptionSuppressed"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 568212f7-1060-4f5c-a7a0-1352c7cc743b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecb147e35b830322240f69f533de7a588064e9d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="4802---discoveryclientprotocolexceptionsuppressed"></a><span data-ttu-id="430c0-102">4802 — DiscoveryClientProtocolExceptionSuppressed</span><span class="sxs-lookup"><span data-stu-id="430c0-102">4802 - DiscoveryClientProtocolExceptionSuppressed</span></span>
## <a name="properties"></a><span data-ttu-id="430c0-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="430c0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="430c0-104">ID</span><span class="sxs-lookup"><span data-stu-id="430c0-104">ID</span></span>|<span data-ttu-id="430c0-105">4802</span><span class="sxs-lookup"><span data-stu-id="430c0-105">4802</span></span>|  
|<span data-ttu-id="430c0-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="430c0-106">Keywords</span></span>|<span data-ttu-id="430c0-107">Odnajdywanie</span><span class="sxs-lookup"><span data-stu-id="430c0-107">Discovery</span></span>|  
|<span data-ttu-id="430c0-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="430c0-108">Level</span></span>|<span data-ttu-id="430c0-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="430c0-109">Information</span></span>|  
|<span data-ttu-id="430c0-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="430c0-110">Channel</span></span>|<span data-ttu-id="430c0-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="430c0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="430c0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="430c0-112">Description</span></span>  
 <span data-ttu-id="430c0-113">To zdarzenie jest emitowany podczas pominięto wyjątek protokołu podczas zamykania obiektu DiscoveryClient.</span><span class="sxs-lookup"><span data-stu-id="430c0-113">This event is emitted when the a ProtocolException was suppressed while closing the DiscoveryClient.</span></span>  
  
## <a name="message"></a><span data-ttu-id="430c0-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="430c0-114">Message</span></span>  
 <span data-ttu-id="430c0-115">Pominięto wyjątek protokołu podczas zamykania obiektu DiscoveryClient.</span><span class="sxs-lookup"><span data-stu-id="430c0-115">A ProtocolException was suppressed while closing the DiscoveryClient.</span></span> <span data-ttu-id="430c0-116">Może to być spowodowane obiekt DiscoveryService nadal próbuje wysłać odpowiedź do obiektu DiscoveryClient.</span><span class="sxs-lookup"><span data-stu-id="430c0-116">This could be because a DiscoveryService is still trying to send response to the DiscoveryClient.</span></span>  
  
## <a name="details"></a><span data-ttu-id="430c0-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="430c0-117">Details</span></span>
