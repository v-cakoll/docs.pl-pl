---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 09bfaa3ab4f2aceb3e80644953a87686fca9830c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="fdb62-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="fdb62-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="fdb62-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="fdb62-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdb62-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fdb62-104">Syntax</span></span>  
  
```  
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="fdb62-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fdb62-105">Methods</span></span>  
 <span data-ttu-id="fdb62-106">Klasa element AsymmetricSecurityBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="fdb62-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fdb62-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="fdb62-107">Properties</span></span>  
 <span data-ttu-id="fdb62-108">Element AsymmetricSecurityBindingElement klasa ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="fdb62-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="fdb62-109">messageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="fdb62-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="fdb62-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fdb62-110">Data type: string</span></span>  
  
 <span data-ttu-id="fdb62-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fdb62-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fdb62-112">Kolejność szyfrowania i podpisywania dla tego powiązania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="fdb62-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="fdb62-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="fdb62-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="fdb62-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fdb62-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="fdb62-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fdb62-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fdb62-116">Określa, czy powiązanie wymaga potwierdzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="fdb62-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdb62-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fdb62-117">Requirements</span></span>  
  
|<span data-ttu-id="fdb62-118">MOF</span><span class="sxs-lookup"><span data-stu-id="fdb62-118">MOF</span></span>|<span data-ttu-id="fdb62-119">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="fdb62-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fdb62-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="fdb62-120">Namespace</span></span>|<span data-ttu-id="fdb62-121">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fdb62-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fdb62-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fdb62-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
