---
title: 4212 — LockRetryTimeout
ms.date: 03/30/2017
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
ms.openlocfilehash: 9b7a463851d380eba1ef7b28fbc6decd0cfc979c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774221"
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="855d0-102">4212 — LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="855d0-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="855d0-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="855d0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="855d0-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="855d0-104">ID</span></span>|<span data-ttu-id="855d0-105">4212</span><span class="sxs-lookup"><span data-stu-id="855d0-105">4212</span></span>|  
|<span data-ttu-id="855d0-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="855d0-106">Keywords</span></span>|<span data-ttu-id="855d0-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="855d0-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="855d0-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="855d0-108">Level</span></span>|<span data-ttu-id="855d0-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="855d0-109">Warning</span></span>|  
|<span data-ttu-id="855d0-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="855d0-110">Channel</span></span>|<span data-ttu-id="855d0-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="855d0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="855d0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="855d0-112">Description</span></span>  
 <span data-ttu-id="855d0-113">Dostawcy bazy danych SQL został przekroczony limit czasu, próbując uzyskać blokadę wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="855d0-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="855d0-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="855d0-114">Message</span></span>  
 <span data-ttu-id="855d0-115">Limit czasu, próbując uzyskać blokadę wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="855d0-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="855d0-116">Operacja nie została ukończona w ciągu przydzielonego limitu czasu %1.</span><span class="sxs-lookup"><span data-stu-id="855d0-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="855d0-117">Czas przydzielony na tę operację mógł stanowić część większego limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="855d0-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="855d0-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="855d0-118">Details</span></span>  
  
|<span data-ttu-id="855d0-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="855d0-119">Data Item Name</span></span>|<span data-ttu-id="855d0-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="855d0-120">Data Item Type</span></span>|<span data-ttu-id="855d0-121">Opis</span><span class="sxs-lookup"><span data-stu-id="855d0-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="855d0-122">Opóźnienie</span><span class="sxs-lookup"><span data-stu-id="855d0-122">Delay</span></span>|<span data-ttu-id="855d0-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="855d0-123">xs:string</span></span>|<span data-ttu-id="855d0-124">Opóźnienie między ponownymi próbami.</span><span class="sxs-lookup"><span data-stu-id="855d0-124">The delay between retries.</span></span>|  
|<span data-ttu-id="855d0-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="855d0-125">AppDomain</span></span>|<span data-ttu-id="855d0-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="855d0-126">xs:string</span></span>|<span data-ttu-id="855d0-127">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="855d0-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
