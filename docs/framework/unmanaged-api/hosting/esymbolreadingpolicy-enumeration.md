---
title: "ESymbolReadingPolicy — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ESymbolReadingPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ESymbolReadingPolicy
helpviewer_keywords: ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ce56486453e88a18ebd9dbb42f30bcfdafcf328e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="cb690-102">ESymbolReadingPolicy — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="cb690-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="cb690-103">Zawiera wartości, które ustawić zasady do odczytywania plików programu (PDB) bazy danych.</span><span class="sxs-lookup"><span data-stu-id="cb690-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb690-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb690-104">Syntax</span></span>  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="cb690-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="cb690-105">Members</span></span>  
  
|<span data-ttu-id="cb690-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="cb690-106">Member</span></span>|<span data-ttu-id="cb690-107">Opis</span><span class="sxs-lookup"><span data-stu-id="cb690-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="cb690-108">Określa, że debuger zawsze odczytywane pliki PDB.</span><span class="sxs-lookup"><span data-stu-id="cb690-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="cb690-109">Określa, czy debuger powinien przeczytać PDB tylko te pliki, które są skojarzone z zestawami pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="cb690-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="cb690-110">Określa, czy debuger powinien nigdy nie odczytu plików PDB.</span><span class="sxs-lookup"><span data-stu-id="cb690-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb690-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb690-111">Remarks</span></span>  
 <span data-ttu-id="cb690-112">`ESymbolReadingPolicy` Wyliczenie jest używany z [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="cb690-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb690-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb690-113">Requirements</span></span>  
 <span data-ttu-id="cb690-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb690-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb690-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cb690-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb690-116">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb690-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb690-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb690-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb690-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb690-118">See Also</span></span>  
 [<span data-ttu-id="cb690-119">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="cb690-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
