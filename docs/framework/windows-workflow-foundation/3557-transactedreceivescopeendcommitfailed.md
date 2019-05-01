---
title: 3557 — TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 444fa2e51322edd793f709fd3f92c5f9fe826522
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774455"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="8f021-102">3557 — TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="8f021-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="8f021-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="8f021-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8f021-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="8f021-104">ID</span></span>|<span data-ttu-id="8f021-105">3557</span><span class="sxs-lookup"><span data-stu-id="8f021-105">3557</span></span>|  
|<span data-ttu-id="8f021-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="8f021-106">Keywords</span></span>|<span data-ttu-id="8f021-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="8f021-107">WFServices</span></span>|  
|<span data-ttu-id="8f021-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="8f021-108">Level</span></span>|<span data-ttu-id="8f021-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="8f021-109">Information</span></span>|  
|<span data-ttu-id="8f021-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="8f021-110">Channel</span></span>|<span data-ttu-id="8f021-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="8f021-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8f021-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8f021-112">Description</span></span>  
 <span data-ttu-id="8f021-113">Wskazuje, że wywołanie EndCommit na CommittableTransaction zgłosił TransactionException —.</span><span class="sxs-lookup"><span data-stu-id="8f021-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8f021-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="8f021-114">Message</span></span>  
 <span data-ttu-id="8f021-115">Wywołanie EndCommit na Commitabletransakction o identyfikatorze = '%1' zgłosił TransactionException — z następującym komunikatem: "%2".</span><span class="sxs-lookup"><span data-stu-id="8f021-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8f021-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8f021-116">Details</span></span>  
  
|<span data-ttu-id="8f021-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="8f021-117">Data Item Name</span></span>|<span data-ttu-id="8f021-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="8f021-118">Data Item Type</span></span>|<span data-ttu-id="8f021-119">Opis</span><span class="sxs-lookup"><span data-stu-id="8f021-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8f021-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="8f021-120">TransactionId</span></span>|<span data-ttu-id="8f021-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="8f021-121">xs:string</span></span>|<span data-ttu-id="8f021-122">Identyfikator Commitabletransakction.</span><span class="sxs-lookup"><span data-stu-id="8f021-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="8f021-123">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="8f021-123">Exception</span></span>|<span data-ttu-id="8f021-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="8f021-124">xs:string</span></span>|<span data-ttu-id="8f021-125">Szczegóły wyjątku, dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="8f021-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="8f021-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8f021-126">AppDomain</span></span>|<span data-ttu-id="8f021-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="8f021-127">xs:string</span></span>|<span data-ttu-id="8f021-128">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8f021-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
