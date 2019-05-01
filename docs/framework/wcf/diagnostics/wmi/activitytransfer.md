---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 936e870c1ec991e2e33acf8a08ccc93975989679
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964298"
---
# <a name="activitytransfer"></a><span data-ttu-id="20bdd-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="20bdd-102">ActivityTransfer</span></span>
<span data-ttu-id="20bdd-103">Zdarzenia transferu aktywności</span><span class="sxs-lookup"><span data-stu-id="20bdd-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20bdd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20bdd-104">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="20bdd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="20bdd-105">Methods</span></span>  
 <span data-ttu-id="20bdd-106">Klasa ActivityTransfer nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="20bdd-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="20bdd-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="20bdd-107">Properties</span></span>  
 <span data-ttu-id="20bdd-108">Klasa ActivityTransfer ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="20bdd-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="20bdd-109">Identyfikator działania</span><span class="sxs-lookup"><span data-stu-id="20bdd-109">ActivityID</span></span>  
  
- <span data-ttu-id="20bdd-110">Typ danych: obiekt</span><span class="sxs-lookup"><span data-stu-id="20bdd-110">Data type: object</span></span>  
    <span data-ttu-id="20bdd-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="20bdd-111">Access type: Read-only</span></span>  
  
- <span data-ttu-id="20bdd-112">Identyfikator działania</span><span class="sxs-lookup"><span data-stu-id="20bdd-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="20bdd-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="20bdd-113">RelatedActivityID</span></span>  
  
- <span data-ttu-id="20bdd-114">Typ danych: obiekt</span><span class="sxs-lookup"><span data-stu-id="20bdd-114">Data type: object</span></span>  
    <span data-ttu-id="20bdd-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="20bdd-115">Access type: Read-only</span></span>  
  
- <span data-ttu-id="20bdd-116">Identyfikator działania powiązane</span><span class="sxs-lookup"><span data-stu-id="20bdd-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20bdd-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20bdd-117">Requirements</span></span>  
  
|<span data-ttu-id="20bdd-118">MOF</span><span class="sxs-lookup"><span data-stu-id="20bdd-118">MOF</span></span>|<span data-ttu-id="20bdd-119">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="20bdd-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="20bdd-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="20bdd-120">Namespace</span></span>|<span data-ttu-id="20bdd-121">Zdefiniowane w root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="20bdd-121">Defined in root\ServiceModel.</span></span>|
