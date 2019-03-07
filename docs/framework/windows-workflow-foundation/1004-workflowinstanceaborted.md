---
title: 1004 — WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: d34f6f1ab6af8e06a0f28fb043faf9fe16a8b211
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485190"
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="1b957-102">1004 — WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="1b957-102">1004 - WorkflowInstanceAborted</span></span>

## <a name="properties"></a><span data-ttu-id="1b957-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1b957-103">Properties</span></span>

|||
|-|-|
|<span data-ttu-id="1b957-104">ID</span><span class="sxs-lookup"><span data-stu-id="1b957-104">ID</span></span>|<span data-ttu-id="1b957-105">1004</span><span class="sxs-lookup"><span data-stu-id="1b957-105">1004</span></span>|
|<span data-ttu-id="1b957-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="1b957-106">Keywords</span></span>|<span data-ttu-id="1b957-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1b957-107">WFRuntime</span></span>|
|<span data-ttu-id="1b957-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="1b957-108">Level</span></span>|<span data-ttu-id="1b957-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="1b957-109">Information</span></span>|
|<span data-ttu-id="1b957-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="1b957-110">Channel</span></span>|<span data-ttu-id="1b957-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="1b957-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|

## <a name="description"></a><span data-ttu-id="1b957-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1b957-112">Description</span></span>

<span data-ttu-id="1b957-113">Wskazuje, że wystąpienie przepływu pracy, została przerwana z powodu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="1b957-113">Indicates a workflow instance has aborted with an exception.</span></span>

## <a name="message"></a><span data-ttu-id="1b957-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="1b957-114">Message</span></span>

<span data-ttu-id="1b957-115">WorkflowInstance Id: "%1" została przerwana z powodu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="1b957-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>

## <a name="details"></a><span data-ttu-id="1b957-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1b957-116">Details</span></span>

|<span data-ttu-id="1b957-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="1b957-117">Data Item Name</span></span>|<span data-ttu-id="1b957-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="1b957-118">Data Item Type</span></span>|<span data-ttu-id="1b957-119">Opis</span><span class="sxs-lookup"><span data-stu-id="1b957-119">Description</span></span>|
|--------------------|--------------------|-----------------|
|<span data-ttu-id="1b957-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="1b957-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="1b957-121">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="1b957-121">The instance id for the workflow</span></span>|
|<span data-ttu-id="1b957-122">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="1b957-122">Exception</span></span>|`xs:string`|<span data-ttu-id="1b957-123">Szczegóły wyjątku, dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="1b957-123">The exception details for the exception</span></span>|
|<span data-ttu-id="1b957-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1b957-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1b957-125">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1b957-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
