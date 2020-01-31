---
title: 'ICorDebugMergedAssemblyRecord:: GetVersion — Metoda'
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 8b5995183be7f1c992cf3230e16456cb248eff0c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793082"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="b2752-102">ICorDebugMergedAssemblyRecord:: GetVersion — Metoda</span><span class="sxs-lookup"><span data-stu-id="b2752-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="b2752-103">Pobiera informacje o wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="b2752-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2752-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2752-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2752-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2752-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="b2752-106">określoną Wskaźnik do głównego numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="b2752-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="b2752-107">określoną Wskaźnik do pomocniczego numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="b2752-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="b2752-108">określoną Wskaźnik do numeru kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b2752-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="b2752-109">określoną Wskaźnik do numeru poprawki.</span><span class="sxs-lookup"><span data-stu-id="b2752-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2752-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2752-110">Remarks</span></span>  
 <span data-ttu-id="b2752-111">Informacje o numerach wersji zestawu znajdują się w temacie <xref:System.Version> Class.</span><span class="sxs-lookup"><span data-stu-id="b2752-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2752-112">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b2752-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2752-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2752-113">Requirements</span></span>  
 <span data-ttu-id="b2752-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2752-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2752-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b2752-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2752-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b2752-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2752-117">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2752-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2752-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2752-118">See also</span></span>

- [<span data-ttu-id="b2752-119">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2752-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="b2752-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b2752-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
