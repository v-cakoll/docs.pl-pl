---
title: "ICorDebugEval::NewObjectNoConstructor — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.NewObjectNoConstructor
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::NewObjectNoConstructor
helpviewer_keywords:
- NewObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval::NewObjectNoConstructor method [.NET Framework debugging]
ms.assetid: 80d509ca-b5e3-4c46-9c14-800db73d9bf7
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 415c8f2faae44fbdfec5441abaff8b93042ac124
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="20feb-102">ICorDebugEval::NewObjectNoConstructor — Metoda</span><span class="sxs-lookup"><span data-stu-id="20feb-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>
<span data-ttu-id="20feb-103">Przydziela nowe wystąpienie obiektu określonego typu bez próba wywołania metody konstruktora.</span><span class="sxs-lookup"><span data-stu-id="20feb-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="20feb-104">Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="20feb-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="20feb-105">Użyj [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="20feb-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20feb-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="20feb-106">Syntax</span></span>  
  
```  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20feb-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="20feb-107">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="20feb-108">[in] Wskaźnik do obiektu ICorDebugClass, który reprezentuje typ obiektu można utworzyć wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="20feb-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20feb-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20feb-109">Requirements</span></span>  
 <span data-ttu-id="20feb-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20feb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20feb-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20feb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20feb-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20feb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20feb-113">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="20feb-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20feb-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20feb-114">See Also</span></span>  
 [<span data-ttu-id="20feb-115">NewParameterizedObjectNoConstructor — metoda</span><span class="sxs-lookup"><span data-stu-id="20feb-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)
