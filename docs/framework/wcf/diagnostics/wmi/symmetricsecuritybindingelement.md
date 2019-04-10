---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: f6effd533a205d0e8fd1421119e325f06b340dd1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206801"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="1f382-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="1f382-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="1f382-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="1f382-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f382-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f382-104">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1f382-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1f382-105">Methods</span></span>  
 <span data-ttu-id="1f382-106">Klasa element SymmetricSecurityBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="1f382-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1f382-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1f382-107">Properties</span></span>  
 <span data-ttu-id="1f382-108">Klasa element SymmetricSecurityBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="1f382-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="1f382-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="1f382-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="1f382-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="1f382-110">Data type: string</span></span>  
  
 <span data-ttu-id="1f382-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1f382-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f382-112">Kolejność komunikatów szyfrowania i podpisywania dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1f382-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="1f382-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="1f382-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="1f382-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="1f382-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="1f382-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1f382-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f382-116">Czy wiązanie wymaga potwierdzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="1f382-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f382-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f382-117">Requirements</span></span>  
  
|<span data-ttu-id="1f382-118">MOF</span><span class="sxs-lookup"><span data-stu-id="1f382-118">MOF</span></span>|<span data-ttu-id="1f382-119">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1f382-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1f382-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="1f382-120">Namespace</span></span>|<span data-ttu-id="1f382-121">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1f382-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f382-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f382-122">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
