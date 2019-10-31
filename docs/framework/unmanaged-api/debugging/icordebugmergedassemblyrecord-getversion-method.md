---
title: 'ICorDebugMergedAssemblyRecord:: GetVersion — Metoda'
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 0c89d0749281da412bbf71400d51bee1ed651fbe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129767"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="c245d-102">ICorDebugMergedAssemblyRecord:: GetVersion — Metoda</span><span class="sxs-lookup"><span data-stu-id="c245d-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="c245d-103">Pobiera informacje o wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="c245d-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c245d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c245d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c245d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c245d-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="c245d-106">określoną Wskaźnik do głównego numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="c245d-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="c245d-107">określoną Wskaźnik do pomocniczego numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="c245d-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="c245d-108">określoną Wskaźnik do numeru kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c245d-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="c245d-109">określoną Wskaźnik do numeru poprawki.</span><span class="sxs-lookup"><span data-stu-id="c245d-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c245d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c245d-110">Remarks</span></span>  
 <span data-ttu-id="c245d-111">Informacje o numerach wersji zestawu znajdują się w temacie <xref:System.Version> Class.</span><span class="sxs-lookup"><span data-stu-id="c245d-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c245d-112">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c245d-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c245d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c245d-113">Requirements</span></span>  
 <span data-ttu-id="c245d-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c245d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c245d-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c245d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c245d-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c245d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c245d-117">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c245d-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c245d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c245d-118">See also</span></span>

- [<span data-ttu-id="c245d-119">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="c245d-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="c245d-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c245d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
