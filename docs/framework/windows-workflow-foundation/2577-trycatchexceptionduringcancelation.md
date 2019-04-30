---
title: 2577 — TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: c272dd91249dfc90e6f4c38a7339919a5a6446e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755626"
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="e158a-102">2577 — TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="e158a-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="e158a-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e158a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e158a-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="e158a-104">ID</span></span>|<span data-ttu-id="e158a-105">2577</span><span class="sxs-lookup"><span data-stu-id="e158a-105">2577</span></span>|  
|<span data-ttu-id="e158a-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="e158a-106">Keywords</span></span>|<span data-ttu-id="e158a-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="e158a-107">WFActivities</span></span>|  
|<span data-ttu-id="e158a-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="e158a-108">Level</span></span>|<span data-ttu-id="e158a-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="e158a-109">Warning</span></span>|  
|<span data-ttu-id="e158a-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="e158a-110">Channel</span></span>|<span data-ttu-id="e158a-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e158a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e158a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e158a-112">Description</span></span>  
 <span data-ttu-id="e158a-113">Wskazuje, że działanie podrzędne działania TryCatch został zgłoszony wyjątek w trakcie anulowania.</span><span class="sxs-lookup"><span data-stu-id="e158a-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e158a-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="e158a-114">Message</span></span>  
 <span data-ttu-id="e158a-115">Działanie podrzędne działania TryCatch '%1' został zgłoszony wyjątek w trakcie anulowania.</span><span class="sxs-lookup"><span data-stu-id="e158a-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e158a-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e158a-116">Details</span></span>  
  
|<span data-ttu-id="e158a-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="e158a-117">Data Item Name</span></span>|<span data-ttu-id="e158a-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="e158a-118">Data Item Type</span></span>|<span data-ttu-id="e158a-119">Opis</span><span class="sxs-lookup"><span data-stu-id="e158a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e158a-120">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="e158a-120">DisplayName</span></span>|<span data-ttu-id="e158a-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="e158a-121">xs:string</span></span>|<span data-ttu-id="e158a-122">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="e158a-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="e158a-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e158a-123">AppDomain</span></span>|<span data-ttu-id="e158a-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="e158a-124">xs:string</span></span>|<span data-ttu-id="e158a-125">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e158a-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
