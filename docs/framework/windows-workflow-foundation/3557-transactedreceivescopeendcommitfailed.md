---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 444fa2e51322edd793f709fd3f92c5f9fe826522
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512164"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="32c14-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="32c14-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="32c14-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="32c14-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="32c14-104">ID</span><span class="sxs-lookup"><span data-stu-id="32c14-104">ID</span></span>|<span data-ttu-id="32c14-105">3557</span><span class="sxs-lookup"><span data-stu-id="32c14-105">3557</span></span>|  
|<span data-ttu-id="32c14-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="32c14-106">Keywords</span></span>|<span data-ttu-id="32c14-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="32c14-107">WFServices</span></span>|  
|<span data-ttu-id="32c14-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="32c14-108">Level</span></span>|<span data-ttu-id="32c14-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="32c14-109">Information</span></span>|  
|<span data-ttu-id="32c14-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="32c14-110">Channel</span></span>|<span data-ttu-id="32c14-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="32c14-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="32c14-112">Opis</span><span class="sxs-lookup"><span data-stu-id="32c14-112">Description</span></span>  
 <span data-ttu-id="32c14-113">Wskazuje, że wywołanie metody EndCommit w obiekcie CommittableTransaction zwrócił TransactionException.</span><span class="sxs-lookup"><span data-stu-id="32c14-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="32c14-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="32c14-114">Message</span></span>  
 <span data-ttu-id="32c14-115">Wywołanie metody EndCommit w obiekcie CommittableTransaction o identyfikatorze = '%1' zgłosił TransactionException z następującym komunikatem: "%2".</span><span class="sxs-lookup"><span data-stu-id="32c14-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="32c14-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="32c14-116">Details</span></span>  
  
|<span data-ttu-id="32c14-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="32c14-117">Data Item Name</span></span>|<span data-ttu-id="32c14-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="32c14-118">Data Item Type</span></span>|<span data-ttu-id="32c14-119">Opis</span><span class="sxs-lookup"><span data-stu-id="32c14-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="32c14-120">Identyfikator transakcji</span><span class="sxs-lookup"><span data-stu-id="32c14-120">TransactionId</span></span>|<span data-ttu-id="32c14-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="32c14-121">xs:string</span></span>|<span data-ttu-id="32c14-122">Identyfikator obiekcie CommittableTransaction.</span><span class="sxs-lookup"><span data-stu-id="32c14-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="32c14-123">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="32c14-123">Exception</span></span>|<span data-ttu-id="32c14-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="32c14-124">xs:string</span></span>|<span data-ttu-id="32c14-125">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="32c14-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="32c14-126">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="32c14-126">AppDomain</span></span>|<span data-ttu-id="32c14-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="32c14-127">xs:string</span></span>|<span data-ttu-id="32c14-128">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="32c14-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
