---
title: ICorDebugProcess2::GetDesiredNGENCompilerFlags — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77ffb53e3a2b3802d3fcc1319397c8f51c5b127c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="7fdb7-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="7fdb7-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="7fdb7-103">Pobiera kompilatora bieżącego ustawienia flagi, które używa środowisko uruchomieniowe języka wspólnego (CLR), aby wybrać poprawny wstępnie skompilowana (oznacza to, że natywnego) obraz ma być załadowane do tego procesu.</span><span class="sxs-lookup"><span data-stu-id="7fdb7-103">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fdb7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7fdb7-104">Syntax</span></span>  
  
```  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7fdb7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7fdb7-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="7fdb7-106">[out] Wskaźnik do bitowe połączenie [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) wartości wyliczenia, które służą do wybierania prawidłowy prekompilowany obraz do załadowania.</span><span class="sxs-lookup"><span data-stu-id="7fdb7-106">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7fdb7-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7fdb7-107">Remarks</span></span>  
 <span data-ttu-id="7fdb7-108">Użyj [ICorDebugProcess2::SetDesiredNGENCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md) metody można ustawić flagi, które CLR będzie Użyj, aby wybrać prawidłowy obraz wstępnie skompilowanym załadować.</span><span class="sxs-lookup"><span data-stu-id="7fdb7-108">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fdb7-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7fdb7-109">Requirements</span></span>  
 <span data-ttu-id="7fdb7-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fdb7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fdb7-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7fdb7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7fdb7-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7fdb7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fdb7-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fdb7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
