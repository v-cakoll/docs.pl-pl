---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 7e6a96c217b038e870b4e865315766afa3b3c757
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963166"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="5d2b1-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="5d2b1-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="5d2b1-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="5d2b1-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d2b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d2b1-104">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5d2b1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5d2b1-105">Methods</span></span>  
 <span data-ttu-id="5d2b1-106">Klasa MustUnderstandBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="5d2b1-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5d2b1-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5d2b1-107">Properties</span></span>  
 <span data-ttu-id="5d2b1-108">Klasa MustUnderstandBehavior ma następującą właściwość:</span><span class="sxs-lookup"><span data-stu-id="5d2b1-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="5d2b1-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="5d2b1-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="5d2b1-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="5d2b1-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="5d2b1-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5d2b1-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d2b1-112">Gdy `true`, wszystkich nagłówków protokołu SOAP z `MustUnderstand` atrybutów, które nie są obsługiwane, że zachowanie, aby zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="5d2b1-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d2b1-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d2b1-113">Requirements</span></span>  
  
|<span data-ttu-id="5d2b1-114">MOF</span><span class="sxs-lookup"><span data-stu-id="5d2b1-114">MOF</span></span>|<span data-ttu-id="5d2b1-115">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5d2b1-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5d2b1-116">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="5d2b1-116">Namespace</span></span>|<span data-ttu-id="5d2b1-117">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5d2b1-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d2b1-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d2b1-118">See also</span></span>

- <xref:System.ServiceModel.Description.MustUnderstandBehavior>
