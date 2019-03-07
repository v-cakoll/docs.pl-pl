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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8462f0d518307ad271c31e712b46c784c67974a3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498487"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="4d555-102">IMetaDataDispenser::OpenScopeOnMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="4d555-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="4d555-103">Zostanie otwarty obszar pamięci, który zawiera istniejące metadane.</span><span class="sxs-lookup"><span data-stu-id="4d555-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="4d555-104">Oznacza to ta metoda powoduje otwarcie określonego obszaru pamięci, w którym istniejących danych jest traktowana jako metadanych.</span><span class="sxs-lookup"><span data-stu-id="4d555-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d555-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d555-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d555-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d555-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="4d555-107">[in] Wskaźnik Określa adres początkowy obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="4d555-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="4d555-108">[in] Rozmiar obszaru pamięci w bajtach.</span><span class="sxs-lookup"><span data-stu-id="4d555-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="4d555-109">[in] Wartość [coropenflags —](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) wyliczeniu, aby określić tryb (Odczyt, zapis i tak dalej) otwierania.</span><span class="sxs-lookup"><span data-stu-id="4d555-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="4d555-110">[in] IID interfejsu żądaną metadanych ma zostać zwrócona; obiekt wywołujący użyje interfejsu do zaimportowania (odczyt) lub emitować metadane (Zapisz).</span><span class="sxs-lookup"><span data-stu-id="4d555-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="4d555-111">Wartość `riid` należy określić jeden z interfejsów "import" lub "Dodaj".</span><span class="sxs-lookup"><span data-stu-id="4d555-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="4d555-112">Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 lub IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="4d555-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="4d555-113">[out] Wskaźnik do interfejsu zwrócone.</span><span class="sxs-lookup"><span data-stu-id="4d555-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d555-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d555-114">Remarks</span></span>  
 <span data-ttu-id="4d555-115">Kopia w pamięci metadanych mogą być przeszukiwane przy użyciu metod z jednego z interfejsów "import" lub dodane do przy użyciu metod z jednego z interfejsów "Dodaj".</span><span class="sxs-lookup"><span data-stu-id="4d555-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="4d555-116">`OpenScopeOnMemory` Metoda jest podobna do [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) metody, z tą różnicą, że metadane zainteresowania już istnieje w pamięci, a nie w pliku na dysku.</span><span class="sxs-lookup"><span data-stu-id="4d555-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="4d555-117">Jeśli obszar pamięci, docelowy nie zawiera wspólnych metadanych języka wspólnego (CLR) `OpenScopeOnMemory` metoda zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="4d555-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d555-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d555-118">Requirements</span></span>  
 <span data-ttu-id="4d555-119">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d555-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d555-120">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4d555-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d555-121">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4d555-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4d555-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d555-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d555-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d555-123">See also</span></span>
- [<span data-ttu-id="4d555-124">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d555-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="4d555-125">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d555-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="4d555-126">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d555-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="4d555-127">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d555-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="4d555-128">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d555-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4d555-129">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d555-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="4d555-130">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d555-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4d555-131">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d555-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
