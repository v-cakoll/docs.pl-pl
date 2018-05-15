---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7fc720f4f0be25a0cec25d979942af8472efa4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="bbf94-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="bbf94-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="bbf94-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="bbf94-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbf94-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bbf94-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="bbf94-105">Metody</span><span class="sxs-lookup"><span data-stu-id="bbf94-105">Methods</span></span>  
 <span data-ttu-id="bbf94-106">Klasa element SymmetricSecurityBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="bbf94-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bbf94-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="bbf94-107">Properties</span></span>  
 <span data-ttu-id="bbf94-108">Klasa SymmetricSecurityBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="bbf94-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="bbf94-109">messageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="bbf94-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="bbf94-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="bbf94-110">Data type: string</span></span>  
  
 <span data-ttu-id="bbf94-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="bbf94-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bbf94-112">Kolejność szyfrowania i podpisywania dla tego powiązania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="bbf94-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="bbf94-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="bbf94-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="bbf94-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="bbf94-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="bbf94-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="bbf94-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bbf94-116">Określa, czy powiązanie wymaga potwierdzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="bbf94-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbf94-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bbf94-117">Requirements</span></span>  
  
|<span data-ttu-id="bbf94-118">MOF</span><span class="sxs-lookup"><span data-stu-id="bbf94-118">MOF</span></span>|<span data-ttu-id="bbf94-119">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="bbf94-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="bbf94-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="bbf94-120">Namespace</span></span>|<span data-ttu-id="bbf94-121">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="bbf94-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bbf94-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bbf94-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
