---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
author: BrucePerlerMS
ms.openlocfilehash: 63af1c9a607cb9f81e2c0abf795ee2b3432cbf9c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075060"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="f3504-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="f3504-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="f3504-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="f3504-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3504-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3504-104">Syntax</span></span>  
  
```  
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f3504-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f3504-105">Methods</span></span>  
 <span data-ttu-id="f3504-106">Klasa element AsymmetricSecurityBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="f3504-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f3504-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f3504-107">Properties</span></span>  
 <span data-ttu-id="f3504-108">Klasa element AsymmetricSecurityBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="f3504-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="f3504-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="f3504-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="f3504-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="f3504-110">Data type: string</span></span>  
  
 <span data-ttu-id="f3504-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f3504-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f3504-112">Kolejność komunikatów szyfrowania i podpisywania dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f3504-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="f3504-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="f3504-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="f3504-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="f3504-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="f3504-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f3504-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f3504-116">Czy wiązanie wymaga potwierdzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="f3504-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3504-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f3504-117">Requirements</span></span>  
  
|<span data-ttu-id="f3504-118">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="f3504-118">MOF</span></span>|<span data-ttu-id="f3504-119">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f3504-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f3504-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="f3504-120">Namespace</span></span>|<span data-ttu-id="f3504-121">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f3504-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3504-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3504-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
