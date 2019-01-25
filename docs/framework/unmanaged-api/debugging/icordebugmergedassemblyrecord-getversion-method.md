---
title: Metoda ICorDebugMergedAssemblyRecord::GetVersion
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4895610ba3a8e8e8eb1a1c360ecb2b707f9cee4d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622094"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="da8e8-102">Metoda ICorDebugMergedAssemblyRecord::GetVersion</span><span class="sxs-lookup"><span data-stu-id="da8e8-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="da8e8-103">Pobiera informacje o wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="da8e8-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da8e8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="da8e8-104">Syntax</span></span>  
  
```  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da8e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da8e8-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="da8e8-106">[out] Wskaźnik do główny numer wersji.</span><span class="sxs-lookup"><span data-stu-id="da8e8-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="da8e8-107">[out] Wskaźnik do pomocniczy numer wersji.</span><span class="sxs-lookup"><span data-stu-id="da8e8-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="da8e8-108">[out] Wskaźnik do numeru kompilacji.</span><span class="sxs-lookup"><span data-stu-id="da8e8-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="da8e8-109">[out] Wskaźnik do numer poprawki.</span><span class="sxs-lookup"><span data-stu-id="da8e8-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da8e8-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="da8e8-110">Remarks</span></span>  
 <span data-ttu-id="da8e8-111">Aby uzyskać informacji o numerach wersji zestawu, zobacz <xref:System.Version> temat poświęcony klasie.</span><span class="sxs-lookup"><span data-stu-id="da8e8-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da8e8-112">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="da8e8-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da8e8-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="da8e8-113">Requirements</span></span>  
 <span data-ttu-id="da8e8-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da8e8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da8e8-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da8e8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da8e8-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da8e8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da8e8-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da8e8-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da8e8-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="da8e8-118">See also</span></span>
- [<span data-ttu-id="da8e8-119">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="da8e8-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="da8e8-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="da8e8-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
