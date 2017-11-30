---
title: ServiceAppDomain
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 36048f56c3b54447a112e6f0a457624062ce965a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="serviceappdomain"></a><span data-ttu-id="b1d7e-102">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="b1d7e-102">ServiceAppDomain</span></span>
<span data-ttu-id="b1d7e-103">Mapuje usługi domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b1d7e-103">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1d7e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1d7e-104">Syntax</span></span>  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b1d7e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b1d7e-105">Methods</span></span>  
 <span data-ttu-id="b1d7e-106">Klasa ServiceAppDomain nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="b1d7e-106">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b1d7e-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b1d7e-107">Properties</span></span>  
 <span data-ttu-id="b1d7e-108">Klasa ServiceAppDomain ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="b1d7e-108">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="b1d7e-109">ref</span><span class="sxs-lookup"><span data-stu-id="b1d7e-109">ref</span></span>  
 <span data-ttu-id="b1d7e-110">Typ danych: usługi</span><span class="sxs-lookup"><span data-stu-id="b1d7e-110">Data type: Service</span></span>  
<span data-ttu-id="b1d7e-111">Kwalifikatory: klucz</span><span class="sxs-lookup"><span data-stu-id="b1d7e-111">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="b1d7e-112">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b1d7e-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b1d7e-113">Usługa tej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b1d7e-113">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="b1d7e-114">ref</span><span class="sxs-lookup"><span data-stu-id="b1d7e-114">ref</span></span>  
 <span data-ttu-id="b1d7e-115">Typ danych: AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="b1d7e-115">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="b1d7e-116">Kwalifikatory: klucz</span><span class="sxs-lookup"><span data-stu-id="b1d7e-116">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="b1d7e-117">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b1d7e-117">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b1d7e-118">Zawiera właściwości domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b1d7e-118">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1d7e-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1d7e-119">Requirements</span></span>  
  
|<span data-ttu-id="b1d7e-120">MOF</span><span class="sxs-lookup"><span data-stu-id="b1d7e-120">MOF</span></span>|<span data-ttu-id="b1d7e-121">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b1d7e-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b1d7e-122">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="b1d7e-122">Namespace</span></span>|<span data-ttu-id="b1d7e-123">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b1d7e-123">Defined in root\ServiceModel</span></span>|
