---
title: "ICorDebugManagedCallback::UpdateModuleSymbols — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback.UpdateModuleSymbols
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UpdateModuleSymbols
helpviewer_keywords:
- UpdateModuleSymbols method [.NET Framework debugging]
- ICorDebugManagedCallback::UpdateModuleSymbols method [.NET Framework debugging]
ms.assetid: 0863f644-58e8-45a0-b0c3-a28e99b20938
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ad5a84268f3810a1fb73a21a6bd8106e82ccbd78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a><span data-ttu-id="b4bab-102">ICorDebugManagedCallback::UpdateModuleSymbols — Metoda</span><span class="sxs-lookup"><span data-stu-id="b4bab-102">ICorDebugManagedCallback::UpdateModuleSymbols Method</span></span>
<span data-ttu-id="b4bab-103">Powiadamia debuger zmieniono symboli dla modułu środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="b4bab-103">Notifies the debugger that the symbols for a common language runtime module have changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4bab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4bab-104">Syntax</span></span>  
  
```  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4bab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4bab-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b4bab-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji zawierające moduł, w którym symbole zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="b4bab-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the module in which the symbols have changed.</span></span>  
  
 `pModule`  
 <span data-ttu-id="b4bab-107">[in] Wskaźnik do obiektu ICorDebugModule, który reprezentuje modułu, w którym symbole zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="b4bab-107">[in] A pointer to an ICorDebugModule object that represents the module in which the symbols have changed.</span></span>  
  
 `pSymbolStream`  
 <span data-ttu-id="b4bab-108">[in] Wskaźnik do Win32 COM `IStream` obiekt, który zawiera symbole zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="b4bab-108">[in] A pointer to a Win32 COM `IStream` object that contains the modified symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4bab-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4bab-109">Remarks</span></span>  
 <span data-ttu-id="b4bab-110">Ta metoda zapewnia możliwość zaktualizować widoku debugera symboli modułu wywołując [ISymUnmanagedReader::UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) lub [ISymUnmanagedReader::ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span><span class="sxs-lookup"><span data-stu-id="b4bab-110">This method provides an opportunity to update the debugger's view of a module's symbols by calling [ISymUnmanagedReader::UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) or [ISymUnmanagedReader::ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span></span>  
  
 <span data-ttu-id="b4bab-111">Tego wywołania zwrotnego może wystąpić wiele razy dla tego samego modułu.</span><span class="sxs-lookup"><span data-stu-id="b4bab-111">This callback can occur multiple times for the same module.</span></span>  
  
 <span data-ttu-id="b4bab-112">Debuger należy dążyć do powiązania niezwiązanego poziomu źródła punktów przerwania.</span><span class="sxs-lookup"><span data-stu-id="b4bab-112">A debugger should try to bind unbound source-level breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4bab-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4bab-113">Requirements</span></span>  
 <span data-ttu-id="b4bab-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4bab-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4bab-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4bab-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4bab-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4bab-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4bab-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4bab-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4bab-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4bab-118">See Also</span></span>  
 [<span data-ttu-id="b4bab-119">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="b4bab-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
