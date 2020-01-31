---
title: ICorProfilerInfo::GetModuleMetaData — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
ms.openlocfilehash: 6e787de6287dc5b3091d3671d3da2f2154b12e88
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869927"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="1088d-102">ICorProfilerInfo::GetModuleMetaData — Metoda</span><span class="sxs-lookup"><span data-stu-id="1088d-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="1088d-103">Pobiera wystąpienie interfejsu metadanych, które mapuje do określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="1088d-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1088d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1088d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1088d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1088d-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="1088d-106">podczas Identyfikator modułu, do którego zostanie zamapowana wystąpienie interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1088d-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="1088d-107">podczas Wartość wyliczenia [CorOpenFlags —](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) , która określa tryb otwierania plików manifestu.</span><span class="sxs-lookup"><span data-stu-id="1088d-107">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="1088d-108">Tylko `ofRead`, `ofWrite` i `ofNoTransform` BITS są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="1088d-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="1088d-109">podczas Identyfikator odwołania (GUID) interfejsu metadanych, którego wystąpienie zostanie pobrane.</span><span class="sxs-lookup"><span data-stu-id="1088d-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="1088d-110">Zobacz [interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) , aby uzyskać listę interfejsów.</span><span class="sxs-lookup"><span data-stu-id="1088d-110">See [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="1088d-111">określoną Wskaźnik do adresu wystąpienia interfejsu metadanych.</span><span class="sxs-lookup"><span data-stu-id="1088d-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1088d-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1088d-112">Remarks</span></span>  
 <span data-ttu-id="1088d-113">Możesz poproszenie o otwarcie metadanych w trybie odczytu/zapisu, ale spowoduje to wolniejsze wykonanie tego programu, ponieważ nie można zoptymalizować zmian wprowadzonych w metadanych, ponieważ znajdowały się one w kompilatorze.</span><span class="sxs-lookup"><span data-stu-id="1088d-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="1088d-114">Niektóre moduły (takie jak moduły zasobów) nie mają metadanych.</span><span class="sxs-lookup"><span data-stu-id="1088d-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="1088d-115">W takich przypadkach `GetModuleMetaData` zwróci wartość HRESULT S_FALSE i ma wartość null w`ppOut`.</span><span class="sxs-lookup"><span data-stu-id="1088d-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1088d-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1088d-116">Requirements</span></span>  
 <span data-ttu-id="1088d-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1088d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1088d-118">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1088d-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1088d-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1088d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1088d-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1088d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1088d-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1088d-121">See also</span></span>

- [<span data-ttu-id="1088d-122">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="1088d-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
