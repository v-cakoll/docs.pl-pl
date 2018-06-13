---
title: 1017 - ScheduleCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
ms.openlocfilehash: 186b012cdd554ec7dd0d195b460619cca04eddcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510175"
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="1fd66-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="1fd66-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="1fd66-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1fd66-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1fd66-104">ID</span><span class="sxs-lookup"><span data-stu-id="1fd66-104">ID</span></span>|<span data-ttu-id="1fd66-105">1017</span><span class="sxs-lookup"><span data-stu-id="1fd66-105">1017</span></span>|  
|<span data-ttu-id="1fd66-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="1fd66-106">Keywords</span></span>|<span data-ttu-id="1fd66-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1fd66-107">WFRuntime</span></span>|  
|<span data-ttu-id="1fd66-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="1fd66-108">Level</span></span>|<span data-ttu-id="1fd66-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="1fd66-109">Verbose</span></span>|  
|<span data-ttu-id="1fd66-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="1fd66-110">Channel</span></span>|<span data-ttu-id="1fd66-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="1fd66-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1fd66-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1fd66-112">Description</span></span>  
 <span data-ttu-id="1fd66-113">Wskazuje, że zaplanowano element roboczy CancelActivityWorkItem.</span><span class="sxs-lookup"><span data-stu-id="1fd66-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1fd66-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="1fd66-114">Message</span></span>  
 <span data-ttu-id="1fd66-115">Zaplanowano element roboczy CancelActivityWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="1fd66-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1fd66-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1fd66-116">Details</span></span>  
  
|<span data-ttu-id="1fd66-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="1fd66-117">Data Item Name</span></span>|<span data-ttu-id="1fd66-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="1fd66-118">Data Item Type</span></span>|<span data-ttu-id="1fd66-119">Opis</span><span class="sxs-lookup"><span data-stu-id="1fd66-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1fd66-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="1fd66-120">Activity</span></span>|<span data-ttu-id="1fd66-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="1fd66-121">xs:string</span></span>|<span data-ttu-id="1fd66-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="1fd66-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="1fd66-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="1fd66-123">DisplayName</span></span>|<span data-ttu-id="1fd66-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="1fd66-124">xs:string</span></span>|<span data-ttu-id="1fd66-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="1fd66-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="1fd66-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="1fd66-126">InstanceId</span></span>|<span data-ttu-id="1fd66-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="1fd66-127">xs:string</span></span>|<span data-ttu-id="1fd66-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="1fd66-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="1fd66-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="1fd66-129">AppDomain</span></span>|<span data-ttu-id="1fd66-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="1fd66-130">xs:string</span></span>|<span data-ttu-id="1fd66-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1fd66-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
