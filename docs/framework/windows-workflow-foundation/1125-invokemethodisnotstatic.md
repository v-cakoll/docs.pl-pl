---
title: 1125 - InvokeMethodIsNotStatic
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8b5e255e9a753c6476a070609b0cbda189d37a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="d7f02-102">1125 - InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="d7f02-102">1125 - InvokeMethodIsNotStatic</span></span>
## <a name="properties"></a><span data-ttu-id="d7f02-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d7f02-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d7f02-104">ID</span><span class="sxs-lookup"><span data-stu-id="d7f02-104">ID</span></span>|<span data-ttu-id="d7f02-105">1125</span><span class="sxs-lookup"><span data-stu-id="d7f02-105">1125</span></span>|  
|<span data-ttu-id="d7f02-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="d7f02-106">Keywords</span></span>|<span data-ttu-id="d7f02-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d7f02-107">WFRuntime</span></span>|  
|<span data-ttu-id="d7f02-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="d7f02-108">Level</span></span>|<span data-ttu-id="d7f02-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="d7f02-109">Information</span></span>|  
|<span data-ttu-id="d7f02-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="d7f02-110">Channel</span></span>|<span data-ttu-id="d7f02-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="d7f02-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d7f02-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d7f02-112">Description</span></span>  
 <span data-ttu-id="d7f02-113">Podczas wykonywania kroku CacheMetadata działanie InvokeMethod wskazuje, że wywoływanej metody nie jest statyczne.</span><span class="sxs-lookup"><span data-stu-id="d7f02-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d7f02-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="d7f02-114">Message</span></span>  
 <span data-ttu-id="d7f02-115">InvokeMethod "%1" — metoda nie jest statyczna.</span><span class="sxs-lookup"><span data-stu-id="d7f02-115">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d7f02-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d7f02-116">Details</span></span>  
  
|<span data-ttu-id="d7f02-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="d7f02-117">Data Item Name</span></span>|<span data-ttu-id="d7f02-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="d7f02-118">Data Item Type</span></span>|<span data-ttu-id="d7f02-119">Opis</span><span class="sxs-lookup"><span data-stu-id="d7f02-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d7f02-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="d7f02-120">InvokeMethod</span></span>|<span data-ttu-id="d7f02-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="d7f02-121">xs:string</span></span>|<span data-ttu-id="d7f02-122">Nazwa wyświetlana InvokeMethod działania.</span><span class="sxs-lookup"><span data-stu-id="d7f02-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="d7f02-123">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="d7f02-123">AppDomain</span></span>|<span data-ttu-id="d7f02-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="d7f02-124">xs:string</span></span>|<span data-ttu-id="d7f02-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d7f02-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
