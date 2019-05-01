---
title: 1125 — InvokeMethodIsNotStatic
ms.date: 03/30/2017
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
ms.openlocfilehash: 692c5e56dac0a69ab5705acd284f048391145641
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924268"
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="1c1b3-102">1125 — InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="1c1b3-102">1125 - InvokeMethodIsNotStatic</span></span>
## <a name="properties"></a><span data-ttu-id="1c1b3-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1c1b3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1c1b3-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="1c1b3-104">ID</span></span>|<span data-ttu-id="1c1b3-105">1125</span><span class="sxs-lookup"><span data-stu-id="1c1b3-105">1125</span></span>|  
|<span data-ttu-id="1c1b3-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="1c1b3-106">Keywords</span></span>|<span data-ttu-id="1c1b3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1c1b3-107">WFRuntime</span></span>|  
|<span data-ttu-id="1c1b3-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="1c1b3-108">Level</span></span>|<span data-ttu-id="1c1b3-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="1c1b3-109">Information</span></span>|  
|<span data-ttu-id="1c1b3-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="1c1b3-110">Channel</span></span>|<span data-ttu-id="1c1b3-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="1c1b3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1c1b3-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1c1b3-112">Description</span></span>  
 <span data-ttu-id="1c1b3-113">Podczas wykonywania kroku użyciu metody CacheMetadata działania InvokeMethod wskazuje, że wywoływanej metody nie jest statyczne.</span><span class="sxs-lookup"><span data-stu-id="1c1b3-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1c1b3-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="1c1b3-114">Message</span></span>  
 <span data-ttu-id="1c1b3-115">InvokeMethod "%1" - metoda nie jest statyczne.</span><span class="sxs-lookup"><span data-stu-id="1c1b3-115">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1c1b3-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1c1b3-116">Details</span></span>  
  
|<span data-ttu-id="1c1b3-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="1c1b3-117">Data Item Name</span></span>|<span data-ttu-id="1c1b3-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="1c1b3-118">Data Item Type</span></span>|<span data-ttu-id="1c1b3-119">Opis</span><span class="sxs-lookup"><span data-stu-id="1c1b3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1c1b3-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="1c1b3-120">InvokeMethod</span></span>|<span data-ttu-id="1c1b3-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="1c1b3-121">xs:string</span></span>|<span data-ttu-id="1c1b3-122">Nazwa wyświetlana działania InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="1c1b3-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="1c1b3-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1c1b3-123">AppDomain</span></span>|<span data-ttu-id="1c1b3-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="1c1b3-124">xs:string</span></span>|<span data-ttu-id="1c1b3-125">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1c1b3-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
