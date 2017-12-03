---
title: 4207 - MaximumRetriesExceededForSqlCommand
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c8bee26-9ad4-4e01-bd16-0e1fd510fb6b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1708cba44a4afc22635a039f7868a9ffbf41fc37
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="4207---maximumretriesexceededforsqlcommand"></a><span data-ttu-id="061f9-102">4207 - MaximumRetriesExceededForSqlCommand</span><span class="sxs-lookup"><span data-stu-id="061f9-102">4207 - MaximumRetriesExceededForSqlCommand</span></span>
## <a name="properties"></a><span data-ttu-id="061f9-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="061f9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="061f9-104">ID</span><span class="sxs-lookup"><span data-stu-id="061f9-104">ID</span></span>|<span data-ttu-id="061f9-105">4207</span><span class="sxs-lookup"><span data-stu-id="061f9-105">4207</span></span>|  
|<span data-ttu-id="061f9-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="061f9-106">Keywords</span></span>|<span data-ttu-id="061f9-107">Limit przydziału, WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="061f9-107">Quota, WFInstanceStore</span></span>|  
|<span data-ttu-id="061f9-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="061f9-108">Level</span></span>|<span data-ttu-id="061f9-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="061f9-109">Information</span></span>|  
|<span data-ttu-id="061f9-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="061f9-110">Channel</span></span>|<span data-ttu-id="061f9-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="061f9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="061f9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="061f9-112">Description</span></span>  
 <span data-ttu-id="061f9-113">Wskazuje, że dostawca SQL przerywa ponownych prób wykonania polecenia SQL jako maksymalną liczbę ponownych prób, które mogły zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="061f9-113">Indicates SQL provider is giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="061f9-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="061f9-114">Message</span></span>  
 <span data-ttu-id="061f9-115">Zwiększanie liczby ponownych polecenia SQL jako maksymalną liczbę ponownych prób mogły zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="061f9-115">Giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="details"></a><span data-ttu-id="061f9-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="061f9-116">Details</span></span>  
  
|<span data-ttu-id="061f9-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="061f9-117">Data Item Name</span></span>|<span data-ttu-id="061f9-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="061f9-118">Data Item Type</span></span>|<span data-ttu-id="061f9-119">Opis</span><span class="sxs-lookup"><span data-stu-id="061f9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="061f9-120">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="061f9-120">AppDomain</span></span>|<span data-ttu-id="061f9-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="061f9-121">xs:string</span></span>|<span data-ttu-id="061f9-122">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="061f9-122">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
