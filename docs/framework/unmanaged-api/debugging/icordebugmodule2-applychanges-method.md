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
ms.openlocfilehash: 5a406e945a67352bc7f126b40bd56f4a11dd693b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="cf135-102">ICorDebugModule2::ApplyChanges — Metoda</span><span class="sxs-lookup"><span data-stu-id="cf135-102">ICorDebugModule2::ApplyChanges Method</span></span>
<span data-ttu-id="cf135-103">Stosuje zmiany w metadanych i zmian w kodzie języka pośredniego (MSIL) firmy Microsoft do uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="cf135-103">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf135-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf135-104">Syntax</span></span>  
  
```  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf135-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf135-105">Parameters</span></span>  
 `cbMetadata`  
 <span data-ttu-id="cf135-106">[in] Rozmiar w bajtach metadanych delta.</span><span class="sxs-lookup"><span data-stu-id="cf135-106">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="cf135-107">[in] Bufor zawierający metadane delta.</span><span class="sxs-lookup"><span data-stu-id="cf135-107">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="cf135-108">Adres buforu jest zwracana z [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="cf135-108">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="cf135-109">Względne wirtualnych adresów (RVAs) w metadanych powinna być określona względem początku kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="cf135-109">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="cf135-110">[in] Rozmiar w bajtach różnicowych kod MSIL.</span><span class="sxs-lookup"><span data-stu-id="cf135-110">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="cf135-111">[in] Buforu, który zawiera zaktualizowanego kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="cf135-111">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf135-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cf135-112">Remarks</span></span>  
 <span data-ttu-id="cf135-113">`pbMetadata` Parametru jest w formacie metadanych delta specjalnych (jak wyjściowych przez [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span><span class="sxs-lookup"><span data-stu-id="cf135-113">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="cf135-114">`pbMetadata` Trwa poprzednie metadanych jako podstawa oraz opis poszczególnych zmian do zastosowania do tej bazy.</span><span class="sxs-lookup"><span data-stu-id="cf135-114">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="cf135-115">Z kolei `pbIL[`] parametr zawiera nowe MSIL dla zaktualizowanej metody i ma całkowicie zastąpić poprzednie MSIL dla tej metody</span><span class="sxs-lookup"><span data-stu-id="cf135-115">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="cf135-116">Gdy delta MSIL i metadanych zostały utworzone w pamięci debugera, debuger wywołuje `ApplyChanges` Aby wysłać zmiany do środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="cf135-116">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="cf135-117">Środowisko uruchomieniowe aktualizuje jego tabele metadanych, umieszcza nowe MSIL w procesie i konfiguruje just in time (JIT) zbiór nowych MSIL.</span><span class="sxs-lookup"><span data-stu-id="cf135-117">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="cf135-118">Podczas zmiany zostały zastosowane, debuger powinien wywoływać [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) do przygotowania do następnej sesji edytowania.</span><span class="sxs-lookup"><span data-stu-id="cf135-118">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="cf135-119">Debuger może następnie kontynuować proces.</span><span class="sxs-lookup"><span data-stu-id="cf135-119">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="cf135-120">Zawsze, gdy debuger wywołuje `ApplyChanges` na module, który ma metadane zmian, należy także wywołać [IMetaDataEmit::ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) metadanymi zmian na wszystkich jego kopie metadanych tego modułu, z wyjątkiem kopii używany do wysyłania zmiany.</span><span class="sxs-lookup"><span data-stu-id="cf135-120">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="cf135-121">Jeśli kopia metadanych jakiś sposób staje się poza synchronizacja z metadanymi rzeczywiste debuger zawsze wyrzucać tej kopii i uzyskać nową kopię.</span><span class="sxs-lookup"><span data-stu-id="cf135-121">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="cf135-122">Jeśli `ApplyChanges` metoda zawiedzie, debugowania sesja jest w nieprawidłowym stanie i musi zostać ponownie uruchomione.</span><span class="sxs-lookup"><span data-stu-id="cf135-122">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf135-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cf135-123">Requirements</span></span>  
 <span data-ttu-id="cf135-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf135-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf135-125">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf135-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf135-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf135-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf135-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf135-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
