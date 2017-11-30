---
title: AsymmetricSecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 104810fc24cfe7c4c6ddf7ee5ece9f16a345c80c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="93fbd-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="93fbd-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="93fbd-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="93fbd-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93fbd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="93fbd-104">Syntax</span></span>  
  
```  
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="93fbd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="93fbd-105">Methods</span></span>  
 <span data-ttu-id="93fbd-106">Klasa element AsymmetricSecurityBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="93fbd-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="93fbd-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="93fbd-107">Properties</span></span>  
 <span data-ttu-id="93fbd-108">Element AsymmetricSecurityBindingElement klasa ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="93fbd-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="93fbd-109">messageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="93fbd-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="93fbd-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="93fbd-110">Data type: string</span></span>  
  
 <span data-ttu-id="93fbd-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="93fbd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93fbd-112">Kolejność szyfrowania i podpisywania dla tego powiązania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="93fbd-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="93fbd-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="93fbd-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="93fbd-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="93fbd-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="93fbd-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="93fbd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93fbd-116">Określa, czy powiązanie wymaga potwierdzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="93fbd-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93fbd-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93fbd-117">Requirements</span></span>  
  
|<span data-ttu-id="93fbd-118">MOF</span><span class="sxs-lookup"><span data-stu-id="93fbd-118">MOF</span></span>|<span data-ttu-id="93fbd-119">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="93fbd-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="93fbd-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="93fbd-120">Namespace</span></span>|<span data-ttu-id="93fbd-121">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="93fbd-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="93fbd-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93fbd-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
