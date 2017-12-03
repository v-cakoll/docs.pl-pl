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
ms.openlocfilehash: 8ea57cc60f9626763308267a98624c825f8312b0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="1b459-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="1b459-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="1b459-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1b459-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1b459-104">ID</span><span class="sxs-lookup"><span data-stu-id="1b459-104">ID</span></span>|<span data-ttu-id="1b459-105">3557</span><span class="sxs-lookup"><span data-stu-id="1b459-105">3557</span></span>|  
|<span data-ttu-id="1b459-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="1b459-106">Keywords</span></span>|<span data-ttu-id="1b459-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="1b459-107">WFServices</span></span>|  
|<span data-ttu-id="1b459-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="1b459-108">Level</span></span>|<span data-ttu-id="1b459-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="1b459-109">Information</span></span>|  
|<span data-ttu-id="1b459-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="1b459-110">Channel</span></span>|<span data-ttu-id="1b459-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="1b459-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1b459-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1b459-112">Description</span></span>  
 <span data-ttu-id="1b459-113">Wskazuje, że wywołanie metody EndCommit w obiekcie CommittableTransaction zwrócił TransactionException.</span><span class="sxs-lookup"><span data-stu-id="1b459-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1b459-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="1b459-114">Message</span></span>  
 <span data-ttu-id="1b459-115">Wywołanie metody EndCommit w obiekcie CommittableTransaction o identyfikatorze = '%1' zgłosił TransactionException z następującym komunikatem: "%2".</span><span class="sxs-lookup"><span data-stu-id="1b459-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1b459-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1b459-116">Details</span></span>  
  
|<span data-ttu-id="1b459-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="1b459-117">Data Item Name</span></span>|<span data-ttu-id="1b459-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="1b459-118">Data Item Type</span></span>|<span data-ttu-id="1b459-119">Opis</span><span class="sxs-lookup"><span data-stu-id="1b459-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1b459-120">Identyfikator transakcji</span><span class="sxs-lookup"><span data-stu-id="1b459-120">TransactionId</span></span>|<span data-ttu-id="1b459-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="1b459-121">xs:string</span></span>|<span data-ttu-id="1b459-122">Identyfikator obiekcie CommittableTransaction.</span><span class="sxs-lookup"><span data-stu-id="1b459-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="1b459-123">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="1b459-123">Exception</span></span>|<span data-ttu-id="1b459-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="1b459-124">xs:string</span></span>|<span data-ttu-id="1b459-125">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="1b459-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="1b459-126">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="1b459-126">AppDomain</span></span>|<span data-ttu-id="1b459-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="1b459-127">xs:string</span></span>|<span data-ttu-id="1b459-128">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1b459-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
