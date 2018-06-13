---
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 752cd73066c3c15ecbb36c40c417ee84b3fcf184
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512008"
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="1dd70-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="1dd70-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="1dd70-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1dd70-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1dd70-104">ID</span><span class="sxs-lookup"><span data-stu-id="1dd70-104">ID</span></span>|<span data-ttu-id="1dd70-105">3502</span><span class="sxs-lookup"><span data-stu-id="1dd70-105">3502</span></span>|  
|<span data-ttu-id="1dd70-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="1dd70-106">Keywords</span></span>|<span data-ttu-id="1dd70-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="1dd70-107">WFServices</span></span>|  
|<span data-ttu-id="1dd70-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="1dd70-108">Level</span></span>|<span data-ttu-id="1dd70-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="1dd70-109">Information</span></span>|  
|<span data-ttu-id="1dd70-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="1dd70-110">Channel</span></span>|<span data-ttu-id="1dd70-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="1dd70-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1dd70-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1dd70-112">Description</span></span>  
 <span data-ttu-id="1dd70-113">Wskazuje, że OperationDescription został wywnioskowany na podstawie obiektu WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="1dd70-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1dd70-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="1dd70-114">Message</span></span>  
 <span data-ttu-id="1dd70-115">OperationDescription o nazwie "% 1" w kontrakcie "%2" został wywnioskowany na podstawie obiektu WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="1dd70-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="1dd70-116">Ustawienie właściwości IsOneWay = %3.</span><span class="sxs-lookup"><span data-stu-id="1dd70-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1dd70-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1dd70-117">Details</span></span>  
  
|<span data-ttu-id="1dd70-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="1dd70-118">Data Item Name</span></span>|<span data-ttu-id="1dd70-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="1dd70-119">Data Item Type</span></span>|<span data-ttu-id="1dd70-120">Opis</span><span class="sxs-lookup"><span data-stu-id="1dd70-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1dd70-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="1dd70-121">OperationName</span></span>|<span data-ttu-id="1dd70-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="1dd70-122">xs:string</span></span>|<span data-ttu-id="1dd70-123">Nazwa operacji.</span><span class="sxs-lookup"><span data-stu-id="1dd70-123">The name of the operation.</span></span>|  
|<span data-ttu-id="1dd70-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="1dd70-124">ContractName</span></span>|<span data-ttu-id="1dd70-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="1dd70-125">xs:string</span></span>|<span data-ttu-id="1dd70-126">Nazwa kontraktu.</span><span class="sxs-lookup"><span data-stu-id="1dd70-126">The name of the contract.</span></span>|  
|<span data-ttu-id="1dd70-127">Ustawienie właściwości IsOneWay</span><span class="sxs-lookup"><span data-stu-id="1dd70-127">IsOneWay</span></span>|<span data-ttu-id="1dd70-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="1dd70-128">xs:string</span></span>|<span data-ttu-id="1dd70-129">Wartość PRAWDA lub Fałsz wskazująca, czy kontrakt jest jednokierunkowa.</span><span class="sxs-lookup"><span data-stu-id="1dd70-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="1dd70-130">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="1dd70-130">AppDomain</span></span>|<span data-ttu-id="1dd70-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="1dd70-131">xs:string</span></span>|<span data-ttu-id="1dd70-132">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1dd70-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
