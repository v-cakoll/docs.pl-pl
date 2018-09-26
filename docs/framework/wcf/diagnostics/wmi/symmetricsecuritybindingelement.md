---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
author: BrucePerlerMS
ms.openlocfilehash: 180b64f6f37e5c765585e52b292319816618be28
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198855"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="b787c-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="b787c-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="b787c-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="b787c-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b787c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b787c-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b787c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b787c-105">Methods</span></span>  
 <span data-ttu-id="b787c-106">Klasa element SymmetricSecurityBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="b787c-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b787c-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b787c-107">Properties</span></span>  
 <span data-ttu-id="b787c-108">Klasa element SymmetricSecurityBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="b787c-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="b787c-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="b787c-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="b787c-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="b787c-110">Data type: string</span></span>  
  
 <span data-ttu-id="b787c-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b787c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b787c-112">Kolejność komunikatów szyfrowania i podpisywania dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b787c-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="b787c-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="b787c-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="b787c-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="b787c-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="b787c-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b787c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b787c-116">Czy wiązanie wymaga potwierdzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="b787c-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b787c-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b787c-117">Requirements</span></span>  
  
|<span data-ttu-id="b787c-118">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="b787c-118">MOF</span></span>|<span data-ttu-id="b787c-119">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b787c-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b787c-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="b787c-120">Namespace</span></span>|<span data-ttu-id="b787c-121">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b787c-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b787c-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b787c-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
