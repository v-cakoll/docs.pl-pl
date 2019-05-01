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
ms.openlocfilehash: 62e4328b75a7f6fecc28cd620ec3ac18460316c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993450"
---
# <a name="writeablemetadataupdatemode-enumeration"></a><span data-ttu-id="61b62-102">Wyliczenie WriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="61b62-102">WriteableMetadataUpdateMode Enumeration</span></span>
<span data-ttu-id="61b62-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="61b62-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="61b62-104">Zawiera wartości, które określają, czy aktualizacje metadanych w pamięci są widoczne dla debugera.</span><span class="sxs-lookup"><span data-stu-id="61b62-104">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61b62-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="61b62-105">Syntax</span></span>  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a><span data-ttu-id="61b62-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="61b62-106">Members</span></span>  
  
|<span data-ttu-id="61b62-107">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="61b62-107">Member name</span></span>|<span data-ttu-id="61b62-108">Opis</span><span class="sxs-lookup"><span data-stu-id="61b62-108">Description</span></span>|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|<span data-ttu-id="61b62-109">Podczas wprowadzania aktualizacji w pamięci do metadanych widoczne, należy zachować zgodność z poprzednimi wersjami programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="61b62-109">Maintain compatibility with previous versions of the .NET Framework when making in-memory updates to metadata visible.</span></span> <span data-ttu-id="61b62-110">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="61b62-110">See the Remarks section for more information.</span></span>|  
|`AlwaysShowUpdates`|<span data-ttu-id="61b62-111">Wyświetlaj aktualizacje w pamięci do metadanych do debugera.</span><span class="sxs-lookup"><span data-stu-id="61b62-111">Make in-memory updates to metadata visible to the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61b62-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="61b62-112">Remarks</span></span>  
 <span data-ttu-id="61b62-113">Członek `WriteableMetadataUpdateMode` wyliczenia mogą być przekazywane do [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) metodę, aby kontrolować, czy w pamięci aktualizacje metadanych w procesie docelowym są widoczne dla debugera.</span><span class="sxs-lookup"><span data-stu-id="61b62-113">A member of the `WriteableMetadataUpdateMode` enumeration can be passed to the [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) method to control whether in-memory updates to metadata in the target process are visible to the debugger.</span></span>  
  
 <span data-ttu-id="61b62-114">`LegacyCompatPolicy` Opcji wymusza takie samo zachowanie, jak w wersjach programu .NET Framework przed 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="61b62-114">The `LegacyCompatPolicy` option enforces the same behavior as in versions of the .NET Framework before 4.5.2.</span></span> <span data-ttu-id="61b62-115">Często oznacza to, metadane aktualizacji nie jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="61b62-115">This often means that metadata from updates is not visible.</span></span> <span data-ttu-id="61b62-116">Wywołania metod debugowania przekształcić niejawnie debugera, aby aktualizacje były widoczne.</span><span class="sxs-lookup"><span data-stu-id="61b62-116">However, calls to a number of debugging methods implicitly coerce the debugger to make updates visible.</span></span> <span data-ttu-id="61b62-117">Na przykład, jeśli jest debugera przekazuje [ICorDebugILFrame::GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) indeksu w zmiennej, nie znaleziono metody oryginalnych metadanych wszystkie metadane dla modułu jest aktualizowana w celu dopasowania bieżący stan migawki proces.</span><span class="sxs-lookup"><span data-stu-id="61b62-117">For example, if the debugger passes [ICorDebugILFrame::GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) the index of a variable not found in the method's original metadata, all metadata for the module is updated to a snapshot matching the current state of the process.</span></span> <span data-ttu-id="61b62-118">Innymi słowy, za pomocą `LegacyCompatPolicy` debuger może być wyświetlona żadnego, niektórych lub wszystkich aktualizacje dostępne metadane, w zależności od tego, w jaki sposób używa innych części niezarządzanego interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="61b62-118">In other words, with the `LegacyCompatPolicy` option, the debugger might see none, some, or all of the available metadata updates, depending on how it uses other parts of the unmanaged debugging API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61b62-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61b62-119">Requirements</span></span>  
 <span data-ttu-id="61b62-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61b62-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61b62-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61b62-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61b62-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61b62-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61b62-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61b62-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61b62-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61b62-124">See also</span></span>

- [<span data-ttu-id="61b62-125">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="61b62-125">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="61b62-126">SetWriteableMetadataUpdateMode, metoda</span><span class="sxs-lookup"><span data-stu-id="61b62-126">SetWriteableMetadataUpdateMode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
