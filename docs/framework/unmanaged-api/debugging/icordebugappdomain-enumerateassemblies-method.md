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
ms.openlocfilehash: 573b08fcf2ce0fa5ce3187df6ae6a1c2cc385f52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134008"
---
# <a name="icordebugappdomainenumerateassemblies-method"></a><span data-ttu-id="ad6fa-102">ICorDebugAppDomain::EnumerateAssemblies — Metoda</span><span class="sxs-lookup"><span data-stu-id="ad6fa-102">ICorDebugAppDomain::EnumerateAssemblies Method</span></span>
<span data-ttu-id="ad6fa-103">Pobiera moduł wyliczający dla zestawów w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ad6fa-103">Gets an enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad6fa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad6fa-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateAssemblies (  
    [out] ICorDebugAssemblyEnum  **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad6fa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad6fa-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="ad6fa-106">określoną Wskaźnik do adresu obiektu ICorDebugAssemblyEnum, który jest modułem wyliczającym dla zestawów w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ad6fa-106">[out] A pointer to the address of an ICorDebugAssemblyEnum object that is the enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad6fa-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad6fa-107">Requirements</span></span>  
 <span data-ttu-id="ad6fa-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad6fa-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad6fa-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ad6fa-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad6fa-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ad6fa-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad6fa-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad6fa-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
