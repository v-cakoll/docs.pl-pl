---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 85e9456f6b4c1884b2e28671b304728135b6b1d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="358d0-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="358d0-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="358d0-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="358d0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="358d0-104">ID</span><span class="sxs-lookup"><span data-stu-id="358d0-104">ID</span></span>|<span data-ttu-id="358d0-105">3557</span><span class="sxs-lookup"><span data-stu-id="358d0-105">3557</span></span>|  
|<span data-ttu-id="358d0-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="358d0-106">Keywords</span></span>|<span data-ttu-id="358d0-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="358d0-107">WFServices</span></span>|  
|<span data-ttu-id="358d0-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="358d0-108">Level</span></span>|<span data-ttu-id="358d0-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="358d0-109">Information</span></span>|  
|<span data-ttu-id="358d0-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="358d0-110">Channel</span></span>|<span data-ttu-id="358d0-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="358d0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="358d0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="358d0-112">Description</span></span>  
 <span data-ttu-id="358d0-113">Wskazuje, że wywołanie metody EndCommit w obiekcie CommittableTransaction zwrócił TransactionException.</span><span class="sxs-lookup"><span data-stu-id="358d0-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="358d0-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="358d0-114">Message</span></span>  
 <span data-ttu-id="358d0-115">Wywołanie metody EndCommit w obiekcie CommittableTransaction o identyfikatorze = '%1' zgłosił TransactionException z następującym komunikatem: "%2".</span><span class="sxs-lookup"><span data-stu-id="358d0-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="358d0-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="358d0-116">Details</span></span>  
  
|<span data-ttu-id="358d0-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="358d0-117">Data Item Name</span></span>|<span data-ttu-id="358d0-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="358d0-118">Data Item Type</span></span>|<span data-ttu-id="358d0-119">Opis</span><span class="sxs-lookup"><span data-stu-id="358d0-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="358d0-120">Identyfikator transakcji</span><span class="sxs-lookup"><span data-stu-id="358d0-120">TransactionId</span></span>|<span data-ttu-id="358d0-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="358d0-121">xs:string</span></span>|<span data-ttu-id="358d0-122">Identyfikator obiekcie CommittableTransaction.</span><span class="sxs-lookup"><span data-stu-id="358d0-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="358d0-123">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="358d0-123">Exception</span></span>|<span data-ttu-id="358d0-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="358d0-124">xs:string</span></span>|<span data-ttu-id="358d0-125">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="358d0-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="358d0-126">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="358d0-126">AppDomain</span></span>|<span data-ttu-id="358d0-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="358d0-127">xs:string</span></span>|<span data-ttu-id="358d0-128">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="358d0-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
