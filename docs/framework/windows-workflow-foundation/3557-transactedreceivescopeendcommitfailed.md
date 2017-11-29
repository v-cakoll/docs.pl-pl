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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c1f9f1066f1948411d584a2dee1af2129aa3a103
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="d6eef-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="d6eef-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="d6eef-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d6eef-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d6eef-104">ID</span><span class="sxs-lookup"><span data-stu-id="d6eef-104">ID</span></span>|<span data-ttu-id="d6eef-105">3557</span><span class="sxs-lookup"><span data-stu-id="d6eef-105">3557</span></span>|  
|<span data-ttu-id="d6eef-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="d6eef-106">Keywords</span></span>|<span data-ttu-id="d6eef-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="d6eef-107">WFServices</span></span>|  
|<span data-ttu-id="d6eef-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="d6eef-108">Level</span></span>|<span data-ttu-id="d6eef-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="d6eef-109">Information</span></span>|  
|<span data-ttu-id="d6eef-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="d6eef-110">Channel</span></span>|<span data-ttu-id="d6eef-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="d6eef-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d6eef-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d6eef-112">Description</span></span>  
 <span data-ttu-id="d6eef-113">Wskazuje, że wywołanie metody EndCommit w obiekcie CommittableTransaction zwrócił TransactionException.</span><span class="sxs-lookup"><span data-stu-id="d6eef-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d6eef-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="d6eef-114">Message</span></span>  
 <span data-ttu-id="d6eef-115">Wywołanie metody EndCommit w obiekcie CommittableTransaction o identyfikatorze = '%1' zgłosił TransactionException z następującym komunikatem: "%2".</span><span class="sxs-lookup"><span data-stu-id="d6eef-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d6eef-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d6eef-116">Details</span></span>  
  
|<span data-ttu-id="d6eef-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="d6eef-117">Data Item Name</span></span>|<span data-ttu-id="d6eef-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="d6eef-118">Data Item Type</span></span>|<span data-ttu-id="d6eef-119">Opis</span><span class="sxs-lookup"><span data-stu-id="d6eef-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d6eef-120">Identyfikator transakcji</span><span class="sxs-lookup"><span data-stu-id="d6eef-120">TransactionId</span></span>|<span data-ttu-id="d6eef-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="d6eef-121">xs:string</span></span>|<span data-ttu-id="d6eef-122">Identyfikator obiekcie CommittableTransaction.</span><span class="sxs-lookup"><span data-stu-id="d6eef-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="d6eef-123">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="d6eef-123">Exception</span></span>|<span data-ttu-id="d6eef-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="d6eef-124">xs:string</span></span>|<span data-ttu-id="d6eef-125">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="d6eef-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="d6eef-126">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="d6eef-126">AppDomain</span></span>|<span data-ttu-id="d6eef-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="d6eef-127">xs:string</span></span>|<span data-ttu-id="d6eef-128">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d6eef-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
