---
title: 1004 — WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: d34f6f1ab6af8e06a0f28fb043faf9fe16a8b211
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008619"
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="cc775-102">1004 — WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="cc775-102">1004 - WorkflowInstanceAborted</span></span>

## <a name="properties"></a><span data-ttu-id="cc775-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="cc775-103">Properties</span></span>

|||
|-|-|
|<span data-ttu-id="cc775-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="cc775-104">ID</span></span>|<span data-ttu-id="cc775-105">1004</span><span class="sxs-lookup"><span data-stu-id="cc775-105">1004</span></span>|
|<span data-ttu-id="cc775-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="cc775-106">Keywords</span></span>|<span data-ttu-id="cc775-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="cc775-107">WFRuntime</span></span>|
|<span data-ttu-id="cc775-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="cc775-108">Level</span></span>|<span data-ttu-id="cc775-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="cc775-109">Information</span></span>|
|<span data-ttu-id="cc775-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="cc775-110">Channel</span></span>|<span data-ttu-id="cc775-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="cc775-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|

## <a name="description"></a><span data-ttu-id="cc775-112">Opis</span><span class="sxs-lookup"><span data-stu-id="cc775-112">Description</span></span>

<span data-ttu-id="cc775-113">Wskazuje, że wystąpienie przepływu pracy, została przerwana z powodu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="cc775-113">Indicates a workflow instance has aborted with an exception.</span></span>

## <a name="message"></a><span data-ttu-id="cc775-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="cc775-114">Message</span></span>

<span data-ttu-id="cc775-115">WorkflowInstance Id: "%1" została przerwana z powodu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="cc775-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>

## <a name="details"></a><span data-ttu-id="cc775-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="cc775-116">Details</span></span>

|<span data-ttu-id="cc775-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="cc775-117">Data Item Name</span></span>|<span data-ttu-id="cc775-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="cc775-118">Data Item Type</span></span>|<span data-ttu-id="cc775-119">Opis</span><span class="sxs-lookup"><span data-stu-id="cc775-119">Description</span></span>|
|--------------------|--------------------|-----------------|
|<span data-ttu-id="cc775-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="cc775-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="cc775-121">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="cc775-121">The instance id for the workflow</span></span>|
|<span data-ttu-id="cc775-122">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="cc775-122">Exception</span></span>|`xs:string`|<span data-ttu-id="cc775-123">Szczegóły wyjątku, dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="cc775-123">The exception details for the exception</span></span>|
|<span data-ttu-id="cc775-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cc775-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="cc775-125">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="cc775-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
