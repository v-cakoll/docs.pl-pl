---
title: Wyliczenie WriteableMetadataUpdateMode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- WriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6758f4d3-6bc7-4c99-8582-e9be00566784
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fbf9a24c350dd4c33bb50b0add8817c8922925f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="writeablemetadataupdatemode-enumeration"></a><span data-ttu-id="8fc13-102">Wyliczenie WriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="8fc13-102">WriteableMetadataUpdateMode Enumeration</span></span>
<span data-ttu-id="8fc13-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="8fc13-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="8fc13-104">Zawiera wartości, które określają, czy aktualizacje metadanych w pamięci są widoczne dla debugera.</span><span class="sxs-lookup"><span data-stu-id="8fc13-104">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fc13-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8fc13-105">Syntax</span></span>  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a><span data-ttu-id="8fc13-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8fc13-106">Members</span></span>  
  
|<span data-ttu-id="8fc13-107">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="8fc13-107">Member name</span></span>|<span data-ttu-id="8fc13-108">Opis</span><span class="sxs-lookup"><span data-stu-id="8fc13-108">Description</span></span>|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|<span data-ttu-id="8fc13-109">Zachować zgodność z poprzednimi wersjami programu .NET Framework podczas wprowadzania aktualizacji w pamięci metadanych widoczne.</span><span class="sxs-lookup"><span data-stu-id="8fc13-109">Maintain compatibility with previous versions of the .NET Framework when making in-memory updates to metadata visible.</span></span> <span data-ttu-id="8fc13-110">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="8fc13-110">See the Remarks section for more information.</span></span>|  
|`AlwaysShowUpdates`|<span data-ttu-id="8fc13-111">Wyświetlaj aktualizacje w pamięci do metadanych do debugera.</span><span class="sxs-lookup"><span data-stu-id="8fc13-111">Make in-memory updates to metadata visible to the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fc13-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8fc13-112">Remarks</span></span>  
 <span data-ttu-id="8fc13-113">Członek `WriteableMetadataUpdateMode` wyliczenia mogą zostać przekazane do [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) metody kontrolowania, czy w pamięci aktualizacji metadanych w procesie docelowym są widoczne dla debugera.</span><span class="sxs-lookup"><span data-stu-id="8fc13-113">A member of the `WriteableMetadataUpdateMode` enumeration can be passed to the [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) method to control whether in-memory updates to metadata in the target process are visible to the debugger.</span></span>  
  
 <span data-ttu-id="8fc13-114">`LegacyCompatPolicy` Opcja wymusza takie samo jak wersji programu .NET Framework, przed 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="8fc13-114">The `LegacyCompatPolicy` option enforces the same behavior as in versions of the .NET Framework before 4.5.2.</span></span> <span data-ttu-id="8fc13-115">Często oznacza to, że metadane z aktualizacji nie jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="8fc13-115">This often means that metadata from updates is not visible.</span></span> <span data-ttu-id="8fc13-116">Wywołań metod debugowania przekształcić niejawnie debugera, aby aktualizacje były widoczne.</span><span class="sxs-lookup"><span data-stu-id="8fc13-116">However, calls to a number of debugging methods implicitly coerce the debugger to make updates visible.</span></span> <span data-ttu-id="8fc13-117">Na przykład, jeśli przekazuje debuger [ICorDebugILFrame::GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) indeksu zmiennej nie znaleziono metody oryginalnych metadanych, wszystkie metadane dla modułu jest aktualizowana do migawki dopasowania bieżący stan proces.</span><span class="sxs-lookup"><span data-stu-id="8fc13-117">For example, if the debugger passes [ICorDebugILFrame::GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) the index of a variable not found in the method's original metadata, all metadata for the module is updated to a snapshot matching the current state of the process.</span></span> <span data-ttu-id="8fc13-118">Innymi słowy, z `LegacyCompatPolicy` opcji debuger napotkać none, niektóre lub wszystkie aktualizacje dostępne metadanych, w zależności od tego, jak używa innych części niezarządzanego API debugowania.</span><span class="sxs-lookup"><span data-stu-id="8fc13-118">In other words, with the `LegacyCompatPolicy` option, the debugger might see none, some, or all of the available metadata updates, depending on how it uses other parts of the unmanaged debugging API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fc13-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8fc13-119">Requirements</span></span>  
 <span data-ttu-id="8fc13-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fc13-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fc13-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8fc13-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8fc13-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fc13-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fc13-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fc13-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc13-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8fc13-124">See Also</span></span>  
 [<span data-ttu-id="8fc13-125">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="8fc13-125">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="8fc13-126">SetWriteableMetadataUpdateMode, metoda</span><span class="sxs-lookup"><span data-stu-id="8fc13-126">SetWriteableMetadataUpdateMode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
