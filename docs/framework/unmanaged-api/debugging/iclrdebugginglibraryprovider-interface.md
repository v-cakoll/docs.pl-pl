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
ms.openlocfilehash: a8d9348572ec0cf67c5facebb2053a7091661724
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793603"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="a33ce-102">ICLRDebuggingLibraryProvider — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a33ce-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="a33ce-103">Obejmuje metodę [metody ProvideLibrary —](iclrdebugginglibraryprovider-providelibrary-method.md) , która pobiera interfejs wywołania zwrotnego dostawcy biblioteki, który umożliwia zlokalizowanie i załadowanie bibliotek debugowania specyficznych dla wersji środowiska uruchomieniowego języka wspólnego na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a33ce-103">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a33ce-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a33ce-104">Methods</span></span>  
  
|<span data-ttu-id="a33ce-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a33ce-105">Method</span></span>|<span data-ttu-id="a33ce-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a33ce-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a33ce-107">ProvideLibrary, metoda</span><span class="sxs-lookup"><span data-stu-id="a33ce-107">ProvideLibrary Method</span></span>](iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="a33ce-108">Zezwala debugerowi na dostarczenie dojścia do modułu, którego można użyć do załadowania biblioteki debugowania.</span><span class="sxs-lookup"><span data-stu-id="a33ce-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a33ce-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a33ce-109">Requirements</span></span>  
 <span data-ttu-id="a33ce-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a33ce-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a33ce-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a33ce-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a33ce-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a33ce-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a33ce-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a33ce-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a33ce-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a33ce-114">See also</span></span>

- [<span data-ttu-id="a33ce-115">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a33ce-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a33ce-116">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="a33ce-116">Debugging</span></span>](index.md)
