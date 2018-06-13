---
title: 4203 - RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 984f7ddae8797cba17753a618d0820d21bde5eef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513932"
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="30c49-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="30c49-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="30c49-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="30c49-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="30c49-104">ID</span><span class="sxs-lookup"><span data-stu-id="30c49-104">ID</span></span>|<span data-ttu-id="30c49-105">4203</span><span class="sxs-lookup"><span data-stu-id="30c49-105">4203</span></span>|  
|<span data-ttu-id="30c49-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="30c49-106">Keywords</span></span>|<span data-ttu-id="30c49-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="30c49-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="30c49-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="30c49-108">Level</span></span>|<span data-ttu-id="30c49-109">Błąd</span><span class="sxs-lookup"><span data-stu-id="30c49-109">Error</span></span>|  
|<span data-ttu-id="30c49-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="30c49-110">Channel</span></span>|<span data-ttu-id="30c49-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="30c49-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="30c49-112">Opis</span><span class="sxs-lookup"><span data-stu-id="30c49-112">Description</span></span>  
 <span data-ttu-id="30c49-113">Wskazuje dostawcy SQL można przedłużyć okresu ważności blokady z powodu albo okresu ważności blokady już minęła lub właściciel blokady został usunięty.</span><span class="sxs-lookup"><span data-stu-id="30c49-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="30c49-114">Obiekt SqlWorkflowInstanceStore zostanie przerwane.</span><span class="sxs-lookup"><span data-stu-id="30c49-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="30c49-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="30c49-115">Message</span></span>  
 <span data-ttu-id="30c49-116">Nie można przedłużyć okresu ważności blokady, blokada już wygasła lub właściciel blokady został usunięty.</span><span class="sxs-lookup"><span data-stu-id="30c49-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="30c49-117">Trwa przerywanie SqlWorkflowInstanceStore.</span><span class="sxs-lookup"><span data-stu-id="30c49-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="30c49-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="30c49-118">Details</span></span>  
  
|<span data-ttu-id="30c49-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="30c49-119">Data Item Name</span></span>|<span data-ttu-id="30c49-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="30c49-120">Data Item Type</span></span>|<span data-ttu-id="30c49-121">Opis</span><span class="sxs-lookup"><span data-stu-id="30c49-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="30c49-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="30c49-122">AppDomain</span></span>|<span data-ttu-id="30c49-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="30c49-123">xs:string</span></span>|<span data-ttu-id="30c49-124">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="30c49-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
