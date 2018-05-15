---
title: Metoda ICorDebugProcess7::SetWriteableMetadataUpdateMode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a67f93a3f3f75b89bc3f0240995471bc0bf44992
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="6c252-102">Metoda ICorDebugProcess7::SetWriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="6c252-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>
<span data-ttu-id="6c252-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="6c252-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6c252-104">Określa, jak debuger obsługuje aktualizacje w pamięci do metadanych w ramach procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="6c252-104">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c252-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c252-105">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c252-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c252-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="6c252-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) wartości wyliczenia, która określa, czy w pamięci aktualizacji metadanych w procesie docelowym są widoczne (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) lub nie jest widoczny (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) do debugera.</span><span class="sxs-lookup"><span data-stu-id="6c252-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c252-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6c252-108">Remarks</span></span>  
 <span data-ttu-id="6c252-109">Aktualizacji metadanych proces docelowy mogą pochodzić z Edytuj i Kontynuuj, profilera, lub <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6c252-109">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c252-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c252-110">Requirements</span></span>  
 <span data-ttu-id="6c252-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c252-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c252-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c252-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c252-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c252-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c252-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c252-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c252-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6c252-115">See Also</span></span>  
 [<span data-ttu-id="6c252-116">ICorDebugProcess7, interfejs</span><span class="sxs-lookup"><span data-stu-id="6c252-116">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 [<span data-ttu-id="6c252-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6c252-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
