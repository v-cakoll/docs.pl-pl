---
title: ESymbolReadingPolicy — Wyliczenie
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28f6bdbc3e382f82b7fdd632b9fc8c4d422629c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429738"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="28bf5-102">ESymbolReadingPolicy — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="28bf5-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="28bf5-103">Zawiera wartości, które ustawić zasady do odczytywania plików programu (PDB) bazy danych.</span><span class="sxs-lookup"><span data-stu-id="28bf5-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28bf5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="28bf5-104">Syntax</span></span>  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="28bf5-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="28bf5-105">Members</span></span>  
  
|<span data-ttu-id="28bf5-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="28bf5-106">Member</span></span>|<span data-ttu-id="28bf5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="28bf5-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="28bf5-108">Określa, że debuger zawsze odczytywane pliki PDB.</span><span class="sxs-lookup"><span data-stu-id="28bf5-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="28bf5-109">Określa, czy debuger powinien przeczytać PDB tylko te pliki, które są skojarzone z zestawami pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="28bf5-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="28bf5-110">Określa, czy debuger powinien nigdy nie odczytu plików PDB.</span><span class="sxs-lookup"><span data-stu-id="28bf5-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28bf5-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28bf5-111">Remarks</span></span>  
 <span data-ttu-id="28bf5-112">`ESymbolReadingPolicy` Wyliczenie jest używany z [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="28bf5-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28bf5-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="28bf5-113">Requirements</span></span>  
 <span data-ttu-id="28bf5-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28bf5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28bf5-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="28bf5-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28bf5-116">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="28bf5-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28bf5-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28bf5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28bf5-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28bf5-118">See Also</span></span>  
 [<span data-ttu-id="28bf5-119">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="28bf5-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
