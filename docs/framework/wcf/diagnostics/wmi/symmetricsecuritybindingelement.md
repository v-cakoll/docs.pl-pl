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
ms.openlocfilehash: ab341f55947bfcfbc776143e3bbc33e125da89c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="ededa-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ededa-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="ededa-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ededa-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ededa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ededa-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ededa-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ededa-105">Methods</span></span>  
 <span data-ttu-id="ededa-106">Klasa element SymmetricSecurityBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="ededa-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ededa-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ededa-107">Properties</span></span>  
 <span data-ttu-id="ededa-108">Klasa SymmetricSecurityBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="ededa-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="ededa-109">messageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="ededa-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="ededa-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="ededa-110">Data type: string</span></span>  
  
 <span data-ttu-id="ededa-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ededa-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ededa-112">Kolejność szyfrowania i podpisywania dla tego powiązania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="ededa-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="ededa-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="ededa-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="ededa-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="ededa-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="ededa-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ededa-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ededa-116">Określa, czy powiązanie wymaga potwierdzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="ededa-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ededa-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ededa-117">Requirements</span></span>  
  
|<span data-ttu-id="ededa-118">MOF</span><span class="sxs-lookup"><span data-stu-id="ededa-118">MOF</span></span>|<span data-ttu-id="ededa-119">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ededa-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ededa-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="ededa-120">Namespace</span></span>|<span data-ttu-id="ededa-121">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ededa-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ededa-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ededa-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
