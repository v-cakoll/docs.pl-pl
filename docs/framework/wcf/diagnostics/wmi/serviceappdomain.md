---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: aef0a0da9d107b92d9d3017968d5554205a6fd71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485671"
---
# <a name="serviceappdomain"></a><span data-ttu-id="e1387-102">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="e1387-102">ServiceAppDomain</span></span>
<span data-ttu-id="e1387-103">Mapuje usługi domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1387-103">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1387-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1387-104">Syntax</span></span>  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e1387-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e1387-105">Methods</span></span>  
 <span data-ttu-id="e1387-106">Klasa ServiceAppDomain nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="e1387-106">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e1387-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e1387-107">Properties</span></span>  
 <span data-ttu-id="e1387-108">Klasa ServiceAppDomain ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="e1387-108">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="e1387-109">ref</span><span class="sxs-lookup"><span data-stu-id="e1387-109">ref</span></span>  
 <span data-ttu-id="e1387-110">Typ danych: usługi</span><span class="sxs-lookup"><span data-stu-id="e1387-110">Data type: Service</span></span>  
<span data-ttu-id="e1387-111">Kwalifikatory: klucz</span><span class="sxs-lookup"><span data-stu-id="e1387-111">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="e1387-112">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e1387-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e1387-113">Usługa tej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1387-113">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="e1387-114">ref</span><span class="sxs-lookup"><span data-stu-id="e1387-114">ref</span></span>  
 <span data-ttu-id="e1387-115">Typ danych: AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="e1387-115">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="e1387-116">Kwalifikatory: klucz</span><span class="sxs-lookup"><span data-stu-id="e1387-116">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="e1387-117">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e1387-117">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e1387-118">Zawiera właściwości domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1387-118">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1387-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e1387-119">Requirements</span></span>  
  
|<span data-ttu-id="e1387-120">MOF</span><span class="sxs-lookup"><span data-stu-id="e1387-120">MOF</span></span>|<span data-ttu-id="e1387-121">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e1387-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e1387-122">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="e1387-122">Namespace</span></span>|<span data-ttu-id="e1387-123">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e1387-123">Defined in root\ServiceModel</span></span>|
