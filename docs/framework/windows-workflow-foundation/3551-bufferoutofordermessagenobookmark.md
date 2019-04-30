---
title: 3551 — BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 89643edde5856688c762b0cf0d188bd4e7ba8a24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755535"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="8e419-102">3551 — BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="8e419-102">3551 - BufferOutOfOrderMessageNoBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="8e419-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="8e419-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8e419-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="8e419-104">ID</span></span>|<span data-ttu-id="8e419-105">3551</span><span class="sxs-lookup"><span data-stu-id="8e419-105">3551</span></span>|  
|<span data-ttu-id="8e419-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="8e419-106">Keywords</span></span>|<span data-ttu-id="8e419-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="8e419-107">WFServices</span></span>|  
|<span data-ttu-id="8e419-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="8e419-108">Level</span></span>|<span data-ttu-id="8e419-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="8e419-109">Information</span></span>|  
|<span data-ttu-id="8e419-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="8e419-110">Channel</span></span>|<span data-ttu-id="8e419-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="8e419-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8e419-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8e419-112">Description</span></span>  
 <span data-ttu-id="8e419-113">Wskazuje, że nie powiodło się wznowienie zakładki.</span><span class="sxs-lookup"><span data-stu-id="8e419-113">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="8e419-114">Buforowane odbieranie operacji zostanie podjęta ponownie kiedy wystąpienie usługi jest gotowy do przetwarzania tej operacji.</span><span class="sxs-lookup"><span data-stu-id="8e419-114">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8e419-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="8e419-115">Message</span></span>  
 <span data-ttu-id="8e419-116">Nie można wykonać operacji "%2" na wystąpienie usługi "%1" w tej chwili.</span><span class="sxs-lookup"><span data-stu-id="8e419-116">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="8e419-117">Nastąpi wtedy podjąć kolejną próbę, gdy wystąpienie usługi jest gotowy do przetwarzania tej operacji.</span><span class="sxs-lookup"><span data-stu-id="8e419-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8e419-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8e419-118">Details</span></span>  
  
|<span data-ttu-id="8e419-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="8e419-119">Data Item Name</span></span>|<span data-ttu-id="8e419-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="8e419-120">Data Item Type</span></span>|<span data-ttu-id="8e419-121">Opis</span><span class="sxs-lookup"><span data-stu-id="8e419-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8e419-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="8e419-122">OperationName</span></span>|<span data-ttu-id="8e419-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="8e419-123">xs:string</span></span>|<span data-ttu-id="8e419-124">Nazwa operacji.</span><span class="sxs-lookup"><span data-stu-id="8e419-124">The name of the operation.</span></span>|  
|<span data-ttu-id="8e419-125">ServiceInstanceId</span><span class="sxs-lookup"><span data-stu-id="8e419-125">ServiceInstanceId</span></span>|<span data-ttu-id="8e419-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="8e419-126">xs:string</span></span>|<span data-ttu-id="8e419-127">Identyfikator wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="8e419-127">The id of the service instance.</span></span>|  
|<span data-ttu-id="8e419-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8e419-128">AppDomain</span></span>|<span data-ttu-id="8e419-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="8e419-129">xs:string</span></span>|<span data-ttu-id="8e419-130">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8e419-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
