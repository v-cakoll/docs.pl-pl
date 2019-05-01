---
title: 1126 — InvokedMethodThrewException
ms.date: 03/30/2017
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
ms.openlocfilehash: 714a98a300426d80c3b494d701ae1bd53a49592f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924010"
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="9cfa3-102">1126 — InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="9cfa3-102">1126 - InvokedMethodThrewException</span></span>
## <a name="properties"></a><span data-ttu-id="9cfa3-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="9cfa3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9cfa3-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="9cfa3-104">ID</span></span>|<span data-ttu-id="9cfa3-105">1126</span><span class="sxs-lookup"><span data-stu-id="9cfa3-105">1126</span></span>|  
|<span data-ttu-id="9cfa3-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="9cfa3-106">Keywords</span></span>|<span data-ttu-id="9cfa3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9cfa3-107">WFRuntime</span></span>|  
|<span data-ttu-id="9cfa3-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="9cfa3-108">Level</span></span>|<span data-ttu-id="9cfa3-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="9cfa3-109">Information</span></span>|  
|<span data-ttu-id="9cfa3-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="9cfa3-110">Channel</span></span>|<span data-ttu-id="9cfa3-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9cfa3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9cfa3-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9cfa3-112">Description</span></span>  
 <span data-ttu-id="9cfa3-113">Wskazuje, że wyjątek został zgłoszony przez metody wywołane przez działania InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="9cfa3-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9cfa3-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="9cfa3-114">Message</span></span>  
 <span data-ttu-id="9cfa3-115">Zgłoszono wyjątek metody wywoływane przez działanie "%1".</span><span class="sxs-lookup"><span data-stu-id="9cfa3-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="9cfa3-116">%2</span><span class="sxs-lookup"><span data-stu-id="9cfa3-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="9cfa3-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="9cfa3-117">Details</span></span>  
  
|<span data-ttu-id="9cfa3-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="9cfa3-118">Data Item Name</span></span>|<span data-ttu-id="9cfa3-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="9cfa3-119">Data Item Type</span></span>|<span data-ttu-id="9cfa3-120">Opis</span><span class="sxs-lookup"><span data-stu-id="9cfa3-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9cfa3-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="9cfa3-121">InvokeMethod</span></span>|<span data-ttu-id="9cfa3-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="9cfa3-122">xs:string</span></span>|<span data-ttu-id="9cfa3-123">Nazwa wyświetlana działania InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="9cfa3-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="9cfa3-124">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="9cfa3-124">Exception</span></span>|<span data-ttu-id="9cfa3-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="9cfa3-125">xs:string</span></span>|<span data-ttu-id="9cfa3-126">Szczegóły wyjątku, dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="9cfa3-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="9cfa3-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9cfa3-127">AppDomain</span></span>|<span data-ttu-id="9cfa3-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="9cfa3-128">xs:string</span></span>|<span data-ttu-id="9cfa3-129">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9cfa3-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
