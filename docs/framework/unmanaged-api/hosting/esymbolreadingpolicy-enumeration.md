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
ms.openlocfilehash: 5c3d1d0ebc56ee93c950afb4f015c8e10ec6a0f7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616180"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="ce828-102">ESymbolReadingPolicy — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ce828-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="ce828-103">Zawiera wartości, które ustawiają zasady odczytujące pliki bazy danych (PDB) programu.</span><span class="sxs-lookup"><span data-stu-id="ce828-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce828-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce828-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="ce828-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ce828-105">Members</span></span>  
  
|<span data-ttu-id="ce828-106">Członek</span><span class="sxs-lookup"><span data-stu-id="ce828-106">Member</span></span>|<span data-ttu-id="ce828-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ce828-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="ce828-108">Określa, że debuger powinien zawsze odczytywać pliki PDB.</span><span class="sxs-lookup"><span data-stu-id="ce828-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="ce828-109">Określa, że debuger powinien odczytać tylko pliki PDB, które są skojarzone z zestawami pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="ce828-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="ce828-110">Określa, że debuger nie powinien odczytywać plików PDB.</span><span class="sxs-lookup"><span data-stu-id="ce828-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce828-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ce828-111">Remarks</span></span>  
 <span data-ttu-id="ce828-112">`ESymbolReadingPolicy`Wyliczenie jest używane z metodą [ICLRDebugManager:: SetSymbolReadingPolicy —](iclrdebugmanager-setsymbolreadingpolicy-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ce828-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce828-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ce828-113">Requirements</span></span>  
 <span data-ttu-id="ce828-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce828-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce828-115">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ce828-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ce828-116">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ce828-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce828-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce828-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce828-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce828-118">See also</span></span>

- [<span data-ttu-id="ce828-119">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ce828-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
