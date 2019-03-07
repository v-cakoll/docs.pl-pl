---
title: Metoda ICorDebugMergedAssemblyRecord::GetVersion
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 762ac20c376f4161aa9c053f6e5213ba24c792ba
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499780"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="cad51-102">Metoda ICorDebugMergedAssemblyRecord::GetVersion</span><span class="sxs-lookup"><span data-stu-id="cad51-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="cad51-103">Pobiera informacje o wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="cad51-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cad51-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cad51-104">Syntax</span></span>  
  
```  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cad51-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cad51-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="cad51-106">[out] Wskaźnik do główny numer wersji.</span><span class="sxs-lookup"><span data-stu-id="cad51-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="cad51-107">[out] Wskaźnik do pomocniczy numer wersji.</span><span class="sxs-lookup"><span data-stu-id="cad51-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="cad51-108">[out] Wskaźnik do numeru kompilacji.</span><span class="sxs-lookup"><span data-stu-id="cad51-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="cad51-109">[out] Wskaźnik do numer poprawki.</span><span class="sxs-lookup"><span data-stu-id="cad51-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cad51-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cad51-110">Remarks</span></span>  
 <span data-ttu-id="cad51-111">Aby uzyskać informacji o numerach wersji zestawu, zobacz <xref:System.Version> temat poświęcony klasie.</span><span class="sxs-lookup"><span data-stu-id="cad51-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cad51-112">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cad51-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cad51-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cad51-113">Requirements</span></span>  
 <span data-ttu-id="cad51-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cad51-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cad51-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cad51-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cad51-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cad51-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cad51-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cad51-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cad51-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cad51-118">See also</span></span>
- [<span data-ttu-id="cad51-119">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="cad51-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="cad51-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cad51-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
