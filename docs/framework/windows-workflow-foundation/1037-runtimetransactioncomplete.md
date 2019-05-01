---
title: 1037 — RuntimeTransactionComplete
ms.date: 03/30/2017
ms.assetid: 2c8c31e0-42a9-4f46-865b-2da9ab16a0ba
ms.openlocfilehash: 7a94c917157904c5cb84105c41842657a534c973
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924296"
---
# <a name="1037---runtimetransactioncomplete"></a><span data-ttu-id="cf8dc-102">1037 — RuntimeTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="cf8dc-102">1037 - RuntimeTransactionComplete</span></span>
## <a name="properties"></a><span data-ttu-id="cf8dc-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="cf8dc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cf8dc-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="cf8dc-104">ID</span></span>|<span data-ttu-id="cf8dc-105">1037</span><span class="sxs-lookup"><span data-stu-id="cf8dc-105">1037</span></span>|  
|<span data-ttu-id="cf8dc-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="cf8dc-106">Keywords</span></span>|<span data-ttu-id="cf8dc-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="cf8dc-107">WFRuntime</span></span>|  
|<span data-ttu-id="cf8dc-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="cf8dc-108">Level</span></span>|<span data-ttu-id="cf8dc-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="cf8dc-109">Verbose</span></span>|  
|<span data-ttu-id="cf8dc-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="cf8dc-110">Channel</span></span>|<span data-ttu-id="cf8dc-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="cf8dc-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cf8dc-112">Opis</span><span class="sxs-lookup"><span data-stu-id="cf8dc-112">Description</span></span>  
 <span data-ttu-id="cf8dc-113">Wskazuje, że transakcja środowiska uruchomieniowego została zakończona.</span><span class="sxs-lookup"><span data-stu-id="cf8dc-113">Indicates the runtime transaction has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cf8dc-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="cf8dc-114">Message</span></span>  
 <span data-ttu-id="cf8dc-115">Transakcja środowiska uruchomieniowego została ukończona ze stanem "%1".</span><span class="sxs-lookup"><span data-stu-id="cf8dc-115">The runtime transaction has completed with the state '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cf8dc-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="cf8dc-116">Details</span></span>  
  
|<span data-ttu-id="cf8dc-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="cf8dc-117">Data Item Name</span></span>|<span data-ttu-id="cf8dc-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="cf8dc-118">Data Item Type</span></span>|<span data-ttu-id="cf8dc-119">Opis</span><span class="sxs-lookup"><span data-stu-id="cf8dc-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cf8dc-120">Stan</span><span class="sxs-lookup"><span data-stu-id="cf8dc-120">State</span></span>|<span data-ttu-id="cf8dc-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="cf8dc-121">xs:string</span></span>|<span data-ttu-id="cf8dc-122">Stan transakcji.</span><span class="sxs-lookup"><span data-stu-id="cf8dc-122">The state of the transaction.</span></span>|  
|<span data-ttu-id="cf8dc-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cf8dc-123">AppDomain</span></span>|<span data-ttu-id="cf8dc-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="cf8dc-124">xs:string</span></span>|<span data-ttu-id="cf8dc-125">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="cf8dc-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
