---
title: 4203 — RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 984f7ddae8797cba17753a618d0820d21bde5eef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774351"
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="80e4f-102">4203 — RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="80e4f-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="80e4f-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="80e4f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="80e4f-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="80e4f-104">ID</span></span>|<span data-ttu-id="80e4f-105">4203</span><span class="sxs-lookup"><span data-stu-id="80e4f-105">4203</span></span>|  
|<span data-ttu-id="80e4f-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="80e4f-106">Keywords</span></span>|<span data-ttu-id="80e4f-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="80e4f-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="80e4f-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="80e4f-108">Level</span></span>|<span data-ttu-id="80e4f-109">Błąd</span><span class="sxs-lookup"><span data-stu-id="80e4f-109">Error</span></span>|  
|<span data-ttu-id="80e4f-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="80e4f-110">Channel</span></span>|<span data-ttu-id="80e4f-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="80e4f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="80e4f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="80e4f-112">Description</span></span>  
 <span data-ttu-id="80e4f-113">Wskazuje dostawcy bazy danych SQL nie udało się rozszerzyć wygaśnięcia blokady z powodu wygaśnięcia blokady, albo już minęła lub właściciel blokady został usunięty.</span><span class="sxs-lookup"><span data-stu-id="80e4f-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="80e4f-114">SqlWorkflowInstanceStore zostanie przerwane.</span><span class="sxs-lookup"><span data-stu-id="80e4f-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="80e4f-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="80e4f-115">Message</span></span>  
 <span data-ttu-id="80e4f-116">Nie można rozszerzyć wygaśnięcia blokady, wygaśnięcia blokady już przekazany lub właściciel blokady został usunięty.</span><span class="sxs-lookup"><span data-stu-id="80e4f-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="80e4f-117">Aborting SqlWorkflowInstanceStore.</span><span class="sxs-lookup"><span data-stu-id="80e4f-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="80e4f-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="80e4f-118">Details</span></span>  
  
|<span data-ttu-id="80e4f-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="80e4f-119">Data Item Name</span></span>|<span data-ttu-id="80e4f-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="80e4f-120">Data Item Type</span></span>|<span data-ttu-id="80e4f-121">Opis</span><span class="sxs-lookup"><span data-stu-id="80e4f-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="80e4f-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="80e4f-122">AppDomain</span></span>|<span data-ttu-id="80e4f-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="80e4f-123">xs:string</span></span>|<span data-ttu-id="80e4f-124">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="80e4f-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
