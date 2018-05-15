---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 89643edde5856688c762b0cf0d188bd4e7ba8a24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="0d7af-102">3551 - BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="0d7af-102">3551 - BufferOutOfOrderMessageNoBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="0d7af-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="0d7af-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0d7af-104">ID</span><span class="sxs-lookup"><span data-stu-id="0d7af-104">ID</span></span>|<span data-ttu-id="0d7af-105">3551</span><span class="sxs-lookup"><span data-stu-id="0d7af-105">3551</span></span>|  
|<span data-ttu-id="0d7af-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="0d7af-106">Keywords</span></span>|<span data-ttu-id="0d7af-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="0d7af-107">WFServices</span></span>|  
|<span data-ttu-id="0d7af-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="0d7af-108">Level</span></span>|<span data-ttu-id="0d7af-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="0d7af-109">Information</span></span>|  
|<span data-ttu-id="0d7af-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="0d7af-110">Channel</span></span>|<span data-ttu-id="0d7af-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="0d7af-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0d7af-112">Opis</span><span class="sxs-lookup"><span data-stu-id="0d7af-112">Description</span></span>  
 <span data-ttu-id="0d7af-113">Wskazuje, że nie powiodło się wznowienie zakładki.</span><span class="sxs-lookup"><span data-stu-id="0d7af-113">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="0d7af-114">Buforowany operacji odbierania zostanie podjęta ponownie gdy wystąpienie usługi będzie gotowe do przetworzenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="0d7af-114">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0d7af-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="0d7af-115">Message</span></span>  
 <span data-ttu-id="0d7af-116">W tej chwili nie można wykonać operacji "%2" dla wystąpienia usługi "%1".</span><span class="sxs-lookup"><span data-stu-id="0d7af-116">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="0d7af-117">Kolejna próba zostanie podjęta, gdy wystąpienie usługi będzie gotowe do przetworzenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="0d7af-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0d7af-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="0d7af-118">Details</span></span>  
  
|<span data-ttu-id="0d7af-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="0d7af-119">Data Item Name</span></span>|<span data-ttu-id="0d7af-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="0d7af-120">Data Item Type</span></span>|<span data-ttu-id="0d7af-121">Opis</span><span class="sxs-lookup"><span data-stu-id="0d7af-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0d7af-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="0d7af-122">OperationName</span></span>|<span data-ttu-id="0d7af-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="0d7af-123">xs:string</span></span>|<span data-ttu-id="0d7af-124">Nazwa operacji.</span><span class="sxs-lookup"><span data-stu-id="0d7af-124">The name of the operation.</span></span>|  
|<span data-ttu-id="0d7af-125">ServiceInstanceId</span><span class="sxs-lookup"><span data-stu-id="0d7af-125">ServiceInstanceId</span></span>|<span data-ttu-id="0d7af-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="0d7af-126">xs:string</span></span>|<span data-ttu-id="0d7af-127">Identyfikator wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="0d7af-127">The id of the service instance.</span></span>|  
|<span data-ttu-id="0d7af-128">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="0d7af-128">AppDomain</span></span>|<span data-ttu-id="0d7af-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="0d7af-129">xs:string</span></span>|<span data-ttu-id="0d7af-130">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0d7af-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
