---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: 05be495dbfe87e7dd14b0cfbb38b30c6f8278e6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61957076"
---
# <a name="serviceappdomain"></a><span data-ttu-id="32285-102">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="32285-102">ServiceAppDomain</span></span>
<span data-ttu-id="32285-103">Mapuje domenę aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="32285-103">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32285-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32285-104">Syntax</span></span>  
  
```csharp
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="32285-105">Metody</span><span class="sxs-lookup"><span data-stu-id="32285-105">Methods</span></span>  
 <span data-ttu-id="32285-106">Klasa ServiceAppDomain nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="32285-106">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="32285-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="32285-107">Properties</span></span>  
 <span data-ttu-id="32285-108">Klasa ServiceAppDomain ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="32285-108">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="32285-109">ref</span><span class="sxs-lookup"><span data-stu-id="32285-109">ref</span></span>  
 <span data-ttu-id="32285-110">Typ danych: Usługa</span><span class="sxs-lookup"><span data-stu-id="32285-110">Data type: Service</span></span>  
<span data-ttu-id="32285-111">Kwalifikatory: Key</span><span class="sxs-lookup"><span data-stu-id="32285-111">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="32285-112">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="32285-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32285-113">Usługa ta domena aplikacji.</span><span class="sxs-lookup"><span data-stu-id="32285-113">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="32285-114">ref</span><span class="sxs-lookup"><span data-stu-id="32285-114">ref</span></span>  
 <span data-ttu-id="32285-115">Typ danych: AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="32285-115">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="32285-116">Kwalifikatory: Key</span><span class="sxs-lookup"><span data-stu-id="32285-116">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="32285-117">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="32285-117">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32285-118">Zawiera właściwości domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="32285-118">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32285-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32285-119">Requirements</span></span>  
  
|<span data-ttu-id="32285-120">MOF</span><span class="sxs-lookup"><span data-stu-id="32285-120">MOF</span></span>|<span data-ttu-id="32285-121">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="32285-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="32285-122">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="32285-122">Namespace</span></span>|<span data-ttu-id="32285-123">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="32285-123">Defined in root\ServiceModel</span></span>|
