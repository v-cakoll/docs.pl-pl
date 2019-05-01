---
title: 4209 — TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: d61d710959f99dbc8a91441766a690eb7e9a365c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774273"
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="1b115-102">4209 — TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="1b115-102">4209 - TimeoutOpeningSqlConnection</span></span>
## <a name="properties"></a><span data-ttu-id="1b115-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1b115-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1b115-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="1b115-104">ID</span></span>|<span data-ttu-id="1b115-105">4209</span><span class="sxs-lookup"><span data-stu-id="1b115-105">4209</span></span>|  
|<span data-ttu-id="1b115-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="1b115-106">Keywords</span></span>|<span data-ttu-id="1b115-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="1b115-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="1b115-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="1b115-108">Level</span></span>|<span data-ttu-id="1b115-109">Błąd</span><span class="sxs-lookup"><span data-stu-id="1b115-109">Error</span></span>|  
|<span data-ttu-id="1b115-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="1b115-110">Channel</span></span>|<span data-ttu-id="1b115-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="1b115-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1b115-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1b115-112">Description</span></span>  
 <span data-ttu-id="1b115-113">Wskazuje, że limit czasu podczas próby otwarcia połączenia SQL.</span><span class="sxs-lookup"><span data-stu-id="1b115-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1b115-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="1b115-114">Message</span></span>  
 <span data-ttu-id="1b115-115">Limit czasu podczas próby otwarcia połączenia SQL.</span><span class="sxs-lookup"><span data-stu-id="1b115-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="1b115-116">Operacja nie została ukończona w ciągu przydzielonego limitu czasu %1.</span><span class="sxs-lookup"><span data-stu-id="1b115-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="1b115-117">Czas przydzielony na tę operację mógł stanowić część większego limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="1b115-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1b115-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1b115-118">Details</span></span>  
  
|<span data-ttu-id="1b115-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="1b115-119">Data Item Name</span></span>|<span data-ttu-id="1b115-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="1b115-120">Data Item Type</span></span>|<span data-ttu-id="1b115-121">Opis</span><span class="sxs-lookup"><span data-stu-id="1b115-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1b115-122">limit czasu</span><span class="sxs-lookup"><span data-stu-id="1b115-122">Timeout</span></span>|<span data-ttu-id="1b115-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="1b115-123">xs:string</span></span>|<span data-ttu-id="1b115-124">Limit czasu otwierania połączenia SQL.</span><span class="sxs-lookup"><span data-stu-id="1b115-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="1b115-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1b115-125">AppDomain</span></span>|<span data-ttu-id="1b115-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="1b115-126">xs:string</span></span>|<span data-ttu-id="1b115-127">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1b115-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
