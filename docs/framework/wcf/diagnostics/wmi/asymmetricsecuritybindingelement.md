---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 0f86fc1b410753b5ec100f0a7d43de9badd1401b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196050"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="6ded3-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="6ded3-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="6ded3-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="6ded3-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ded3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ded3-104">Syntax</span></span>  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6ded3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6ded3-105">Methods</span></span>  
 <span data-ttu-id="6ded3-106">Klasa element AsymmetricSecurityBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="6ded3-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6ded3-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="6ded3-107">Properties</span></span>  
 <span data-ttu-id="6ded3-108">Klasa element AsymmetricSecurityBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="6ded3-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="6ded3-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="6ded3-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="6ded3-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="6ded3-110">Data type: string</span></span>  
  
 <span data-ttu-id="6ded3-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6ded3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6ded3-112">Kolejność komunikatów szyfrowania i podpisywania dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="6ded3-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="6ded3-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="6ded3-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="6ded3-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="6ded3-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="6ded3-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6ded3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6ded3-116">Czy wiązanie wymaga potwierdzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="6ded3-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ded3-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ded3-117">Requirements</span></span>  
  
|<span data-ttu-id="6ded3-118">MOF</span><span class="sxs-lookup"><span data-stu-id="6ded3-118">MOF</span></span>|<span data-ttu-id="6ded3-119">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6ded3-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6ded3-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="6ded3-120">Namespace</span></span>|<span data-ttu-id="6ded3-121">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6ded3-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6ded3-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ded3-122">See also</span></span>

- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
