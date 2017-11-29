---
title: "ICorProfilerInfo::GetILFunctionBody — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetILFunctionBody
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6908b6c765a56ef0aa43a66cc58ec74b525bc2d3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="673b3-102">ICorProfilerInfo::GetILFunctionBody — Metoda</span><span class="sxs-lookup"><span data-stu-id="673b3-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="673b3-103">Pobiera wskaźnik do treści metody w kodzie języka pośredniego (MSIL) firmy Microsoft, zaczynając od jej nagłówek.</span><span class="sxs-lookup"><span data-stu-id="673b3-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="673b3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="673b3-104">Syntax</span></span>  
  
```  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="673b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="673b3-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="673b3-106">[in] Identyfikator modułu, w której znajduje się funkcja.</span><span class="sxs-lookup"><span data-stu-id="673b3-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="673b3-107">[in] Token metadanych dla metody.</span><span class="sxs-lookup"><span data-stu-id="673b3-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="673b3-108">[out] Wskaźnik do nagłówka metody.</span><span class="sxs-lookup"><span data-stu-id="673b3-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="673b3-109">[out] Liczba całkowita określająca rozmiar metody.</span><span class="sxs-lookup"><span data-stu-id="673b3-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="673b3-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="673b3-110">Remarks</span></span>  
 <span data-ttu-id="673b3-111">Metoda ma zakres przez moduł, w którym mieszka.</span><span class="sxs-lookup"><span data-stu-id="673b3-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="673b3-112">Ponieważ `GetILFunctionBody` metoda jest przeznaczona do udostępnienia narzędzie kod MSIL przed został załadowany przez środowisko uruchomieniowe języka wspólnego (CLR), używa token metadanych metody, aby znaleźć odpowiednie wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="673b3-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="673b3-113">`GetILFunctionBody`może zwrócić CORPROF_E_FUNCTION_NOT_IL HRESULT, jeśli `methodId` wskazuje metodę bez żadnych MSIL kodu (takie jak metoda abstrakcyjna lub platformę invoke — metoda (funkcja PInvoke)).</span><span class="sxs-lookup"><span data-stu-id="673b3-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="673b3-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="673b3-114">Requirements</span></span>  
 <span data-ttu-id="673b3-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="673b3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="673b3-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="673b3-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="673b3-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="673b3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="673b3-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="673b3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="673b3-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="673b3-119">See Also</span></span>  
 [<span data-ttu-id="673b3-120">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="673b3-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
