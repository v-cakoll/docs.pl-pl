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
ms.openlocfilehash: 9ba29952fe4a6edfc6e9e80ec02f82de65ef0064
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61628603"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="1fa5c-102">ESymbolReadingPolicy — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1fa5c-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="1fa5c-103">Zawiera wartości, które ustawić zasady do odczytywania plików bazy danych (PDB) programu.</span><span class="sxs-lookup"><span data-stu-id="1fa5c-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fa5c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1fa5c-104">Syntax</span></span>  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="1fa5c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1fa5c-105">Members</span></span>  
  
|<span data-ttu-id="1fa5c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="1fa5c-106">Member</span></span>|<span data-ttu-id="1fa5c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1fa5c-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="1fa5c-108">Określa, że debuger zawsze powinni przeczytać pliki PDB.</span><span class="sxs-lookup"><span data-stu-id="1fa5c-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="1fa5c-109">Określa, czy debuger powinien pliki tylko do odczytu pliku PDB, które są skojarzone z zestawów pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="1fa5c-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="1fa5c-110">Określa, że debuger nigdy nie powinni przeczytać pliki PDB.</span><span class="sxs-lookup"><span data-stu-id="1fa5c-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fa5c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1fa5c-111">Remarks</span></span>  
 <span data-ttu-id="1fa5c-112">`ESymbolReadingPolicy` Wyliczenie jest używane z [iclrdebugmanager::setsymbolreadingpolicy —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="1fa5c-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fa5c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1fa5c-113">Requirements</span></span>  
 <span data-ttu-id="1fa5c-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fa5c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fa5c-115">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1fa5c-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1fa5c-116">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1fa5c-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1fa5c-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fa5c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fa5c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1fa5c-118">See also</span></span>

- [<span data-ttu-id="1fa5c-119">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="1fa5c-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
