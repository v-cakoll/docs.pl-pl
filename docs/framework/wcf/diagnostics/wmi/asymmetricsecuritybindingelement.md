---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: e968f5f2d7ffdb193b30762d32a47be3778b98dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621360"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="3e7db-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="3e7db-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="3e7db-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="3e7db-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e7db-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e7db-104">Syntax</span></span>  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3e7db-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3e7db-105">Methods</span></span>  
 <span data-ttu-id="3e7db-106">Klasa element AsymmetricSecurityBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="3e7db-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3e7db-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3e7db-107">Properties</span></span>  
 <span data-ttu-id="3e7db-108">Klasa element AsymmetricSecurityBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="3e7db-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="3e7db-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="3e7db-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="3e7db-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="3e7db-110">Data type: string</span></span>  
  
 <span data-ttu-id="3e7db-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3e7db-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3e7db-112">Kolejność komunikatów szyfrowania i podpisywania dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="3e7db-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="3e7db-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="3e7db-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="3e7db-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="3e7db-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="3e7db-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3e7db-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3e7db-116">Czy wiązanie wymaga potwierdzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="3e7db-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e7db-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3e7db-117">Requirements</span></span>  
  
|<span data-ttu-id="3e7db-118">MOF</span><span class="sxs-lookup"><span data-stu-id="3e7db-118">MOF</span></span>|<span data-ttu-id="3e7db-119">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3e7db-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3e7db-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="3e7db-120">Namespace</span></span>|<span data-ttu-id="3e7db-121">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3e7db-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3e7db-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e7db-122">See also</span></span>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
