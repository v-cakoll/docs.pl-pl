---
title: ServiceTimeoutsBehavior
ms.date: 03/30/2017
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
ms.openlocfilehash: 58e872f2b15776d65bccdcc47c353ce566cd9d2f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59972813"
---
# <a name="servicetimeoutsbehavior"></a><span data-ttu-id="e6cc6-102">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="e6cc6-102">ServiceTimeoutsBehavior</span></span>
<span data-ttu-id="e6cc6-103">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="e6cc6-103">ServiceTimeoutsBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6cc6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6cc6-104">Syntax</span></span>  
  
```csharp
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e6cc6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e6cc6-105">Methods</span></span>  
 <span data-ttu-id="e6cc6-106">Klasa ServiceTimeoutsBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="e6cc6-106">The ServiceTimeoutsBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e6cc6-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e6cc6-107">Properties</span></span>  
 <span data-ttu-id="e6cc6-108">Klasa ServiceTimeoutsBehavior ma następującą właściwość:</span><span class="sxs-lookup"><span data-stu-id="e6cc6-108">The ServiceTimeoutsBehavior class has the following property:</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="e6cc6-109">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="e6cc6-109">TransactionTimeout</span></span>  
 <span data-ttu-id="e6cc6-110">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="e6cc6-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="e6cc6-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e6cc6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e6cc6-112">Okres, w którym należy wykonać transakcję.</span><span class="sxs-lookup"><span data-stu-id="e6cc6-112">The period within which a transaction must complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6cc6-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e6cc6-113">Requirements</span></span>  
  
|<span data-ttu-id="e6cc6-114">MOF</span><span class="sxs-lookup"><span data-stu-id="e6cc6-114">MOF</span></span>|<span data-ttu-id="e6cc6-115">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e6cc6-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e6cc6-116">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="e6cc6-116">Namespace</span></span>|<span data-ttu-id="e6cc6-117">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e6cc6-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6cc6-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6cc6-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
