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
ms.openlocfilehash: 9ee6f43c94b8ff2e765d2a0dde0697c4c895a94f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212376"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a><span data-ttu-id="cc17c-102">ICorDebugManagedCallback::UpdateModuleSymbols — Metoda</span><span class="sxs-lookup"><span data-stu-id="cc17c-102">ICorDebugManagedCallback::UpdateModuleSymbols Method</span></span>
<span data-ttu-id="cc17c-103">Powiadamia debuger o zmianie symboli dla modułu uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="cc17c-103">Notifies the debugger that the symbols for a common language runtime module have changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc17c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc17c-104">Syntax</span></span>  
  
```cpp  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc17c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc17c-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="cc17c-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierającą moduł, w którym symbole zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="cc17c-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the module in which the symbols have changed.</span></span>  
  
 `pModule`  
 <span data-ttu-id="cc17c-107">podczas Wskaźnik do obiektu ICorDebugModule, który reprezentuje moduł, w którym symbole zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="cc17c-107">[in] A pointer to an ICorDebugModule object that represents the module in which the symbols have changed.</span></span>  
  
 `pSymbolStream`  
 <span data-ttu-id="cc17c-108">podczas Wskaźnik do obiektu Win32 COM `IStream` , który zawiera zmodyfikowane symbole.</span><span class="sxs-lookup"><span data-stu-id="cc17c-108">[in] A pointer to a Win32 COM `IStream` object that contains the modified symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc17c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc17c-109">Remarks</span></span>  
 <span data-ttu-id="cc17c-110">Ta metoda umożliwia zaktualizowanie podglądu symboli modułu przez wywołanie [ISymUnmanagedReader:: UpdateSymbolStore —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) lub [ISymUnmanagedReader:: ReplaceSymbolStore —](../diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span><span class="sxs-lookup"><span data-stu-id="cc17c-110">This method provides an opportunity to update the debugger's view of a module's symbols by calling [ISymUnmanagedReader::UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) or [ISymUnmanagedReader::ReplaceSymbolStore](../diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span></span>  
  
 <span data-ttu-id="cc17c-111">To wywołanie zwrotne może wystąpić wiele razy dla tego samego modułu.</span><span class="sxs-lookup"><span data-stu-id="cc17c-111">This callback can occur multiple times for the same module.</span></span>  
  
 <span data-ttu-id="cc17c-112">Debuger powinien próbować powiązać niepowiązane punkty przerwania na poziomie źródła.</span><span class="sxs-lookup"><span data-stu-id="cc17c-112">A debugger should try to bind unbound source-level breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc17c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cc17c-113">Requirements</span></span>  
 <span data-ttu-id="cc17c-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc17c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc17c-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cc17c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc17c-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cc17c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc17c-117">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc17c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc17c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc17c-118">See also</span></span>

- [<span data-ttu-id="cc17c-119">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cc17c-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
