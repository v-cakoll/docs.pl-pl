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
ms.openlocfilehash: 62b34128be99ce7750d45e6c19e26bef7fcc98c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502954"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="8329e-102">ICorProfilerInfo::GetModuleMetaData — Metoda</span><span class="sxs-lookup"><span data-stu-id="8329e-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="8329e-103">Pobiera wystąpienie interfejsu metadanych, które mapuje do określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="8329e-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8329e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8329e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8329e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8329e-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="8329e-106">podczas Identyfikator modułu, do którego zostanie zamapowana wystąpienie interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8329e-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="8329e-107">podczas Wartość wyliczenia [CorOpenFlags —](../metadata/coropenflags-enumeration.md) , która określa tryb otwierania plików manifestu.</span><span class="sxs-lookup"><span data-stu-id="8329e-107">[in] A value of the [CorOpenFlags](../metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="8329e-108">Tylko `ofRead` `ofWrite` `ofNoTransform` bity i są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="8329e-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="8329e-109">podczas Identyfikator odwołania (GUID) interfejsu metadanych, którego wystąpienie zostanie pobrane.</span><span class="sxs-lookup"><span data-stu-id="8329e-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="8329e-110">Zobacz [interfejsy metadanych](../metadata/metadata-interfaces.md) , aby uzyskać listę interfejsów.</span><span class="sxs-lookup"><span data-stu-id="8329e-110">See [Metadata Interfaces](../metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="8329e-111">określoną Wskaźnik do adresu wystąpienia interfejsu metadanych.</span><span class="sxs-lookup"><span data-stu-id="8329e-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8329e-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8329e-112">Remarks</span></span>  
 <span data-ttu-id="8329e-113">Możesz poproszenie o otwarcie metadanych w trybie odczytu/zapisu, ale spowoduje to wolniejsze wykonanie tego programu, ponieważ nie można zoptymalizować zmian wprowadzonych w metadanych, ponieważ znajdowały się one w kompilatorze.</span><span class="sxs-lookup"><span data-stu-id="8329e-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="8329e-114">Niektóre moduły (takie jak moduły zasobów) nie mają metadanych.</span><span class="sxs-lookup"><span data-stu-id="8329e-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="8329e-115">W takich przypadkach zwróci `GetModuleMetaData` wartość HRESULT o wartości S_FALSE i wartość null w \* `ppOut` .</span><span class="sxs-lookup"><span data-stu-id="8329e-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8329e-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8329e-116">Requirements</span></span>  
 <span data-ttu-id="8329e-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8329e-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8329e-118">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8329e-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8329e-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8329e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8329e-120">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8329e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8329e-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8329e-121">See also</span></span>

- [<span data-ttu-id="8329e-122">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="8329e-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
