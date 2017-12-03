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
ms.openlocfilehash: 40075acb2a098c98b4cd0ab35f213981c09f8486
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="65a7c-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="65a7c-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="65a7c-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="65a7c-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65a7c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65a7c-104">Syntax</span></span>  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="65a7c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="65a7c-105">Methods</span></span>  
 <span data-ttu-id="65a7c-106">Klasa MustUnderstandBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="65a7c-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="65a7c-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="65a7c-107">Properties</span></span>  
 <span data-ttu-id="65a7c-108">Klasa MustUnderstandBehavior ma następującą właściwość:</span><span class="sxs-lookup"><span data-stu-id="65a7c-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="65a7c-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="65a7c-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="65a7c-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="65a7c-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="65a7c-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="65a7c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65a7c-112">Gdy `true`, wszystkie nagłówki SOAP z `MustUnderstand` atrybutów, które nie są obsługiwane spowodować zgłoszenie wyjątku zachowania.</span><span class="sxs-lookup"><span data-stu-id="65a7c-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65a7c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65a7c-113">Requirements</span></span>  
  
|<span data-ttu-id="65a7c-114">MOF</span><span class="sxs-lookup"><span data-stu-id="65a7c-114">MOF</span></span>|<span data-ttu-id="65a7c-115">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="65a7c-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="65a7c-116">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="65a7c-116">Namespace</span></span>|<span data-ttu-id="65a7c-117">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="65a7c-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65a7c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65a7c-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>
