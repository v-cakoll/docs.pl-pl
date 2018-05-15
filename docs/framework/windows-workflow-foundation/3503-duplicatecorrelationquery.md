---
title: 3503 - DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: 37a689b30b0bcab9124472deb98627afbe30dfee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="cf27e-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="cf27e-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="cf27e-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="cf27e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cf27e-104">ID</span><span class="sxs-lookup"><span data-stu-id="cf27e-104">ID</span></span>|<span data-ttu-id="cf27e-105">3503</span><span class="sxs-lookup"><span data-stu-id="cf27e-105">3503</span></span>|  
|<span data-ttu-id="cf27e-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="cf27e-106">Keywords</span></span>|<span data-ttu-id="cf27e-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="cf27e-107">WFServices</span></span>|  
|<span data-ttu-id="cf27e-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="cf27e-108">Level</span></span>|<span data-ttu-id="cf27e-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="cf27e-109">Warning</span></span>|  
|<span data-ttu-id="cf27e-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="cf27e-110">Channel</span></span>|<span data-ttu-id="cf27e-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="cf27e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cf27e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="cf27e-112">Description</span></span>  
 <span data-ttu-id="cf27e-113">Wskazuje, że znaleziono zduplikowane CorrelationQuery.</span><span class="sxs-lookup"><span data-stu-id="cf27e-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="cf27e-114">Zduplikowane zapytanie nie zostanie użyte, podczas obliczania korelacji.</span><span class="sxs-lookup"><span data-stu-id="cf27e-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cf27e-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="cf27e-115">Message</span></span>  
 <span data-ttu-id="cf27e-116">Znaleziono zduplikowane CorrelationQuery o Where = '%1'.</span><span class="sxs-lookup"><span data-stu-id="cf27e-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="cf27e-117">To zduplikowane zapytanie nie zostanie użyte podczas obliczania korelacji.</span><span class="sxs-lookup"><span data-stu-id="cf27e-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cf27e-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="cf27e-118">Details</span></span>  
  
|<span data-ttu-id="cf27e-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="cf27e-119">Data Item Name</span></span>|<span data-ttu-id="cf27e-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="cf27e-120">Data Item Type</span></span>|<span data-ttu-id="cf27e-121">Opis</span><span class="sxs-lookup"><span data-stu-id="cf27e-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cf27e-122">Gdzie</span><span class="sxs-lookup"><span data-stu-id="cf27e-122">Where</span></span>|<span data-ttu-id="cf27e-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="cf27e-123">xs:string</span></span>|<span data-ttu-id="cf27e-124">Gdzie część zapytania korelacji.</span><span class="sxs-lookup"><span data-stu-id="cf27e-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="cf27e-125">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="cf27e-125">AppDomain</span></span>|<span data-ttu-id="cf27e-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="cf27e-126">xs:string</span></span>|<span data-ttu-id="cf27e-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="cf27e-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
