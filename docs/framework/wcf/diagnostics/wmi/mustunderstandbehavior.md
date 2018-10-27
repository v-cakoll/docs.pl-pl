---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 0f3efc446104a1afff507f6e7d2cd8c01c4ed417
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452602"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="f9786-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="f9786-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="f9786-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="f9786-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9786-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9786-104">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f9786-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f9786-105">Methods</span></span>  
 <span data-ttu-id="f9786-106">Klasa MustUnderstandBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="f9786-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f9786-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f9786-107">Properties</span></span>  
 <span data-ttu-id="f9786-108">Klasa MustUnderstandBehavior ma następującą właściwość:</span><span class="sxs-lookup"><span data-stu-id="f9786-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="f9786-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="f9786-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="f9786-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="f9786-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="f9786-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f9786-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f9786-112">Gdy `true`, wszystkich nagłówków protokołu SOAP z `MustUnderstand` atrybutów, które nie są obsługiwane, że zachowanie, aby zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f9786-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9786-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f9786-113">Requirements</span></span>  
  
|<span data-ttu-id="f9786-114">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="f9786-114">MOF</span></span>|<span data-ttu-id="f9786-115">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f9786-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f9786-116">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="f9786-116">Namespace</span></span>|<span data-ttu-id="f9786-117">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f9786-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9786-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9786-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>
