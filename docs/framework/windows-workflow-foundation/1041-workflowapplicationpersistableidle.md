---
title: 1041 — WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 07be0ae603443a1ef06cb539bba7b227d7b3e325
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924192"
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="72755-102">1041 — WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="72755-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="72755-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="72755-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="72755-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="72755-104">ID</span></span>|<span data-ttu-id="72755-105">1041</span><span class="sxs-lookup"><span data-stu-id="72755-105">1041</span></span>|  
|<span data-ttu-id="72755-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="72755-106">Keywords</span></span>|<span data-ttu-id="72755-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="72755-107">WFRuntime</span></span>|  
|<span data-ttu-id="72755-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="72755-108">Level</span></span>|<span data-ttu-id="72755-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="72755-109">Information</span></span>|  
|<span data-ttu-id="72755-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="72755-110">Channel</span></span>|<span data-ttu-id="72755-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="72755-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="72755-112">Opis</span><span class="sxs-lookup"><span data-stu-id="72755-112">Description</span></span>  
 <span data-ttu-id="72755-113">Wskazuje, że aplikacja przepływu pracy jest bezczynny i stałe.</span><span class="sxs-lookup"><span data-stu-id="72755-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="72755-114">Aplikacja przepływu pracy będą bezczynny, czy utrwalone.</span><span class="sxs-lookup"><span data-stu-id="72755-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="72755-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="72755-115">Message</span></span>  
 <span data-ttu-id="72755-116">Identyfikator WorkflowApplication: "%1" jest bezczynny i stałe.</span><span class="sxs-lookup"><span data-stu-id="72755-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="72755-117">Zostaną podjęte następujące działania: %2.</span><span class="sxs-lookup"><span data-stu-id="72755-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="72755-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="72755-118">Details</span></span>  
  
|<span data-ttu-id="72755-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="72755-119">Data Item Name</span></span>|<span data-ttu-id="72755-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="72755-120">Data Item Type</span></span>|<span data-ttu-id="72755-121">Opis</span><span class="sxs-lookup"><span data-stu-id="72755-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="72755-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="72755-122">WorkflowApplicationId</span></span>|<span data-ttu-id="72755-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="72755-123">xs:string</span></span>|<span data-ttu-id="72755-124">Identyfikator aplikacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="72755-124">The workflow application id</span></span>|  
|<span data-ttu-id="72755-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="72755-125">ActionTaken</span></span>|<span data-ttu-id="72755-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="72755-126">xs:string</span></span>|<span data-ttu-id="72755-127">Akcja, która zostaną wykonane w aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="72755-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="72755-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="72755-128">AppDomain</span></span>|<span data-ttu-id="72755-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="72755-129">xs:string</span></span>|<span data-ttu-id="72755-130">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="72755-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
