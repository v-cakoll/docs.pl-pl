---
title: 1002 - WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: 01c9aba6e863e07a1a999a28fccefbab95a34d5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510082"
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="d3252-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="d3252-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="d3252-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d3252-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d3252-104">ID</span><span class="sxs-lookup"><span data-stu-id="d3252-104">ID</span></span>|<span data-ttu-id="d3252-105">1002</span><span class="sxs-lookup"><span data-stu-id="d3252-105">1002</span></span>|  
|<span data-ttu-id="d3252-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="d3252-106">Keywords</span></span>|<span data-ttu-id="d3252-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d3252-107">WFRuntime</span></span>|  
|<span data-ttu-id="d3252-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="d3252-108">Level</span></span>|<span data-ttu-id="d3252-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="d3252-109">Information</span></span>|  
|<span data-ttu-id="d3252-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="d3252-110">Channel</span></span>|<span data-ttu-id="d3252-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="d3252-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d3252-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d3252-112">Description</span></span>  
 <span data-ttu-id="d3252-113">Wskazuje, że aplikacja przepływu pracy zostało przerwane w stanie Faulted z wyjątkiem.</span><span class="sxs-lookup"><span data-stu-id="d3252-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d3252-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="d3252-114">Message</span></span>  
 <span data-ttu-id="d3252-115">Obiekt WorkflowApplication o identyfikatorze: '%1' została zakończona.</span><span class="sxs-lookup"><span data-stu-id="d3252-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="d3252-116">Została ukończona w stan końcowy: Faulted z wyjątkiem.</span><span class="sxs-lookup"><span data-stu-id="d3252-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d3252-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d3252-117">Details</span></span>  
  
|<span data-ttu-id="d3252-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="d3252-118">Data Item Name</span></span>|<span data-ttu-id="d3252-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="d3252-119">Data Item Type</span></span>|<span data-ttu-id="d3252-120">Opis</span><span class="sxs-lookup"><span data-stu-id="d3252-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d3252-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="d3252-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="d3252-122">Identyfikator aplikacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="d3252-122">The workflow application id</span></span>|  
|<span data-ttu-id="d3252-123">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="d3252-123">Exception</span></span>|`xs:string`|<span data-ttu-id="d3252-124">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="d3252-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="d3252-125">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="d3252-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d3252-126">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d3252-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
