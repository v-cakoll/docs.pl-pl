---
title: ICorProfilerInfo::GetModuleInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
ms.openlocfilehash: aae6d33166a7685e07c4d82f654f803600e37eec
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438895"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="f8f4d-102">ICorProfilerInfo::GetModuleInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="f8f4d-102">ICorProfilerInfo::GetModuleInfo Method</span></span>
<span data-ttu-id="f8f4d-103">Podanym IDENTYFIKATORem modułu zwraca nazwę pliku modułu i identyfikator zestawu nadrzędnego modułu.</span><span class="sxs-lookup"><span data-stu-id="f8f4d-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8f4d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8f4d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8f4d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8f4d-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="f8f4d-106">podczas Identyfikator modułu, dla którego będą pobierane informacje.</span><span class="sxs-lookup"><span data-stu-id="f8f4d-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="f8f4d-107">określoną Adres podstawowy, z którego moduł jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="f8f4d-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="f8f4d-108">podczas Długość (w znakach) `szName` buforu powrotu.</span><span class="sxs-lookup"><span data-stu-id="f8f4d-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f8f4d-109">określoną Wskaźnik do łącznej długości znaku nazwy pliku modułu, który jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="f8f4d-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="f8f4d-110">określoną Bufor znaków udostępniany przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="f8f4d-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="f8f4d-111">Gdy metoda zwraca, ten bufor zawiera nazwę pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="f8f4d-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="f8f4d-112">określoną Wskaźnik do identyfikatora zestawu nadrzędnego modułu.</span><span class="sxs-lookup"><span data-stu-id="f8f4d-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8f4d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8f4d-113">Remarks</span></span>  
 <span data-ttu-id="f8f4d-114">W przypadku modułów dynamicznych parametr `szName` jest pustym ciągiem, a adres podstawowy to 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="f8f4d-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="f8f4d-115">Mimo że metoda `GetModuleInfo` może być wywoływana, gdy tylko identyfikator modułu istnieje, identyfikator zestawu nadrzędnego nie będzie dostępny do momentu otrzymania przez profiler wywołania zwrotnego [ICorProfilerCallback:: ModuleAttachedToAssembly —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f8f4d-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="f8f4d-116">Gdy `GetModuleInfo` zwraca, należy sprawdzić, czy bufor `szName` był wystarczająco duży, aby zawierał pełną nazwę pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="f8f4d-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="f8f4d-117">W tym celu należy porównać wartość, która `pcchName` wskazuje na wartość parametru `cchName`.</span><span class="sxs-lookup"><span data-stu-id="f8f4d-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="f8f4d-118">Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większy bufor `szName`, zaktualizuj `cchName` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetModuleInfo`.</span><span class="sxs-lookup"><span data-stu-id="f8f4d-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="f8f4d-119">Alternatywnie można najpierw wywołać `GetModuleInfo` z buforem `szName` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="f8f4d-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="f8f4d-120">Następnie można ustawić rozmiar buforu na wartość zwróconą w `pcchName` i ponownie wywołać `GetModuleInfo`.</span><span class="sxs-lookup"><span data-stu-id="f8f4d-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8f4d-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f8f4d-121">Requirements</span></span>  
 <span data-ttu-id="f8f4d-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8f4d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8f4d-123">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f8f4d-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f8f4d-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f8f4d-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8f4d-125">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8f4d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8f4d-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8f4d-126">See also</span></span>

- [<span data-ttu-id="f8f4d-127">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="f8f4d-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="f8f4d-128">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="f8f4d-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="f8f4d-129">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="f8f4d-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
- [<span data-ttu-id="f8f4d-130">GetModuleInfo2, metoda</span><span class="sxs-lookup"><span data-stu-id="f8f4d-130">GetModuleInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
