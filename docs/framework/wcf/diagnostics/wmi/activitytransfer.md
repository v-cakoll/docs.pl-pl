---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 936e870c1ec991e2e33acf8a08ccc93975989679
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50034433"
---
# <a name="activitytransfer"></a><span data-ttu-id="07b65-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="07b65-102">ActivityTransfer</span></span>
<span data-ttu-id="07b65-103">Zdarzenia transferu aktywności</span><span class="sxs-lookup"><span data-stu-id="07b65-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07b65-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="07b65-104">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="07b65-105">Metody</span><span class="sxs-lookup"><span data-stu-id="07b65-105">Methods</span></span>  
 <span data-ttu-id="07b65-106">Klasa ActivityTransfer nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="07b65-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="07b65-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="07b65-107">Properties</span></span>  
 <span data-ttu-id="07b65-108">Klasa ActivityTransfer ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="07b65-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="07b65-109">Identyfikator działania</span><span class="sxs-lookup"><span data-stu-id="07b65-109">ActivityID</span></span>  
  
-   <span data-ttu-id="07b65-110">Typ danych: obiekt</span><span class="sxs-lookup"><span data-stu-id="07b65-110">Data type: object</span></span>  
    <span data-ttu-id="07b65-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07b65-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="07b65-112">Identyfikator działania</span><span class="sxs-lookup"><span data-stu-id="07b65-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="07b65-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="07b65-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="07b65-114">Typ danych: obiekt</span><span class="sxs-lookup"><span data-stu-id="07b65-114">Data type: object</span></span>  
    <span data-ttu-id="07b65-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07b65-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="07b65-116">Identyfikator działania powiązane</span><span class="sxs-lookup"><span data-stu-id="07b65-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07b65-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="07b65-117">Requirements</span></span>  
  
|<span data-ttu-id="07b65-118">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="07b65-118">MOF</span></span>|<span data-ttu-id="07b65-119">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="07b65-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="07b65-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="07b65-120">Namespace</span></span>|<span data-ttu-id="07b65-121">Zdefiniowane w root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="07b65-121">Defined in root\ServiceModel.</span></span>|
