---
title: ICorDebugModule2::ApplyChanges — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ApplyChanges
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab0e28bd21b66f370a1a1e82359fe474574fd7bb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481586"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="2bb4e-102">ICorDebugModule2::ApplyChanges — Metoda</span><span class="sxs-lookup"><span data-stu-id="2bb4e-102">ICorDebugModule2::ApplyChanges Method</span></span>
<span data-ttu-id="2bb4e-103">Ma zastosowanie zmian w metadanych i zmiany w kodzie języka intermediate language (MSIL) firmy Microsoft do uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="2bb4e-103">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bb4e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2bb4e-104">Syntax</span></span>  
  
```  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bb4e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2bb4e-105">Parameters</span></span>  
 `cbMetadata`  
 <span data-ttu-id="2bb4e-106">[in] Rozmiar w bajtach metadanych delta.</span><span class="sxs-lookup"><span data-stu-id="2bb4e-106">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="2bb4e-107">[in] Bufor, który zawiera metadane delta.</span><span class="sxs-lookup"><span data-stu-id="2bb4e-107">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="2bb4e-108">Adres buforu jest zwracana z [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2bb4e-108">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="2bb4e-109">Względnych adresów wirtualnych (RVA) w metadanych powinna być określona względem początku kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="2bb4e-109">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="2bb4e-110">[in] Rozmiar w bajtach, zmian kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="2bb4e-110">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="2bb4e-111">[in] Bufor, który zawiera zaktualizowany kod MSIL.</span><span class="sxs-lookup"><span data-stu-id="2bb4e-111">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bb4e-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2bb4e-112">Remarks</span></span>  
 <span data-ttu-id="2bb4e-113">`pbMetadata` Parametr jest w formacie metadanych specjalne różnicowej (jako dane wyjściowe przez [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span><span class="sxs-lookup"><span data-stu-id="2bb4e-113">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="2bb4e-114">`pbMetadata` Trwa poprzedniego metadanych jako podstawa oraz opis poszczególnych zmian do zastosowania do tej bazy.</span><span class="sxs-lookup"><span data-stu-id="2bb4e-114">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="2bb4e-115">Z kolei `pbIL[`] parametr zawiera nowy język MSIL dla zaktualizowanej metody i mają na celu całkowitego zastąpienia poprzedniego MSIL dla tej metody</span><span class="sxs-lookup"><span data-stu-id="2bb4e-115">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="2bb4e-116">Gdy delta MSIL i metadane zostały utworzone w pamięci w debugerze, debuger wywołuje `ApplyChanges` wysyła zmiany na środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="2bb4e-116">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="2bb4e-117">Środowisko uruchomieniowe aktualizuje jego tabel metadanych, umieszcza nowe MSIL w procesie i konfiguruje kompilacji just-in-time (JIT) nowego języka MSIL.</span><span class="sxs-lookup"><span data-stu-id="2bb4e-117">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="2bb4e-118">Jeśli zmiany zostały zastosowane, należy wywołać debugera [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) Aby przygotować się do edycji następnej sesji.</span><span class="sxs-lookup"><span data-stu-id="2bb4e-118">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="2bb4e-119">Debuger może następnie kontynuować procesu.</span><span class="sxs-lookup"><span data-stu-id="2bb4e-119">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="2bb4e-120">Zawsze, gdy wywołuje debugera `ApplyChanges` w module, który zawiera metadane delta, powinien także wywołać [IMetaDataEmit::ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) metadanymi zmian na wszystkie kopie w metadanych tego modułu, z wyjątkiem kopiowania używany do emitowania zmiany.</span><span class="sxs-lookup"><span data-stu-id="2bb4e-120">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="2bb4e-121">Jeśli kopia metadanych jakiś sposób stanie się poza zsynchronizowane z metadanymi rzeczywiste, debuger zawsze możesz Pozbywać się kopii i uzyskać nową kopię.</span><span class="sxs-lookup"><span data-stu-id="2bb4e-121">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="2bb4e-122">Jeśli `ApplyChanges` metoda nie powiedzie się, debugowania sesji jest w nieprawidłowym stanie i musi zostać uruchomiony ponownie.</span><span class="sxs-lookup"><span data-stu-id="2bb4e-122">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bb4e-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2bb4e-123">Requirements</span></span>  
 <span data-ttu-id="2bb4e-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bb4e-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bb4e-125">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2bb4e-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2bb4e-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bb4e-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bb4e-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bb4e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
