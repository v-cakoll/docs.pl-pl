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
ms.openlocfilehash: e17f88cf7f0d8572e65d00d8500a1fd83aa44eeb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663917"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="9fdaa-102">ESymbolReadingPolicy — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9fdaa-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="9fdaa-103">Zawiera wartości, które ustawić zasady do odczytywania plików bazy danych (PDB) programu.</span><span class="sxs-lookup"><span data-stu-id="9fdaa-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fdaa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9fdaa-104">Syntax</span></span>  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="9fdaa-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9fdaa-105">Members</span></span>  
  
|<span data-ttu-id="9fdaa-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="9fdaa-106">Member</span></span>|<span data-ttu-id="9fdaa-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9fdaa-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="9fdaa-108">Określa, że debuger zawsze powinni przeczytać pliki PDB.</span><span class="sxs-lookup"><span data-stu-id="9fdaa-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="9fdaa-109">Określa, czy debuger powinien pliki tylko do odczytu pliku PDB, które są skojarzone z zestawów pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="9fdaa-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="9fdaa-110">Określa, że debuger nigdy nie powinni przeczytać pliki PDB.</span><span class="sxs-lookup"><span data-stu-id="9fdaa-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fdaa-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9fdaa-111">Remarks</span></span>  
 <span data-ttu-id="9fdaa-112">`ESymbolReadingPolicy` Wyliczenie jest używane z [iclrdebugmanager::setsymbolreadingpolicy —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="9fdaa-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fdaa-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9fdaa-113">Requirements</span></span>  
 <span data-ttu-id="9fdaa-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fdaa-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fdaa-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9fdaa-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9fdaa-116">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9fdaa-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9fdaa-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fdaa-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fdaa-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9fdaa-118">See also</span></span>
- [<span data-ttu-id="9fdaa-119">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9fdaa-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
