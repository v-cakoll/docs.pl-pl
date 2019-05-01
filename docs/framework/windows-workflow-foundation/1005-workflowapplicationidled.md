---
title: 1005 — WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: 6bbd12e8025b6a127dbfec8e5d3690825c188c4d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008606"
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="e903c-102">1005 — WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="e903c-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="e903c-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e903c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e903c-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="e903c-104">ID</span></span>|<span data-ttu-id="e903c-105">1005</span><span class="sxs-lookup"><span data-stu-id="e903c-105">1005</span></span>|  
|<span data-ttu-id="e903c-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="e903c-106">Keywords</span></span>|<span data-ttu-id="e903c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e903c-107">WFRuntime</span></span>|  
|<span data-ttu-id="e903c-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="e903c-108">Level</span></span>|<span data-ttu-id="e903c-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="e903c-109">Information</span></span>|  
|<span data-ttu-id="e903c-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="e903c-110">Channel</span></span>|<span data-ttu-id="e903c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e903c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e903c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e903c-112">Description</span></span>  
 <span data-ttu-id="e903c-113">Wskazuje, że aplikacja przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="e903c-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e903c-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="e903c-114">Message</span></span>  
 <span data-ttu-id="e903c-115">Identyfikator WorkflowApplication: "%1" Wystąpił bezczynności.</span><span class="sxs-lookup"><span data-stu-id="e903c-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e903c-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e903c-116">Details</span></span>  
  
|<span data-ttu-id="e903c-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="e903c-117">Data Item Name</span></span>|<span data-ttu-id="e903c-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="e903c-118">Data Item Type</span></span>|<span data-ttu-id="e903c-119">Opis</span><span class="sxs-lookup"><span data-stu-id="e903c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e903c-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="e903c-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="e903c-121">Identyfikator aplikacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e903c-121">The workflow application id</span></span>|  
|<span data-ttu-id="e903c-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e903c-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e903c-123">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e903c-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
