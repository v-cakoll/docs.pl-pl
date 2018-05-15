---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 480670f19407321eb0928d07752936b2ece1f7e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="activitytransfer"></a><span data-ttu-id="53a58-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="53a58-102">ActivityTransfer</span></span>
<span data-ttu-id="53a58-103">Zdarzenie transferu aktywności</span><span class="sxs-lookup"><span data-stu-id="53a58-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53a58-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="53a58-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="53a58-105">Metody</span><span class="sxs-lookup"><span data-stu-id="53a58-105">Methods</span></span>  
 <span data-ttu-id="53a58-106">Klasa ActivityTransfer nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="53a58-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="53a58-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="53a58-107">Properties</span></span>  
 <span data-ttu-id="53a58-108">Klasa ActivityTransfer ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="53a58-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="53a58-109">Identyfikator działania</span><span class="sxs-lookup"><span data-stu-id="53a58-109">ActivityID</span></span>  
  
-   <span data-ttu-id="53a58-110">Typ danych: obiekt</span><span class="sxs-lookup"><span data-stu-id="53a58-110">Data type: object</span></span>  
    <span data-ttu-id="53a58-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="53a58-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="53a58-112">Identyfikator działania</span><span class="sxs-lookup"><span data-stu-id="53a58-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="53a58-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="53a58-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="53a58-114">Typ danych: obiekt</span><span class="sxs-lookup"><span data-stu-id="53a58-114">Data type: object</span></span>  
    <span data-ttu-id="53a58-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="53a58-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="53a58-116">Identyfikator działania pokrewne</span><span class="sxs-lookup"><span data-stu-id="53a58-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53a58-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="53a58-117">Requirements</span></span>  
  
|<span data-ttu-id="53a58-118">MOF</span><span class="sxs-lookup"><span data-stu-id="53a58-118">MOF</span></span>|<span data-ttu-id="53a58-119">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="53a58-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="53a58-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="53a58-120">Namespace</span></span>|<span data-ttu-id="53a58-121">Zdefiniowany w root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="53a58-121">Defined in root\ServiceModel.</span></span>|
