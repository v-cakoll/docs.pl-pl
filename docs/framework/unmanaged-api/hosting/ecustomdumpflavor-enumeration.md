---
title: "ECustomDumpFlavor — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ECustomDumpFlavor
api_location: mscoree.dll
api_type: COM
f1_keywords: ECustomDumpFlavor
helpviewer_keywords: ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a7317a3a12acef2a16deebab9a1e1b10205ebf6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="cfad1-102">ECustomDumpFlavor — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="cfad1-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="cfad1-103">Zawiera wartości, które wskazują pozycje, które chcesz uwzględnić w niestandardowych podzbiór sterty zrzutu podczas raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="cfad1-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfad1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cfad1-104">Syntax</span></span>  
  
```  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="cfad1-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="cfad1-105">Members</span></span>  
  
|<span data-ttu-id="cfad1-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="cfad1-106">Member</span></span>|<span data-ttu-id="cfad1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="cfad1-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="cfad1-108">Określa, że zrzutu niestandardowych sterty należy uruchomić jako minizrzutu i obejmują dodatkowe dane określonym przez [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) wystąpienia przekazane do tej samej metody.</span><span class="sxs-lookup"><span data-stu-id="cfad1-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="cfad1-109">Określa, że zrzut niestandardowych sterty należy zebrać wszystkie dane stanu czasu wykonywania, które nie zostało przydzielone dynamicznie.</span><span class="sxs-lookup"><span data-stu-id="cfad1-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfad1-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cfad1-110">Remarks</span></span>  
 <span data-ttu-id="cfad1-111">Parametr typu `ECustomDumpFlavor` jest przekazywana do [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="cfad1-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfad1-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cfad1-112">Requirements</span></span>  
 <span data-ttu-id="cfad1-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfad1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfad1-114">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cfad1-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cfad1-115">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cfad1-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cfad1-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfad1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfad1-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cfad1-117">See Also</span></span>  
 [<span data-ttu-id="cfad1-118">ECustomDumpItemKind — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="cfad1-118">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [<span data-ttu-id="cfad1-119">ICLRErrorReportingManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="cfad1-119">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="cfad1-120">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="cfad1-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
