---
title: 2577 - TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: c272dd91249dfc90e6f4c38a7339919a5a6446e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510734"
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="47d3d-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="47d3d-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="47d3d-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="47d3d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="47d3d-104">ID</span><span class="sxs-lookup"><span data-stu-id="47d3d-104">ID</span></span>|<span data-ttu-id="47d3d-105">2577</span><span class="sxs-lookup"><span data-stu-id="47d3d-105">2577</span></span>|  
|<span data-ttu-id="47d3d-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="47d3d-106">Keywords</span></span>|<span data-ttu-id="47d3d-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="47d3d-107">WFActivities</span></span>|  
|<span data-ttu-id="47d3d-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="47d3d-108">Level</span></span>|<span data-ttu-id="47d3d-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="47d3d-109">Warning</span></span>|  
|<span data-ttu-id="47d3d-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="47d3d-110">Channel</span></span>|<span data-ttu-id="47d3d-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="47d3d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="47d3d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="47d3d-112">Description</span></span>  
 <span data-ttu-id="47d3d-113">Wskazuje, że działanie podrzędne działania TryCatch wywołało wyjątek podczas anulowania.</span><span class="sxs-lookup"><span data-stu-id="47d3d-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="47d3d-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="47d3d-114">Message</span></span>  
 <span data-ttu-id="47d3d-115">Działanie podrzędne działania TryCatch "%1" wywołało wyjątek podczas anulowania.</span><span class="sxs-lookup"><span data-stu-id="47d3d-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="47d3d-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="47d3d-116">Details</span></span>  
  
|<span data-ttu-id="47d3d-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="47d3d-117">Data Item Name</span></span>|<span data-ttu-id="47d3d-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="47d3d-118">Data Item Type</span></span>|<span data-ttu-id="47d3d-119">Opis</span><span class="sxs-lookup"><span data-stu-id="47d3d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="47d3d-120">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="47d3d-120">DisplayName</span></span>|<span data-ttu-id="47d3d-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="47d3d-121">xs:string</span></span>|<span data-ttu-id="47d3d-122">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="47d3d-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="47d3d-123">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="47d3d-123">AppDomain</span></span>|<span data-ttu-id="47d3d-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="47d3d-124">xs:string</span></span>|<span data-ttu-id="47d3d-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="47d3d-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
