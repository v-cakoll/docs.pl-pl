---
title: IMetaDataDispenser::DefineScope — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
ms.openlocfilehash: 2f9325f3795262a0c33af02f87fc5d3a020658cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177632"
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="8a652-102">IMetaDataDispenser::DefineScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="8a652-102">IMetaDataDispenser::DefineScope Method</span></span>
<span data-ttu-id="8a652-103">Tworzy nowy obszar w pamięci, w którym można tworzyć nowe metadane.</span><span class="sxs-lookup"><span data-stu-id="8a652-103">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a652-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a652-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a652-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a652-105">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="8a652-106">[w] Identyfikator CLSID wersji struktur metadanych, które mają zostać utworzone.</span><span class="sxs-lookup"><span data-stu-id="8a652-106">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="8a652-107">Ta wartość musi być CLSID_CorMetaDataRuntime dla programu .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="8a652-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="8a652-108">[w] Flagi określające opcje.</span><span class="sxs-lookup"><span data-stu-id="8a652-108">[in] Flags that specify options.</span></span> <span data-ttu-id="8a652-109">Ta wartość musi wynosić zero dla programu .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="8a652-109">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="8a652-110">[w] Identyfikator żądanego interfejsu metadanych do zwrócona; wywołujący użyje interfejsu do utworzenia nowych metadanych.</span><span class="sxs-lookup"><span data-stu-id="8a652-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="8a652-111">Wartość `riid` musi określać jeden z interfejsów "emitować".</span><span class="sxs-lookup"><span data-stu-id="8a652-111">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="8a652-112">Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit lub IID_IMetaDataEmit2.</span><span class="sxs-lookup"><span data-stu-id="8a652-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="8a652-113">[na zewnątrz] Wskaźnik do zwróconego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8a652-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a652-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8a652-114">Remarks</span></span>  
 <span data-ttu-id="8a652-115">`DefineScope`tworzy zestaw tabel metadanych w pamięci, generuje unikatowy identyfikator GUID (identyfikator wersji modułu lub MVID) dla metadanych i tworzy wpis w tabeli modułów dla emitowanej jednostki kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8a652-115">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="8a652-116">Atrybuty można dołączyć do zakresu metadanych jako całości przy użyciu [metody IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) lub [IMetaDataEmit::DefineCustomAttribute.](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)</span><span class="sxs-lookup"><span data-stu-id="8a652-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a652-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a652-117">Requirements</span></span>  
 <span data-ttu-id="8a652-118">**Platforma:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a652-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a652-119">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="8a652-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a652-120">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8a652-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a652-121">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a652-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a652-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a652-122">See also</span></span>

- [<span data-ttu-id="8a652-123">IMetaDataDispenser — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8a652-123">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="8a652-124">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a652-124">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="8a652-125">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8a652-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="8a652-126">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8a652-126">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="8a652-127">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a652-127">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
