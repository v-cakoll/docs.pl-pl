---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
author: BrucePerlerMS
ms.openlocfilehash: 180b64f6f37e5c765585e52b292319816618be28
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47076525"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="88334-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="88334-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="88334-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="88334-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88334-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="88334-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="88334-105">Metody</span><span class="sxs-lookup"><span data-stu-id="88334-105">Methods</span></span>  
 <span data-ttu-id="88334-106">Klasa element SymmetricSecurityBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="88334-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="88334-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="88334-107">Properties</span></span>  
 <span data-ttu-id="88334-108">Klasa element SymmetricSecurityBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="88334-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="88334-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="88334-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="88334-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="88334-110">Data type: string</span></span>  
  
 <span data-ttu-id="88334-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="88334-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="88334-112">Kolejność komunikatów szyfrowania i podpisywania dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="88334-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="88334-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="88334-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="88334-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="88334-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="88334-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="88334-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="88334-116">Czy wiązanie wymaga potwierdzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="88334-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88334-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="88334-117">Requirements</span></span>  
  
|<span data-ttu-id="88334-118">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="88334-118">MOF</span></span>|<span data-ttu-id="88334-119">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="88334-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="88334-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="88334-120">Namespace</span></span>|<span data-ttu-id="88334-121">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="88334-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88334-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88334-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
