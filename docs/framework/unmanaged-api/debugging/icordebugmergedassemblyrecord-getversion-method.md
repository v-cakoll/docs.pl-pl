---
title: ICorDebugMergedAssemblyRecord::GetVersion — metoda
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb206d1bf39307852dd317613eb81028b777514d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414602"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="09ff7-102">ICorDebugMergedAssemblyRecord::GetVersion — metoda</span><span class="sxs-lookup"><span data-stu-id="09ff7-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="09ff7-103">Pobiera informacje o wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="09ff7-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09ff7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="09ff7-104">Syntax</span></span>  
  
```  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09ff7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09ff7-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="09ff7-106">[out] Wskaźnik do głównego numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="09ff7-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="09ff7-107">[out] Wskaźnik do podrzędny numer wersji.</span><span class="sxs-lookup"><span data-stu-id="09ff7-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="09ff7-108">[out] Wskaźnik do numeru kompilacji.</span><span class="sxs-lookup"><span data-stu-id="09ff7-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="09ff7-109">[out] Wskaźnik do numer wersji.</span><span class="sxs-lookup"><span data-stu-id="09ff7-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09ff7-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09ff7-110">Remarks</span></span>  
 <span data-ttu-id="09ff7-111">Aby uzyskać informacje na numery wersji zestawu, zobacz <xref:System.Version> klasy tematu.</span><span class="sxs-lookup"><span data-stu-id="09ff7-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09ff7-112">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="09ff7-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09ff7-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09ff7-113">Requirements</span></span>  
 <span data-ttu-id="09ff7-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09ff7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09ff7-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09ff7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09ff7-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09ff7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09ff7-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09ff7-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ff7-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09ff7-118">See Also</span></span>  
 [<span data-ttu-id="09ff7-119">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="09ff7-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="09ff7-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="09ff7-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
