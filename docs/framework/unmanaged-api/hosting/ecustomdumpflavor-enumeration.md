---
title: ECustomDumpFlavor — Wyliczenie
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2be9f112d5997ec8a6b126229eb8608eb8dd8520
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627645"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="ed743-102">ECustomDumpFlavor — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ed743-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="ed743-103">Zawiera wartości wskazujące, które elementów do uwzględnienia w niestandardowych podzbiór sterty zrzutu podczas zgłaszania błędów.</span><span class="sxs-lookup"><span data-stu-id="ed743-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed743-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed743-104">Syntax</span></span>  
  
```  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="ed743-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ed743-105">Members</span></span>  
  
|<span data-ttu-id="ed743-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ed743-106">Member</span></span>|<span data-ttu-id="ed743-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ed743-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="ed743-108">Określa, że zrzutu sterty niestandardowych należy uruchomić jako minizrzutu i obejmują dodatkowe dane określone przez dowolne [customdumpitem —](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) wystąpienia przekazane do tej samej metody.</span><span class="sxs-lookup"><span data-stu-id="ed743-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="ed743-109">Określa, że zrzut sterty niestandardowego należy zebrać wszystkie dane w stanie w czasie wykonywania, które nie został przydzielony dynamicznie.</span><span class="sxs-lookup"><span data-stu-id="ed743-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed743-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed743-110">Remarks</span></span>  
 <span data-ttu-id="ed743-111">Parametr typu `ECustomDumpFlavor` jest przekazywany do [iclrerrorreportingmanager::begincustomdump —](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ed743-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed743-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed743-112">Requirements</span></span>  
 <span data-ttu-id="ed743-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed743-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed743-114">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ed743-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed743-115">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ed743-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed743-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed743-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed743-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed743-117">See also</span></span>
- [<span data-ttu-id="ed743-118">ECustomDumpItemKind, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ed743-118">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="ed743-119">ICLRErrorReportingManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ed743-119">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="ed743-120">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ed743-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
