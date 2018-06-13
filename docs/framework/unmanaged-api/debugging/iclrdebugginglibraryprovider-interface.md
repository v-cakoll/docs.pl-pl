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
ms.openlocfilehash: 7537d3d6f741f36ab81d73751963a8539de0a36c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404472"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="9e1a3-102">ICLRDebuggingLibraryProvider — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9e1a3-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="9e1a3-103">Obejmuje [ProvideLibrary — metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) metodę, która pobiera dostawcę biblioteki interfejsu wywołania zwrotnego, który umożliwia języka wspólnego bibliotek debugowania określonej wersji środowiska uruchomieniowego należy odnaleźć i załadować na żądanie.</span><span class="sxs-lookup"><span data-stu-id="9e1a3-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e1a3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9e1a3-104">Methods</span></span>  
  
|<span data-ttu-id="9e1a3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9e1a3-105">Method</span></span>|<span data-ttu-id="9e1a3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="9e1a3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e1a3-107">ProvideLibrary, metoda</span><span class="sxs-lookup"><span data-stu-id="9e1a3-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="9e1a3-108">Umożliwia debuger w celu zapewnienia dojścia do modułu, którego można użyć do załadowania biblioteki debugowania.</span><span class="sxs-lookup"><span data-stu-id="9e1a3-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9e1a3-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e1a3-109">Requirements</span></span>  
 <span data-ttu-id="9e1a3-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e1a3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e1a3-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e1a3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e1a3-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e1a3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e1a3-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e1a3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e1a3-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e1a3-114">See Also</span></span>  
 [<span data-ttu-id="9e1a3-115">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9e1a3-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9e1a3-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="9e1a3-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
