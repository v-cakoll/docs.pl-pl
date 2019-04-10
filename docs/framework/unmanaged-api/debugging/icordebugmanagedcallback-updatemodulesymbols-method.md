---
title: ICorDebugManagedCallback::UpdateModuleSymbols — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 581ea4f974bfec3961a32cd7c9985a5e45d2bddd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209986"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a><span data-ttu-id="75a80-102">ICorDebugManagedCallback::UpdateModuleSymbols — Metoda</span><span class="sxs-lookup"><span data-stu-id="75a80-102">ICorDebugManagedCallback::UpdateModuleSymbols Method</span></span>
<span data-ttu-id="75a80-103">Powiadamia debuger zmieniono symbole dla moduł środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="75a80-103">Notifies the debugger that the symbols for a common language runtime module have changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75a80-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="75a80-104">Syntax</span></span>  
  
```  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75a80-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="75a80-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="75a80-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierające moduł, w którym symbole zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="75a80-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the module in which the symbols have changed.</span></span>  
  
 `pModule`  
 <span data-ttu-id="75a80-107">[in] Wskaźnik do obiektu ICorDebugModule, który reprezentuje moduł, w którym symbole zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="75a80-107">[in] A pointer to an ICorDebugModule object that represents the module in which the symbols have changed.</span></span>  
  
 `pSymbolStream`  
 <span data-ttu-id="75a80-108">[in] Wskaźnik do Win32 COM `IStream` obiekt, który zawiera symbole zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="75a80-108">[in] A pointer to a Win32 COM `IStream` object that contains the modified symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75a80-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="75a80-109">Remarks</span></span>  
 <span data-ttu-id="75a80-110">Ta metoda zapewnia możliwość zaktualizuj widok debugera symboli dla modułu, wywołując [ISymUnmanagedReader::UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) lub [ISymUnmanagedReader::ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span><span class="sxs-lookup"><span data-stu-id="75a80-110">This method provides an opportunity to update the debugger's view of a module's symbols by calling [ISymUnmanagedReader::UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) or [ISymUnmanagedReader::ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span></span>  
  
 <span data-ttu-id="75a80-111">To wywołanie zwrotne, może wystąpić wiele razy dla tego samego modułu.</span><span class="sxs-lookup"><span data-stu-id="75a80-111">This callback can occur multiple times for the same module.</span></span>  
  
 <span data-ttu-id="75a80-112">Debuger starać się powiązać niepowiązanych poziom źródła punktów przerwania.</span><span class="sxs-lookup"><span data-stu-id="75a80-112">A debugger should try to bind unbound source-level breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75a80-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75a80-113">Requirements</span></span>  
 <span data-ttu-id="75a80-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75a80-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75a80-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75a80-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75a80-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75a80-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="75a80-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="75a80-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="75a80-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75a80-118">See also</span></span>

- [<span data-ttu-id="75a80-119">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="75a80-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
