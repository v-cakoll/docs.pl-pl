---
title: "ICLRDebuggingLibraryProvider — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebuggingLibraryProvider
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebuggingLibraryProvider
helpviewer_keywords: ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 82ed352e3f5fb83a2f464f2d82ff9a9885227fe7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="09a3a-102">ICLRDebuggingLibraryProvider — Interfejs</span><span class="sxs-lookup"><span data-stu-id="09a3a-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="09a3a-103">Obejmuje [ProvideLibrary — metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) metodę, która pobiera dostawcę biblioteki interfejsu wywołania zwrotnego, który umożliwia języka wspólnego bibliotek debugowania określonej wersji środowiska uruchomieniowego należy odnaleźć i załadować na żądanie.</span><span class="sxs-lookup"><span data-stu-id="09a3a-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="09a3a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="09a3a-104">Methods</span></span>  
  
|<span data-ttu-id="09a3a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="09a3a-105">Method</span></span>|<span data-ttu-id="09a3a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="09a3a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="09a3a-107">ProvideLibrary — metoda</span><span class="sxs-lookup"><span data-stu-id="09a3a-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="09a3a-108">Umożliwia debuger w celu zapewnienia dojścia do modułu, którego można użyć do załadowania biblioteki debugowania.</span><span class="sxs-lookup"><span data-stu-id="09a3a-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="09a3a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09a3a-109">Requirements</span></span>  
 <span data-ttu-id="09a3a-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09a3a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09a3a-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09a3a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09a3a-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09a3a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09a3a-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09a3a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09a3a-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09a3a-114">See Also</span></span>  
 [<span data-ttu-id="09a3a-115">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="09a3a-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="09a3a-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="09a3a-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
