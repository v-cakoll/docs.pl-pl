---
title: ICorProfilerInfo::GetILFunctionBody — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type:
- apiref
ms.openlocfilehash: 5984c63f0e1a1859dd5cc2550d6dc37c963affb3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503006"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="15d98-102">ICorProfilerInfo::GetILFunctionBody — Metoda</span><span class="sxs-lookup"><span data-stu-id="15d98-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="15d98-103">Pobiera wskaźnik do treści metody w kodzie języka pośredniego firmy Microsoft (MSIL), rozpoczynając od jego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="15d98-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15d98-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="15d98-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15d98-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15d98-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="15d98-106">podczas Identyfikator modułu, w którym znajduje się funkcja.</span><span class="sxs-lookup"><span data-stu-id="15d98-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="15d98-107">podczas Token metadanych dla metody.</span><span class="sxs-lookup"><span data-stu-id="15d98-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="15d98-108">określoną Wskaźnik do nagłówka metody.</span><span class="sxs-lookup"><span data-stu-id="15d98-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="15d98-109">określoną Liczba całkowita określająca rozmiar metody.</span><span class="sxs-lookup"><span data-stu-id="15d98-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15d98-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15d98-110">Remarks</span></span>  
 <span data-ttu-id="15d98-111">Metoda jest objęta zakresem przez moduł, w którym przebywa.</span><span class="sxs-lookup"><span data-stu-id="15d98-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="15d98-112">Ponieważ `GetILFunctionBody` Metoda została zaprojektowana w celu zapewnienia narzędziu dostępu do kodu MSIL przed jego załadowaniem przez środowisko uruchomieniowe języka wspólnego (CLR), używa tokenu metadanych metody w celu znalezienia żądanego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="15d98-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="15d98-113">`GetILFunctionBody`może zwrócić CORPROF_E_FUNCTION_NOT_IL HRESULT, jeśli `methodId` wskazuje na metodę bez żadnego kodu MSIL (takie jak metoda abstrakcyjna lub metoda wywołania platformy (PInvoke).</span><span class="sxs-lookup"><span data-stu-id="15d98-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15d98-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15d98-114">Requirements</span></span>  
 <span data-ttu-id="15d98-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15d98-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15d98-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="15d98-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="15d98-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="15d98-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15d98-118">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15d98-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d98-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15d98-119">See also</span></span>

- [<span data-ttu-id="15d98-120">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="15d98-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
