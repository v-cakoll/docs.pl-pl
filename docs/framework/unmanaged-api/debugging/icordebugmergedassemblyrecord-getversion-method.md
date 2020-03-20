---
title: ICorDebugMergedAssemblyRecord::Metoda GetVersion
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 5dc9995e88086da854d2e9382cef81b229ff9dc9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178683"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="7cc35-102">ICorDebugMergedAssemblyRecord::Metoda GetVersion</span><span class="sxs-lookup"><span data-stu-id="7cc35-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="7cc35-103">Pobiera informacje o wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="7cc35-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cc35-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7cc35-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,
   [out] USHORT *pMinor,
   [out] USHORT *pBuild,
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cc35-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7cc35-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="7cc35-106">[na zewnątrz] Wskaźnik do głównego numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="7cc35-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="7cc35-107">[na zewnątrz] Wskaźnik do pomocniczego numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="7cc35-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="7cc35-108">[na zewnątrz] Wskaźnik do numeru kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7cc35-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="7cc35-109">[na zewnątrz] Wskaźnik do numeru poprawki.</span><span class="sxs-lookup"><span data-stu-id="7cc35-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cc35-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7cc35-110">Remarks</span></span>  
 <span data-ttu-id="7cc35-111">Aby uzyskać informacje na temat <xref:System.Version> numerów wersji zestawu, zobacz temat klasy.</span><span class="sxs-lookup"><span data-stu-id="7cc35-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7cc35-112">Ta metoda jest dostępna tylko w przypadku platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7cc35-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cc35-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7cc35-113">Requirements</span></span>  
 <span data-ttu-id="7cc35-114">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cc35-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cc35-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7cc35-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7cc35-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cc35-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cc35-117">**Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cc35-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cc35-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7cc35-118">See also</span></span>

- [<span data-ttu-id="7cc35-119">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="7cc35-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="7cc35-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="7cc35-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
