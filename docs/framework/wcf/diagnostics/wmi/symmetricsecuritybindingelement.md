---
title: SymmetricSecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7960ae9972490f2363b0f6f9942e947677c7d299
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="b4f84-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="b4f84-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="b4f84-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="b4f84-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4f84-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4f84-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b4f84-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b4f84-105">Methods</span></span>  
 <span data-ttu-id="b4f84-106">Klasa element SymmetricSecurityBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="b4f84-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b4f84-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b4f84-107">Properties</span></span>  
 <span data-ttu-id="b4f84-108">Klasa SymmetricSecurityBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="b4f84-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="b4f84-109">messageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="b4f84-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="b4f84-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="b4f84-110">Data type: string</span></span>  
  
 <span data-ttu-id="b4f84-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b4f84-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4f84-112">Kolejność szyfrowania i podpisywania dla tego powiązania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b4f84-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="b4f84-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="b4f84-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="b4f84-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="b4f84-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="b4f84-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b4f84-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4f84-116">Określa, czy powiązanie wymaga potwierdzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="b4f84-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4f84-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4f84-117">Requirements</span></span>  
  
|<span data-ttu-id="b4f84-118">MOF</span><span class="sxs-lookup"><span data-stu-id="b4f84-118">MOF</span></span>|<span data-ttu-id="b4f84-119">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b4f84-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b4f84-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="b4f84-120">Namespace</span></span>|<span data-ttu-id="b4f84-121">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b4f84-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b4f84-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4f84-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
