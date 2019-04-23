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
ms.openlocfilehash: 94e2f1c13c91c50daa5730898adf0aedf00f6579
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092620"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="bc9ec-102">Metoda ICorDebugProcess7::SetWriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="bc9ec-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>
<span data-ttu-id="bc9ec-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="bc9ec-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="bc9ec-104">Określa, jak debuger obsługuje aktualizacje w pamięci do metadanych w ramach procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="bc9ec-104">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc9ec-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc9ec-105">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc9ec-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc9ec-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="bc9ec-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) wartości wyliczenia, która określa, czy aktualizacje metadanych w procesie docelowym w pamięci są widoczne (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) lub nie jest widoczny (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) do debugera.</span><span class="sxs-lookup"><span data-stu-id="bc9ec-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc9ec-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc9ec-108">Remarks</span></span>  
 <span data-ttu-id="bc9ec-109">Aktualizacji metadanych procesu docelowego mogą pochodzić z Edit and Continue, program profilujący, lub <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bc9ec-109">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc9ec-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc9ec-110">Requirements</span></span>  
 <span data-ttu-id="bc9ec-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc9ec-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc9ec-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc9ec-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc9ec-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc9ec-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc9ec-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc9ec-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc9ec-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc9ec-115">See also</span></span>

- [<span data-ttu-id="bc9ec-116">ICorDebugProcess7, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc9ec-116">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)
- [<span data-ttu-id="bc9ec-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bc9ec-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
