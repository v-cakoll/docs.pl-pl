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
ms.openlocfilehash: c0381cf924e44e581c8b275c9750cacba045cf1b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501784"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a><span data-ttu-id="871b4-102">ICorDebugManagedCallback::UpdateModuleSymbols — Metoda</span><span class="sxs-lookup"><span data-stu-id="871b4-102">ICorDebugManagedCallback::UpdateModuleSymbols Method</span></span>
<span data-ttu-id="871b4-103">Powiadamia debuger o zmianie symboli dla modułu uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="871b4-103">Notifies the debugger that the symbols for a common language runtime module have changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="871b4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="871b4-104">Syntax</span></span>  
  
```cpp  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="871b4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="871b4-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="871b4-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierającą moduł, w którym symbole zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="871b4-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the module in which the symbols have changed.</span></span>  
  
 `pModule`  
 <span data-ttu-id="871b4-107">podczas Wskaźnik do obiektu ICorDebugModule, który reprezentuje moduł, w którym symbole zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="871b4-107">[in] A pointer to an ICorDebugModule object that represents the module in which the symbols have changed.</span></span>  
  
 `pSymbolStream`  
 <span data-ttu-id="871b4-108">podczas Wskaźnik do obiektu Win32 COM `IStream` , który zawiera zmodyfikowane symbole.</span><span class="sxs-lookup"><span data-stu-id="871b4-108">[in] A pointer to a Win32 COM `IStream` object that contains the modified symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="871b4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="871b4-109">Remarks</span></span>  
 <span data-ttu-id="871b4-110">Ta metoda umożliwia zaktualizowanie podglądu symboli modułu przez wywołanie [ISymUnmanagedReader:: UpdateSymbolStore —](../diagnostics/isymunmanagedreader-updatesymbolstore-method.md) lub [ISymUnmanagedReader:: ReplaceSymbolStore —](../diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span><span class="sxs-lookup"><span data-stu-id="871b4-110">This method provides an opportunity to update the debugger's view of a module's symbols by calling [ISymUnmanagedReader::UpdateSymbolStore](../diagnostics/isymunmanagedreader-updatesymbolstore-method.md) or [ISymUnmanagedReader::ReplaceSymbolStore](../diagnostics/isymunmanagedreader-replacesymbolstore-method.md).</span></span>  
  
 <span data-ttu-id="871b4-111">To wywołanie zwrotne może wystąpić wiele razy dla tego samego modułu.</span><span class="sxs-lookup"><span data-stu-id="871b4-111">This callback can occur multiple times for the same module.</span></span>  
  
 <span data-ttu-id="871b4-112">Debuger powinien próbować powiązać niepowiązane punkty przerwania na poziomie źródła.</span><span class="sxs-lookup"><span data-stu-id="871b4-112">A debugger should try to bind unbound source-level breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="871b4-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="871b4-113">Requirements</span></span>  
 <span data-ttu-id="871b4-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="871b4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="871b4-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="871b4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="871b4-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="871b4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="871b4-117">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="871b4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="871b4-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="871b4-118">See also</span></span>

- [<span data-ttu-id="871b4-119">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="871b4-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
