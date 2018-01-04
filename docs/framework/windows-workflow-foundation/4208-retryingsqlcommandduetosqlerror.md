---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51374a25ee11b3344e950670cc7882db42d39779
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="6edd4-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="6edd4-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="6edd4-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="6edd4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6edd4-104">ID</span><span class="sxs-lookup"><span data-stu-id="6edd4-104">ID</span></span>|<span data-ttu-id="6edd4-105">4208</span><span class="sxs-lookup"><span data-stu-id="6edd4-105">4208</span></span>|  
|<span data-ttu-id="6edd4-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="6edd4-106">Keywords</span></span>|<span data-ttu-id="6edd4-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="6edd4-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="6edd4-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="6edd4-108">Level</span></span>|<span data-ttu-id="6edd4-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="6edd4-109">Information</span></span>|  
|<span data-ttu-id="6edd4-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="6edd4-110">Channel</span></span>|<span data-ttu-id="6edd4-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="6edd4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6edd4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6edd4-112">Description</span></span>  
 <span data-ttu-id="6edd4-113">Wskazuje, że dostawca SQL jest ponownych prób wykonania polecenia SQL z powodu błędu SQL.</span><span class="sxs-lookup"><span data-stu-id="6edd4-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6edd4-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="6edd4-114">Message</span></span>  
 <span data-ttu-id="6edd4-115">Ponownych prób wykonania polecenia SQL z powodu błędu SQL numer %1.</span><span class="sxs-lookup"><span data-stu-id="6edd4-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6edd4-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="6edd4-116">Details</span></span>  
  
|<span data-ttu-id="6edd4-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="6edd4-117">Data Item Name</span></span>|<span data-ttu-id="6edd4-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="6edd4-118">Data Item Type</span></span>|<span data-ttu-id="6edd4-119">Opis</span><span class="sxs-lookup"><span data-stu-id="6edd4-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6edd4-120">Numer_błędu</span><span class="sxs-lookup"><span data-stu-id="6edd4-120">ErrorNumber</span></span>|<span data-ttu-id="6edd4-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="6edd4-121">xs:string</span></span>|<span data-ttu-id="6edd4-122">Numer błędu SQL.</span><span class="sxs-lookup"><span data-stu-id="6edd4-122">The SQL error number.</span></span>|  
|<span data-ttu-id="6edd4-123">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="6edd4-123">AppDomain</span></span>|<span data-ttu-id="6edd4-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="6edd4-124">xs:string</span></span>|<span data-ttu-id="6edd4-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6edd4-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
