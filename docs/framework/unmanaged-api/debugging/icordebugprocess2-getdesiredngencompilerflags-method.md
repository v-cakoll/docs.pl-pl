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
ms.openlocfilehash: d2e54f0b16300673409eb2f5757338dfa3011e61
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213000"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="6b112-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b112-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="6b112-103">Pobiera bieżące ustawienia flagi kompilatora, które są używane przez środowisko uruchomieniowe języka wspólnego (CLR) do wybierania poprawnego prekompilowanego obrazu (czyli macierzystego) do załadowania do tego procesu.</span><span class="sxs-lookup"><span data-stu-id="6b112-103">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b112-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b112-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b112-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b112-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="6b112-106">określoną Wskaźnik do bitowej kombinacji wartości wyliczenia [CorDebugJITCompilerFlags —](cordebugjitcompilerflags-enumeration.md) , które są używane do wybierania poprawnego prekompilowanego obrazu do załadowania.</span><span class="sxs-lookup"><span data-stu-id="6b112-106">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b112-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b112-107">Remarks</span></span>  
 <span data-ttu-id="6b112-108">Użyj metody [ICorDebugProcess2:: SetDesiredNGENCompilerFlags —](icordebugprocess2-setdesiredngencompilerflags-method.md) , aby ustawić flagi, które będą używane przez środowisko CLR do wybrania poprawnego prekompilowanego obrazu do załadowania.</span><span class="sxs-lookup"><span data-stu-id="6b112-108">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b112-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b112-109">Requirements</span></span>  
 <span data-ttu-id="6b112-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b112-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b112-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6b112-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b112-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6b112-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b112-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b112-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
