---
title: ICLRDebuggingLibraryProvider — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider
helpviewer_keywords:
- ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c62079a87c09bcbe09167a137fd39530652ae3e5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59106343"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="eae37-102">ICLRDebuggingLibraryProvider — Interfejs</span><span class="sxs-lookup"><span data-stu-id="eae37-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="eae37-103">Obejmuje [providelibrary — metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) metody, która pobiera interfejs wywołania zwrotnego, która umożliwia języka wspólnego bibliotek debugowania specyficznych dla wersji środowiska uruchomieniowego lokalizowanie i ładowanie na żądanie dostawcy biblioteki.</span><span class="sxs-lookup"><span data-stu-id="eae37-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eae37-104">Metody</span><span class="sxs-lookup"><span data-stu-id="eae37-104">Methods</span></span>  
  
|<span data-ttu-id="eae37-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="eae37-105">Method</span></span>|<span data-ttu-id="eae37-106">Opis</span><span class="sxs-lookup"><span data-stu-id="eae37-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eae37-107">ProvideLibrary, metoda</span><span class="sxs-lookup"><span data-stu-id="eae37-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="eae37-108">Umożliwia debugera, aby zapewnić dojścia do modułu, który może służyć do załadowania biblioteki debugowania.</span><span class="sxs-lookup"><span data-stu-id="eae37-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eae37-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eae37-109">Requirements</span></span>  
 <span data-ttu-id="eae37-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eae37-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eae37-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eae37-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eae37-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eae37-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eae37-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eae37-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eae37-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eae37-114">See also</span></span>

- [<span data-ttu-id="eae37-115">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="eae37-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="eae37-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="eae37-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
