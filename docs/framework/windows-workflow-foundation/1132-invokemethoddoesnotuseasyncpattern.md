---
title: 1132 — InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 64701d4c38c042e8273129be19f9caeb2c442abf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924218"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="72967-102">1132 — InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="72967-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="72967-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="72967-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="72967-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="72967-104">ID</span></span>|<span data-ttu-id="72967-105">1132</span><span class="sxs-lookup"><span data-stu-id="72967-105">1132</span></span>|  
|<span data-ttu-id="72967-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="72967-106">Keywords</span></span>|<span data-ttu-id="72967-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="72967-107">WFRuntime</span></span>|  
|<span data-ttu-id="72967-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="72967-108">Level</span></span>|<span data-ttu-id="72967-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="72967-109">Information</span></span>|  
|<span data-ttu-id="72967-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="72967-110">Channel</span></span>|<span data-ttu-id="72967-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="72967-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="72967-112">Opis</span><span class="sxs-lookup"><span data-stu-id="72967-112">Description</span></span>  
 <span data-ttu-id="72967-113">Podczas wykonywania kroku użyciu metody CacheMetadata działania InvokeMethod wskazuje, że nie używa wzorca asynchronicznego podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="72967-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="72967-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="72967-114">Message</span></span>  
 <span data-ttu-id="72967-115">InvokeMethod "%1" - metoda nie korzysta z wzorca asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="72967-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="72967-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="72967-116">Details</span></span>  
  
|<span data-ttu-id="72967-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="72967-117">Data Item Name</span></span>|<span data-ttu-id="72967-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="72967-118">Data Item Type</span></span>|<span data-ttu-id="72967-119">Opis</span><span class="sxs-lookup"><span data-stu-id="72967-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="72967-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="72967-120">InvokeMethod</span></span>|<span data-ttu-id="72967-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="72967-121">xs:string</span></span>|<span data-ttu-id="72967-122">Nazwa wyświetlana działania InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="72967-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="72967-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="72967-123">AppDomain</span></span>|<span data-ttu-id="72967-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="72967-124">xs:string</span></span>|<span data-ttu-id="72967-125">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="72967-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
