---
title: ICorDebugAppDomain::EnumerateAssemblies — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateAssemblies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateAssemblies
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateAssemblies method [.NET Framework debugging]
- EnumerateAssemblies method [.NET Framework debugging]
ms.assetid: 7add64f9-19a8-46a9-be62-905d5e7d1bd8
topic_type:
- apiref
ms.openlocfilehash: 880c234462ac369ead06578730f3c14532c466e9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895286"
---
# <a name="icordebugappdomainenumerateassemblies-method"></a><span data-ttu-id="24b23-102">ICorDebugAppDomain::EnumerateAssemblies — Metoda</span><span class="sxs-lookup"><span data-stu-id="24b23-102">ICorDebugAppDomain::EnumerateAssemblies Method</span></span>
<span data-ttu-id="24b23-103">Pobiera moduł wyliczający dla zestawów w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="24b23-103">Gets an enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24b23-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="24b23-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateAssemblies (  
    [out] ICorDebugAssemblyEnum  **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24b23-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24b23-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="24b23-106">określoną Wskaźnik do adresu obiektu ICorDebugAssemblyEnum, który jest modułem wyliczającym dla zestawów w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="24b23-106">[out] A pointer to the address of an ICorDebugAssemblyEnum object that is the enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24b23-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24b23-107">Requirements</span></span>  
 <span data-ttu-id="24b23-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24b23-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24b23-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="24b23-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24b23-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="24b23-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24b23-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24b23-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
