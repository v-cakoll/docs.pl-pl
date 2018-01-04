---
title: MustUnderstandBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b6838c6ce98e0d373a45c136b12bdedbd8c9eb6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="073b8-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="073b8-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="073b8-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="073b8-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="073b8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="073b8-104">Syntax</span></span>  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="073b8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="073b8-105">Methods</span></span>  
 <span data-ttu-id="073b8-106">Klasa MustUnderstandBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="073b8-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="073b8-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="073b8-107">Properties</span></span>  
 <span data-ttu-id="073b8-108">Klasa MustUnderstandBehavior ma następującą właściwość:</span><span class="sxs-lookup"><span data-stu-id="073b8-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="073b8-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="073b8-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="073b8-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="073b8-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="073b8-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="073b8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="073b8-112">Gdy `true`, wszystkie nagłówki SOAP z `MustUnderstand` atrybutów, które nie są obsługiwane spowodować zgłoszenie wyjątku zachowania.</span><span class="sxs-lookup"><span data-stu-id="073b8-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="073b8-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="073b8-113">Requirements</span></span>  
  
|<span data-ttu-id="073b8-114">MOF</span><span class="sxs-lookup"><span data-stu-id="073b8-114">MOF</span></span>|<span data-ttu-id="073b8-115">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="073b8-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="073b8-116">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="073b8-116">Namespace</span></span>|<span data-ttu-id="073b8-117">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="073b8-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="073b8-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="073b8-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>
