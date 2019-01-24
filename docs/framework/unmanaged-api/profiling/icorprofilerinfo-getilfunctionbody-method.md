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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9e1ef61271e5b413972b8ba40a8fe8bac60ceeb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566222"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="89389-102">ICorProfilerInfo::GetILFunctionBody — Metoda</span><span class="sxs-lookup"><span data-stu-id="89389-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="89389-103">Pobiera wskaźnik do treści metody w kodzie języka intermediate language (MSIL) firmy Microsoft, zaczynając od jej nagłówek.</span><span class="sxs-lookup"><span data-stu-id="89389-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89389-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="89389-104">Syntax</span></span>  
  
```  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89389-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="89389-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="89389-106">[in] Identyfikator modułu, w której znajduje się funkcja.</span><span class="sxs-lookup"><span data-stu-id="89389-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="89389-107">[in] Token metadanych dla metody.</span><span class="sxs-lookup"><span data-stu-id="89389-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="89389-108">[out] Wskaźnik do nagłówka metody.</span><span class="sxs-lookup"><span data-stu-id="89389-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="89389-109">[out] Liczba całkowita określająca rozmiar metody.</span><span class="sxs-lookup"><span data-stu-id="89389-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89389-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89389-110">Remarks</span></span>  
 <span data-ttu-id="89389-111">Metoda obejmuje przez moduł, w którym się znajdują.</span><span class="sxs-lookup"><span data-stu-id="89389-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="89389-112">Ponieważ `GetILFunctionBody` metoda kwotę ustalono, aby udzielić dostępu narzędzie do kodu MSIL, zanim został załadowany przez środowisko uruchomieniowe języka wspólnego (CLR), używa tokenu metadanych, metody można znaleźć żądanego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="89389-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="89389-113">`GetILFunctionBody` może zwracać CORPROF_E_FUNCTION_NOT_IL HRESULT, jeśli `methodId` wskazuje metodę bez żadnych MSIL kod (takie jak metody abstrakcyjnej lub platformę invoke, metoda (funkcja PInvoke)).</span><span class="sxs-lookup"><span data-stu-id="89389-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89389-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="89389-114">Requirements</span></span>  
 <span data-ttu-id="89389-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89389-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89389-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="89389-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="89389-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89389-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89389-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89389-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89389-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89389-119">See also</span></span>
- [<span data-ttu-id="89389-120">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="89389-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
