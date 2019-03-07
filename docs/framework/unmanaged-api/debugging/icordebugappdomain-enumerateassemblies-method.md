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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ce95daaee3c74ac57b107ab8bcb23d41e42cabb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466651"
---
# <a name="icordebugappdomainenumerateassemblies-method"></a><span data-ttu-id="874e3-102">ICorDebugAppDomain::EnumerateAssemblies — Metoda</span><span class="sxs-lookup"><span data-stu-id="874e3-102">ICorDebugAppDomain::EnumerateAssemblies Method</span></span>
<span data-ttu-id="874e3-103">Pobiera moduł wyliczający dla zestawów w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="874e3-103">Gets an enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="874e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="874e3-104">Syntax</span></span>  
  
```  
HRESULT EnumerateAssemblies (  
    [out] ICorDebugAssemblyEnum  **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="874e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="874e3-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="874e3-106">[out] Wskaźnik na adres icordebugassemblyenum — obiekt, który jest moduł wyliczający dla zestawów w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="874e3-106">[out] A pointer to the address of an ICorDebugAssemblyEnum object that is the enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="874e3-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="874e3-107">Requirements</span></span>  
 <span data-ttu-id="874e3-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="874e3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="874e3-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="874e3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="874e3-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="874e3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="874e3-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="874e3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
