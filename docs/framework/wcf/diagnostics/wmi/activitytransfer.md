---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 6237d65d6964a4ebca34af895158c83239641593
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662820"
---
# <a name="activitytransfer"></a><span data-ttu-id="c8251-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="c8251-102">ActivityTransfer</span></span>
<span data-ttu-id="c8251-103">Zdarzenia transferu aktywności</span><span class="sxs-lookup"><span data-stu-id="c8251-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8251-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8251-104">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c8251-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c8251-105">Methods</span></span>  
 <span data-ttu-id="c8251-106">Klasa ActivityTransfer nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="c8251-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c8251-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c8251-107">Properties</span></span>  
 <span data-ttu-id="c8251-108">Klasa ActivityTransfer ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="c8251-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="c8251-109">Identyfikator działania</span><span class="sxs-lookup"><span data-stu-id="c8251-109">ActivityID</span></span>  
  
- <span data-ttu-id="c8251-110">Typ danych: obiekt</span><span class="sxs-lookup"><span data-stu-id="c8251-110">Data type: object</span></span>  
    <span data-ttu-id="c8251-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c8251-111">Access type: Read-only</span></span>  
  
- <span data-ttu-id="c8251-112">Identyfikator działania</span><span class="sxs-lookup"><span data-stu-id="c8251-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="c8251-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="c8251-113">RelatedActivityID</span></span>  
  
- <span data-ttu-id="c8251-114">Typ danych: obiekt</span><span class="sxs-lookup"><span data-stu-id="c8251-114">Data type: object</span></span>  
    <span data-ttu-id="c8251-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c8251-115">Access type: Read-only</span></span>  
  
- <span data-ttu-id="c8251-116">Identyfikator działania powiązane</span><span class="sxs-lookup"><span data-stu-id="c8251-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8251-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c8251-117">Requirements</span></span>  
  
|<span data-ttu-id="c8251-118">MOF</span><span class="sxs-lookup"><span data-stu-id="c8251-118">MOF</span></span>|<span data-ttu-id="c8251-119">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c8251-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c8251-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="c8251-120">Namespace</span></span>|<span data-ttu-id="c8251-121">Zdefiniowane w root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="c8251-121">Defined in root\ServiceModel.</span></span>|
