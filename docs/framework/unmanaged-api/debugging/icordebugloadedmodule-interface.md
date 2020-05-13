---
title: ICorDebugLoadedModule — interfejs
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
ms.openlocfilehash: d9b8245d8c37867971aa48ed3befb9cf22bd5b04
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210166"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="321b1-102">ICorDebugLoadedModule — interfejs</span><span class="sxs-lookup"><span data-stu-id="321b1-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="321b1-103">Zawiera informacje o załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="321b1-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="321b1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="321b1-104">Methods</span></span>  
  
|<span data-ttu-id="321b1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="321b1-105">Method</span></span>|<span data-ttu-id="321b1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="321b1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="321b1-107">GetBaseAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="321b1-107">GetBaseAddress Method</span></span>](icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="321b1-108">Pobiera adres podstawowy załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="321b1-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="321b1-109">GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="321b1-109">GetName Method</span></span>](icordebugloadedmodule-getname-method.md)|<span data-ttu-id="321b1-110">Pobiera nazwę załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="321b1-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="321b1-111">GetSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="321b1-111">GetSize Method</span></span>](icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="321b1-112">Pobiera rozmiar w bajtach załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="321b1-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="321b1-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="321b1-113">Remarks</span></span>  
 <span data-ttu-id="321b1-114">`ICorDebugLoadedModule`Interfejs jest implementowany przez debuger i jest używany przez interfejsy debugowania CLR do uzyskiwania informacji o załadowanym module z debugera.</span><span class="sxs-lookup"><span data-stu-id="321b1-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="321b1-115">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="321b1-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="321b1-116">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="321b1-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="321b1-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="321b1-117">Requirements</span></span>  
 <span data-ttu-id="321b1-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="321b1-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="321b1-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="321b1-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="321b1-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="321b1-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="321b1-121">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="321b1-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="321b1-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="321b1-122">See also</span></span>

- [<span data-ttu-id="321b1-123">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="321b1-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="321b1-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="321b1-124">Debugging</span></span>](index.md)
