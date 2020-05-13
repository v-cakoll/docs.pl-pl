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
ms.openlocfilehash: 99824e9a7fd759fb30bfa377156fc28eb934a2b4
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212220"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="3009e-102">ICorDebugModule2::ApplyChanges — Metoda</span><span class="sxs-lookup"><span data-stu-id="3009e-102">ICorDebugModule2::ApplyChanges Method</span></span>
<span data-ttu-id="3009e-103">Stosuje zmiany w metadanych i zmiany w kodzie języka pośredniego firmy Microsoft (MSIL) do uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="3009e-103">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3009e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3009e-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3009e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3009e-105">Parameters</span></span>  
 `cbMetadata`  
 <span data-ttu-id="3009e-106">podczas Rozmiar metadanych różnicowych w bajtach.</span><span class="sxs-lookup"><span data-stu-id="3009e-106">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="3009e-107">podczas Bufor zawierający metadane różnicowe.</span><span class="sxs-lookup"><span data-stu-id="3009e-107">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="3009e-108">Adres buforu jest zwracany z metody [IMetaDataEmit2:: SaveDeltaToMemory —](../metadata/imetadataemit2-savedeltatomemory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3009e-108">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="3009e-109">Względne adresy wirtualne (RVA) w metadanych powinny być względne względem początku kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="3009e-109">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="3009e-110">podczas Rozmiar (w bajtach) różnicowego kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="3009e-110">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="3009e-111">podczas Bufor zawierający zaktualizowany kod MSIL.</span><span class="sxs-lookup"><span data-stu-id="3009e-111">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3009e-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3009e-112">Remarks</span></span>  
 <span data-ttu-id="3009e-113">`pbMetadata`Parametr jest w specjalnym formacie metadanych różnicowych (jako dane wyjściowe przez [IMetaDataEmit2:: SaveDeltaToMemory —](../metadata/imetadataemit2-savedeltatomemory-method.md)).</span><span class="sxs-lookup"><span data-stu-id="3009e-113">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="3009e-114">`pbMetadata`Pobiera poprzednie metadane jako podstawowe i opisuje indywidualne zmiany, które mają zastosowanie do tej bazy.</span><span class="sxs-lookup"><span data-stu-id="3009e-114">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="3009e-115">Z kolei `pbIL[` parametr] zawiera nowe MSIL dla zaktualizowanej metody i ma na celu całkowite zamienienie poprzedniego MSIL dla tej metody</span><span class="sxs-lookup"><span data-stu-id="3009e-115">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="3009e-116">Po utworzeniu różnicowego MSIL i metadanych w pamięci debugera debuger wywołuje, `ApplyChanges` Aby wysłać zmiany do środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="3009e-116">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="3009e-117">Środowisko uruchomieniowe aktualizuje swoje tabele metadanych, umieszcza nowe MSIL w procesie i konfiguruje kompilację just-in-Time (JIT) nowej MSIL.</span><span class="sxs-lookup"><span data-stu-id="3009e-117">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="3009e-118">Po zastosowaniu zmian debuger powinien wywołać [IMetaDataEmit2:: ResetENCLog —](../metadata/imetadataemit2-resetenclog-method.md) , aby przygotować się do następnej sesji edytowania.</span><span class="sxs-lookup"><span data-stu-id="3009e-118">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="3009e-119">Debuger może następnie kontynuować proces.</span><span class="sxs-lookup"><span data-stu-id="3009e-119">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="3009e-120">Za każdym razem, gdy debuger wywołuje `ApplyChanges` moduł, który ma metadane różnicowe, powinien również wywołać [IMetaDataEmit:: ApplyEditAndContinue —](../metadata/imetadataemit-applyeditandcontinue-method.md) z tymi samymi metadanymi Delta we wszystkich kopiach metadanych tego modułu, z wyjątkiem kopii użytej do emisji zmian.</span><span class="sxs-lookup"><span data-stu-id="3009e-120">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="3009e-121">Jeśli kopia metadanych w jakiś sposób stanie się niezsynchronizowana z rzeczywistymi metadanymi, debuger zawsze może zgłosić tę kopię i uzyskać nową kopię.</span><span class="sxs-lookup"><span data-stu-id="3009e-121">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="3009e-122">Jeśli `ApplyChanges` Metoda zakończy się niepowodzeniem, sesja debugowania jest w nieprawidłowym stanie i musi zostać uruchomiona ponownie.</span><span class="sxs-lookup"><span data-stu-id="3009e-122">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3009e-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3009e-123">Requirements</span></span>  
 <span data-ttu-id="3009e-124">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3009e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3009e-125">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3009e-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3009e-126">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3009e-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3009e-127">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3009e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
