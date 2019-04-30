---
title: 3550 — BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: 1af943e23aa643c6614b946175c0b1854a7ceb62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755587"
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="1dbcc-102">3550 — BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="1dbcc-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="1dbcc-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1dbcc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1dbcc-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="1dbcc-104">ID</span></span>|<span data-ttu-id="1dbcc-105">3550</span><span class="sxs-lookup"><span data-stu-id="1dbcc-105">3550</span></span>|  
|<span data-ttu-id="1dbcc-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="1dbcc-106">Keywords</span></span>|<span data-ttu-id="1dbcc-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="1dbcc-107">WFServices</span></span>|  
|<span data-ttu-id="1dbcc-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="1dbcc-108">Level</span></span>|<span data-ttu-id="1dbcc-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="1dbcc-109">Information</span></span>|  
|<span data-ttu-id="1dbcc-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="1dbcc-110">Channel</span></span>|<span data-ttu-id="1dbcc-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="1dbcc-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1dbcc-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1dbcc-112">Description</span></span>  
 <span data-ttu-id="1dbcc-113">Wskazuje, że buforowane odbieranie nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="1dbcc-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="1dbcc-114">Operacja zostanie podjęta ponownie, gdy wystąpienie usługi jest gotowy do przetwarzania tej operacji.</span><span class="sxs-lookup"><span data-stu-id="1dbcc-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1dbcc-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="1dbcc-115">Message</span></span>  
 <span data-ttu-id="1dbcc-116">W tej chwili nie można wykonać operacji "%1".</span><span class="sxs-lookup"><span data-stu-id="1dbcc-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="1dbcc-117">Nastąpi wtedy podjąć kolejną próbę, gdy wystąpienie usługi jest gotowy do przetwarzania tej operacji.</span><span class="sxs-lookup"><span data-stu-id="1dbcc-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1dbcc-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1dbcc-118">Details</span></span>  
  
|<span data-ttu-id="1dbcc-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="1dbcc-119">Data Item Name</span></span>|<span data-ttu-id="1dbcc-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="1dbcc-120">Data Item Type</span></span>|<span data-ttu-id="1dbcc-121">Opis</span><span class="sxs-lookup"><span data-stu-id="1dbcc-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1dbcc-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="1dbcc-122">OperationName</span></span>|<span data-ttu-id="1dbcc-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="1dbcc-123">xs:string</span></span>|<span data-ttu-id="1dbcc-124">Nazwa operacji.</span><span class="sxs-lookup"><span data-stu-id="1dbcc-124">The name of the operation.</span></span>|  
|<span data-ttu-id="1dbcc-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1dbcc-125">AppDomain</span></span>|<span data-ttu-id="1dbcc-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="1dbcc-126">xs:string</span></span>|<span data-ttu-id="1dbcc-127">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1dbcc-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
