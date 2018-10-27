---
title: ServiceTimeoutsBehavior
ms.date: 03/30/2017
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
ms.openlocfilehash: 1a5284915de739e95325234318842a4d1ab607be
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/26/2018
ms.locfileid: "50135248"
---
# <a name="servicetimeoutsbehavior"></a><span data-ttu-id="3d0a7-102">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="3d0a7-102">ServiceTimeoutsBehavior</span></span>
<span data-ttu-id="3d0a7-103">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="3d0a7-103">ServiceTimeoutsBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d0a7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d0a7-104">Syntax</span></span>  
  
```csharp
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3d0a7-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3d0a7-105">Methods</span></span>  
 <span data-ttu-id="3d0a7-106">Klasa ServiceTimeoutsBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="3d0a7-106">The ServiceTimeoutsBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3d0a7-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3d0a7-107">Properties</span></span>  
 <span data-ttu-id="3d0a7-108">Klasa ServiceTimeoutsBehavior ma następującą właściwość:</span><span class="sxs-lookup"><span data-stu-id="3d0a7-108">The ServiceTimeoutsBehavior class has the following property:</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="3d0a7-109">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="3d0a7-109">TransactionTimeout</span></span>  
 <span data-ttu-id="3d0a7-110">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="3d0a7-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="3d0a7-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3d0a7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3d0a7-112">Okres, w którym należy wykonać transakcję.</span><span class="sxs-lookup"><span data-stu-id="3d0a7-112">The period within which a transaction must complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d0a7-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3d0a7-113">Requirements</span></span>  
  
|<span data-ttu-id="3d0a7-114">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="3d0a7-114">MOF</span></span>|<span data-ttu-id="3d0a7-115">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3d0a7-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3d0a7-116">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="3d0a7-116">Namespace</span></span>|<span data-ttu-id="3d0a7-117">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3d0a7-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3d0a7-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d0a7-118">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
