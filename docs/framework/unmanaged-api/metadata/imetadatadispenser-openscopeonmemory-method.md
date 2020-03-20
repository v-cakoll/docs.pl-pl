---
title: IMetaDataDispenser::OpenScopeOnMemory — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
ms.openlocfilehash: 492c37540ad68b5b134520218eedc59013c68519
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175931"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="bc2ad-102">IMetaDataDispenser::OpenScopeOnMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="bc2ad-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="bc2ad-103">Otwiera obszar pamięci zawierający istniejące metadane.</span><span class="sxs-lookup"><span data-stu-id="bc2ad-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="bc2ad-104">Oznacza to, że ta metoda otwiera określony obszar pamięci, w którym istniejące dane są traktowane jako metadane.</span><span class="sxs-lookup"><span data-stu-id="bc2ad-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc2ad-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc2ad-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,
    [in]  ULONG       cbData,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc2ad-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc2ad-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="bc2ad-107">[w] Wskaźnik określający adres początkowy obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="bc2ad-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="bc2ad-108">[w] Rozmiar obszaru pamięci w bajtach.</span><span class="sxs-lookup"><span data-stu-id="bc2ad-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="bc2ad-109">[w] Wartość [wyliczenia CorOpenFlags,](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) aby określić tryb (odczyt, zapis i tak dalej) do otwarcia.</span><span class="sxs-lookup"><span data-stu-id="bc2ad-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="bc2ad-110">[w] Identyfikator żądanego interfejsu metadanych do zwrócona; wywołujący użyje interfejsu do importowania (odczytu) lub emitowania (zapisu) metadanych.</span><span class="sxs-lookup"><span data-stu-id="bc2ad-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="bc2ad-111">Wartość `riid` musi określać jeden z interfejsów "import" lub "emituj".</span><span class="sxs-lookup"><span data-stu-id="bc2ad-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="bc2ad-112">Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 lub IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="bc2ad-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="bc2ad-113">[na zewnątrz] Wskaźnik do zwróconego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="bc2ad-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc2ad-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc2ad-114">Remarks</span></span>  
 <span data-ttu-id="bc2ad-115">Kopię metadanych w pamięci można zbadać przy użyciu metod z jednego z interfejsów "importuj" lub dodać do przy użyciu metod z jednego z interfejsów "emituj".</span><span class="sxs-lookup"><span data-stu-id="bc2ad-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="bc2ad-116">Metoda `OpenScopeOnMemory` jest podobna do [metody IMetaDataDispenser::OpenScope,](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) z tą różnicą, że metadane będące przedmiotem zainteresowania już istnieją w pamięci, a nie w pliku na dysku.</span><span class="sxs-lookup"><span data-stu-id="bc2ad-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="bc2ad-117">Jeśli obszar docelowy pamięci nie zawiera metadanych wspólnego środowiska `OpenScopeOnMemory` wykonawczego języka (CLR), metoda zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="bc2ad-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc2ad-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc2ad-118">Requirements</span></span>  
 <span data-ttu-id="bc2ad-119">**Platforma:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc2ad-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc2ad-120">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="bc2ad-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bc2ad-121">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bc2ad-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bc2ad-122">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc2ad-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc2ad-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc2ad-123">See also</span></span>

- [<span data-ttu-id="bc2ad-124">IMetaDataDispenser — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bc2ad-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="bc2ad-125">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc2ad-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="bc2ad-126">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bc2ad-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="bc2ad-127">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bc2ad-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="bc2ad-128">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bc2ad-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="bc2ad-129">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc2ad-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="bc2ad-130">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bc2ad-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bc2ad-131">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc2ad-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
