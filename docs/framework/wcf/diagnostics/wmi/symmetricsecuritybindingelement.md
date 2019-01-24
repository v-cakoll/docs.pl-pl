---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: 7b979a6872da15c4130e580a3f7327802f42db18
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701394"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="d70d0-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d70d0-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="d70d0-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d70d0-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d70d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d70d0-104">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d70d0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d70d0-105">Methods</span></span>  
 <span data-ttu-id="d70d0-106">Klasa element SymmetricSecurityBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="d70d0-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d70d0-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d70d0-107">Properties</span></span>  
 <span data-ttu-id="d70d0-108">Klasa element SymmetricSecurityBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="d70d0-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="d70d0-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="d70d0-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="d70d0-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="d70d0-110">Data type: string</span></span>  
  
 <span data-ttu-id="d70d0-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d70d0-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d70d0-112">Kolejność komunikatów szyfrowania i podpisywania dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="d70d0-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="d70d0-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="d70d0-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="d70d0-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="d70d0-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="d70d0-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d70d0-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d70d0-116">Czy wiązanie wymaga potwierdzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="d70d0-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d70d0-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d70d0-117">Requirements</span></span>  
  
|<span data-ttu-id="d70d0-118">MOF</span><span class="sxs-lookup"><span data-stu-id="d70d0-118">MOF</span></span>|<span data-ttu-id="d70d0-119">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d70d0-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d70d0-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="d70d0-120">Namespace</span></span>|<span data-ttu-id="d70d0-121">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d70d0-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d70d0-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d70d0-122">See also</span></span>
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
