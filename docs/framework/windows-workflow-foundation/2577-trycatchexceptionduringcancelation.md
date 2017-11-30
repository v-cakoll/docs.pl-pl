---
title: 2577 - TryCatchExceptionDuringCancelation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a4bc0d9ab45fe8e2f025c651fce137d6a4255bc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="74f7f-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="74f7f-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="74f7f-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="74f7f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="74f7f-104">ID</span><span class="sxs-lookup"><span data-stu-id="74f7f-104">ID</span></span>|<span data-ttu-id="74f7f-105">2577</span><span class="sxs-lookup"><span data-stu-id="74f7f-105">2577</span></span>|  
|<span data-ttu-id="74f7f-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="74f7f-106">Keywords</span></span>|<span data-ttu-id="74f7f-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="74f7f-107">WFActivities</span></span>|  
|<span data-ttu-id="74f7f-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="74f7f-108">Level</span></span>|<span data-ttu-id="74f7f-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="74f7f-109">Warning</span></span>|  
|<span data-ttu-id="74f7f-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="74f7f-110">Channel</span></span>|<span data-ttu-id="74f7f-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="74f7f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="74f7f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="74f7f-112">Description</span></span>  
 <span data-ttu-id="74f7f-113">Wskazuje, że działanie podrzędne działania TryCatch wywołało wyjątek podczas anulowania.</span><span class="sxs-lookup"><span data-stu-id="74f7f-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="74f7f-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="74f7f-114">Message</span></span>  
 <span data-ttu-id="74f7f-115">Działanie podrzędne działania TryCatch "%1" wywołało wyjątek podczas anulowania.</span><span class="sxs-lookup"><span data-stu-id="74f7f-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="74f7f-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="74f7f-116">Details</span></span>  
  
|<span data-ttu-id="74f7f-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="74f7f-117">Data Item Name</span></span>|<span data-ttu-id="74f7f-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="74f7f-118">Data Item Type</span></span>|<span data-ttu-id="74f7f-119">Opis</span><span class="sxs-lookup"><span data-stu-id="74f7f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="74f7f-120">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="74f7f-120">DisplayName</span></span>|<span data-ttu-id="74f7f-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="74f7f-121">xs:string</span></span>|<span data-ttu-id="74f7f-122">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="74f7f-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="74f7f-123">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="74f7f-123">AppDomain</span></span>|<span data-ttu-id="74f7f-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="74f7f-124">xs:string</span></span>|<span data-ttu-id="74f7f-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="74f7f-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
