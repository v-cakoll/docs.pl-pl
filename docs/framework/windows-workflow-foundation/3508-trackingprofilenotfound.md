---
title: 3508 — TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 94c7ce231df241778f7c6ec5fe5998eae364750d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755574"
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="52661-102">3508 — TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="52661-102">3508 - TrackingProfileNotFound</span></span>
## <a name="properties"></a><span data-ttu-id="52661-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="52661-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="52661-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="52661-104">ID</span></span>|<span data-ttu-id="52661-105">3508</span><span class="sxs-lookup"><span data-stu-id="52661-105">3508</span></span>|  
|<span data-ttu-id="52661-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="52661-106">Keywords</span></span>|<span data-ttu-id="52661-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="52661-107">WFServices</span></span>|  
|<span data-ttu-id="52661-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="52661-108">Level</span></span>|<span data-ttu-id="52661-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="52661-109">Verbose</span></span>|  
|<span data-ttu-id="52661-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="52661-110">Channel</span></span>|<span data-ttu-id="52661-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="52661-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="52661-112">Opis</span><span class="sxs-lookup"><span data-stu-id="52661-112">Description</span></span>  
 <span data-ttu-id="52661-113">Oznacza TrackingProfile nie znajduje się w pliku konfiguracji lub ActivityDefinitionId nie pasuje do profilu.</span><span class="sxs-lookup"><span data-stu-id="52661-113">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="52661-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="52661-114">Message</span></span>  
 <span data-ttu-id="52661-115">TrackingProfile "%1" dla ActivityDefinitionId "%2" nie można odnaleźć.</span><span class="sxs-lookup"><span data-stu-id="52661-115">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="52661-116">TrackingProfile nie znajduje się w pliku konfiguracji, albo ActivityDefinitionId jest niezgodny.</span><span class="sxs-lookup"><span data-stu-id="52661-116">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="52661-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="52661-117">Details</span></span>  
  
|<span data-ttu-id="52661-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="52661-118">Data Item Name</span></span>|<span data-ttu-id="52661-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="52661-119">Data Item Type</span></span>|<span data-ttu-id="52661-120">Opis</span><span class="sxs-lookup"><span data-stu-id="52661-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="52661-121">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="52661-121">TrackingProfile</span></span>|<span data-ttu-id="52661-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="52661-122">xs:string</span></span>|<span data-ttu-id="52661-123">Nazwa profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="52661-123">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="52661-124">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="52661-124">ActivityDefinitionId</span></span>|<span data-ttu-id="52661-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="52661-125">xs:string</span></span>|<span data-ttu-id="52661-126">Identyfikator definicji działania.</span><span class="sxs-lookup"><span data-stu-id="52661-126">The activity definition id.</span></span>|  
|<span data-ttu-id="52661-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="52661-127">AppDomain</span></span>|<span data-ttu-id="52661-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="52661-128">xs:string</span></span>|<span data-ttu-id="52661-129">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="52661-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
