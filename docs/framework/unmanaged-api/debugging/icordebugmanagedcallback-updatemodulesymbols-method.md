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
ms.openlocfilehash: 2b64122489481c6b0fde605015720d0a56ba8fe2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788325"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a><span data-ttu-id="55c88-102">ICorDebugManagedCallback::UpdateModuleSymbols — Metoda</span><span class="sxs-lookup"><span data-stu-id="55c88-102">ICorDebugManagedCallback::UpdateModuleSymbols Method</span></span>
<span data-ttu-id="55c88-103">Powiadamia debuger o zmianie symboli dla modułu uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="55c88-103">Notifies the debugger that the symbols for a common language runtime module have changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55c88-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="55c88-104">Syntax</span></span>  
  
```cpp  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55c88-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="55c88-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="55c88-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierającą moduł, w którym symbole zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="55c88-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the module in which the symbols have changed.</span></span>  
  
 `pModule`  
 <span data-ttu-id="55c88-107">podczas Wskaźnik do obiektu ICorDebugModule, który reprezentuje moduł, w którym symbole zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="55c88-107">[in] A pointer to an ICorDebugModule object that represents the module in which the symbols have changed.</span></span>  
  
 `pSymbolStream`  
 <span data-ttu-id="55c88-108">podczas Wskaźnik do obiektu `IStream` Win32 COM, który zawiera zmodyfikowane symbole.</span><span class="sxs-lookup"><span data-stu-id="55c88-108">[in] A pointer to a Win32 COM `IStream` object that contains the modified symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55c88-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="55c88-109">Remarks</span></span>  
 <span data-ttu-id="55c88-110">Ta metoda umożliwia zaktualizowanie podglądu symboli modułu przez wywołanie [ISymUnmanagedReader:: UpdateSymbolStore —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) lub [ISymUnmanagedReader:: ReplaceSymbolStore —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span><span class="sxs-lookup"><span data-stu-id="55c88-110">This method provides an opportunity to update the debugger's view of a module's symbols by calling [ISymUnmanagedReader::UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) or [ISymUnmanagedReader::ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span></span>  
  
 <span data-ttu-id="55c88-111">To wywołanie zwrotne może wystąpić wiele razy dla tego samego modułu.</span><span class="sxs-lookup"><span data-stu-id="55c88-111">This callback can occur multiple times for the same module.</span></span>  
  
 <span data-ttu-id="55c88-112">Debuger powinien próbować powiązać niepowiązane punkty przerwania na poziomie źródła.</span><span class="sxs-lookup"><span data-stu-id="55c88-112">A debugger should try to bind unbound source-level breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55c88-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="55c88-113">Requirements</span></span>  
 <span data-ttu-id="55c88-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55c88-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55c88-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="55c88-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55c88-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="55c88-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55c88-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55c88-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55c88-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55c88-118">See also</span></span>

- [<span data-ttu-id="55c88-119">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="55c88-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
