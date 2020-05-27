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
ms.openlocfilehash: 021ef8de602d6dd928f49e69e36f8d4a61425745
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008368"
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="137eb-102">IMetaDataDispenser::DefineScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="137eb-102">IMetaDataDispenser::DefineScope Method</span></span>
<span data-ttu-id="137eb-103">Tworzy nowy obszar w pamięci, w którym można tworzyć nowe metadane.</span><span class="sxs-lookup"><span data-stu-id="137eb-103">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="137eb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="137eb-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="137eb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="137eb-105">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="137eb-106">podczas Identyfikator CLSID wersji struktur metadanych, które mają zostać utworzone.</span><span class="sxs-lookup"><span data-stu-id="137eb-106">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="137eb-107">Ta wartość musi być CLSID_CorMetaDataRuntime dla .NET Framework wersja 2,0.</span><span class="sxs-lookup"><span data-stu-id="137eb-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="137eb-108">podczas Flagi określające opcje.</span><span class="sxs-lookup"><span data-stu-id="137eb-108">[in] Flags that specify options.</span></span> <span data-ttu-id="137eb-109">Ta wartość musi być równa zero dla .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="137eb-109">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="137eb-110">podczas Identyfikator IID żądanego interfejsu metadanych do zwrócenia; Obiekt wywołujący użyje interfejsu do utworzenia nowych metadanych.</span><span class="sxs-lookup"><span data-stu-id="137eb-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="137eb-111">Wartość `riid` musi określać jeden z interfejsów "Emituj".</span><span class="sxs-lookup"><span data-stu-id="137eb-111">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="137eb-112">Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit lub IID_IMetaDataEmit2.</span><span class="sxs-lookup"><span data-stu-id="137eb-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="137eb-113">określoną Wskaźnik do zwracanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="137eb-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="137eb-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="137eb-114">Remarks</span></span>  
 <span data-ttu-id="137eb-115">`DefineScope`tworzy zestaw tabel metadanych w pamięci, generuje unikatowy identyfikator GUID (identyfikator wersji modułu lub MVID) dla metadanych i tworzy wpis w tabeli modułów dla wyemitowanej jednostki kompilacji.</span><span class="sxs-lookup"><span data-stu-id="137eb-115">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="137eb-116">Można dołączać atrybuty do zakresu metadanych jako całości przy użyciu metody [IMetaDataEmit:: SetModuleProps —](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) lub [IMetaDataEmit::D efinecustomattribute](imetadataemit-definecustomattribute-method.md) , zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="137eb-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="137eb-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="137eb-117">Requirements</span></span>  
 <span data-ttu-id="137eb-118">**Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="137eb-118">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="137eb-119">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="137eb-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="137eb-120">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="137eb-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="137eb-121">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="137eb-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="137eb-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="137eb-122">See also</span></span>

- [<span data-ttu-id="137eb-123">IMetaDataDispenser — Interfejs</span><span class="sxs-lookup"><span data-stu-id="137eb-123">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="137eb-124">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="137eb-124">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="137eb-125">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="137eb-125">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="137eb-126">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="137eb-126">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="137eb-127">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="137eb-127">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
