---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: f6effd533a205d0e8fd1421119e325f06b340dd1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770415"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="afac5-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="afac5-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="afac5-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="afac5-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afac5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="afac5-104">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="afac5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="afac5-105">Methods</span></span>  
 <span data-ttu-id="afac5-106">Klasa element SymmetricSecurityBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="afac5-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="afac5-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="afac5-107">Properties</span></span>  
 <span data-ttu-id="afac5-108">Klasa element SymmetricSecurityBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="afac5-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="afac5-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="afac5-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="afac5-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="afac5-110">Data type: string</span></span>  
  
 <span data-ttu-id="afac5-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="afac5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afac5-112">Kolejność komunikatów szyfrowania i podpisywania dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="afac5-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="afac5-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="afac5-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="afac5-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="afac5-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="afac5-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="afac5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afac5-116">Czy wiązanie wymaga potwierdzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="afac5-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afac5-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="afac5-117">Requirements</span></span>  
  
|<span data-ttu-id="afac5-118">MOF</span><span class="sxs-lookup"><span data-stu-id="afac5-118">MOF</span></span>|<span data-ttu-id="afac5-119">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="afac5-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="afac5-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="afac5-120">Namespace</span></span>|<span data-ttu-id="afac5-121">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="afac5-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="afac5-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="afac5-122">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
