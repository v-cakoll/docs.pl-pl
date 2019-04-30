---
title: 3502 — InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 752cd73066c3c15ecbb36c40c417ee84b3fcf184
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756094"
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="b29b0-102">3502 — InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="b29b0-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="b29b0-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b29b0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b29b0-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="b29b0-104">ID</span></span>|<span data-ttu-id="b29b0-105">3502</span><span class="sxs-lookup"><span data-stu-id="b29b0-105">3502</span></span>|  
|<span data-ttu-id="b29b0-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="b29b0-106">Keywords</span></span>|<span data-ttu-id="b29b0-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="b29b0-107">WFServices</span></span>|  
|<span data-ttu-id="b29b0-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="b29b0-108">Level</span></span>|<span data-ttu-id="b29b0-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="b29b0-109">Information</span></span>|  
|<span data-ttu-id="b29b0-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="b29b0-110">Channel</span></span>|<span data-ttu-id="b29b0-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="b29b0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b29b0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b29b0-112">Description</span></span>  
 <span data-ttu-id="b29b0-113">Wskazuje, że obiekt OperationDescription została wykryta z WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="b29b0-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b29b0-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="b29b0-114">Message</span></span>  
 <span data-ttu-id="b29b0-115">Obiekt OperationDescription o nazwie = "%1" w kontrakcie "%2" została wykryta z WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="b29b0-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="b29b0-116">IsOneWay=%3.</span><span class="sxs-lookup"><span data-stu-id="b29b0-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b29b0-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b29b0-117">Details</span></span>  
  
|<span data-ttu-id="b29b0-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="b29b0-118">Data Item Name</span></span>|<span data-ttu-id="b29b0-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="b29b0-119">Data Item Type</span></span>|<span data-ttu-id="b29b0-120">Opis</span><span class="sxs-lookup"><span data-stu-id="b29b0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b29b0-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="b29b0-121">OperationName</span></span>|<span data-ttu-id="b29b0-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="b29b0-122">xs:string</span></span>|<span data-ttu-id="b29b0-123">Nazwa operacji.</span><span class="sxs-lookup"><span data-stu-id="b29b0-123">The name of the operation.</span></span>|  
|<span data-ttu-id="b29b0-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="b29b0-124">ContractName</span></span>|<span data-ttu-id="b29b0-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="b29b0-125">xs:string</span></span>|<span data-ttu-id="b29b0-126">Nazwa kontraktu.</span><span class="sxs-lookup"><span data-stu-id="b29b0-126">The name of the contract.</span></span>|  
|<span data-ttu-id="b29b0-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="b29b0-127">IsOneWay</span></span>|<span data-ttu-id="b29b0-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="b29b0-128">xs:string</span></span>|<span data-ttu-id="b29b0-129">Wartość PRAWDA lub Fałsz wskazująca, czy kontrakt jest jednokierunkowa.</span><span class="sxs-lookup"><span data-stu-id="b29b0-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="b29b0-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b29b0-130">AppDomain</span></span>|<span data-ttu-id="b29b0-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="b29b0-131">xs:string</span></span>|<span data-ttu-id="b29b0-132">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b29b0-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
