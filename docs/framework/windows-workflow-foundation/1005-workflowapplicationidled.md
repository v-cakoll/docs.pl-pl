---
title: 1005 - WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: 6bbd12e8025b6a127dbfec8e5d3690825c188c4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509297"
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="c7cb9-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="c7cb9-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="c7cb9-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c7cb9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c7cb9-104">ID</span><span class="sxs-lookup"><span data-stu-id="c7cb9-104">ID</span></span>|<span data-ttu-id="c7cb9-105">1005</span><span class="sxs-lookup"><span data-stu-id="c7cb9-105">1005</span></span>|  
|<span data-ttu-id="c7cb9-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="c7cb9-106">Keywords</span></span>|<span data-ttu-id="c7cb9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c7cb9-107">WFRuntime</span></span>|  
|<span data-ttu-id="c7cb9-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="c7cb9-108">Level</span></span>|<span data-ttu-id="c7cb9-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="c7cb9-109">Information</span></span>|  
|<span data-ttu-id="c7cb9-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="c7cb9-110">Channel</span></span>|<span data-ttu-id="c7cb9-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="c7cb9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c7cb9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c7cb9-112">Description</span></span>  
 <span data-ttu-id="c7cb9-113">Wskazuje, że ma idled aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c7cb9-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c7cb9-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="c7cb9-114">Message</span></span>  
 <span data-ttu-id="c7cb9-115">Obiekt WorkflowApplication o identyfikatorze: "%1" zakończył bezczynności.</span><span class="sxs-lookup"><span data-stu-id="c7cb9-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c7cb9-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c7cb9-116">Details</span></span>  
  
|<span data-ttu-id="c7cb9-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="c7cb9-117">Data Item Name</span></span>|<span data-ttu-id="c7cb9-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="c7cb9-118">Data Item Type</span></span>|<span data-ttu-id="c7cb9-119">Opis</span><span class="sxs-lookup"><span data-stu-id="c7cb9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c7cb9-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="c7cb9-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="c7cb9-121">Identyfikator aplikacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c7cb9-121">The workflow application id</span></span>|  
|<span data-ttu-id="c7cb9-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="c7cb9-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c7cb9-123">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c7cb9-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
