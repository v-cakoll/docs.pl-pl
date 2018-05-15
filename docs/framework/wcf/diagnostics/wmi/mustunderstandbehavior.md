---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 14150a992130e9ed4734c950d4ed92f1bbd3206c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="da102-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="da102-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="da102-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="da102-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da102-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="da102-104">Syntax</span></span>  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="da102-105">Metody</span><span class="sxs-lookup"><span data-stu-id="da102-105">Methods</span></span>  
 <span data-ttu-id="da102-106">Klasa MustUnderstandBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="da102-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="da102-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="da102-107">Properties</span></span>  
 <span data-ttu-id="da102-108">Klasa MustUnderstandBehavior ma następującą właściwość:</span><span class="sxs-lookup"><span data-stu-id="da102-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="da102-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="da102-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="da102-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="da102-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="da102-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="da102-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="da102-112">Gdy `true`, wszystkie nagłówki SOAP z `MustUnderstand` atrybutów, które nie są obsługiwane spowodować zgłoszenie wyjątku zachowania.</span><span class="sxs-lookup"><span data-stu-id="da102-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da102-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="da102-113">Requirements</span></span>  
  
|<span data-ttu-id="da102-114">MOF</span><span class="sxs-lookup"><span data-stu-id="da102-114">MOF</span></span>|<span data-ttu-id="da102-115">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="da102-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="da102-116">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="da102-116">Namespace</span></span>|<span data-ttu-id="da102-117">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="da102-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="da102-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da102-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>
