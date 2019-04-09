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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76a439effad9cb3f6dcdd232590cf2196ee7ab99
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101409"
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="e53dc-102">IMetaDataDispenser::DefineScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="e53dc-102">IMetaDataDispenser::DefineScope Method</span></span>
<span data-ttu-id="e53dc-103">Tworzy nowy obszar w pamięci, w którym można tworzyć nowe metadane.</span><span class="sxs-lookup"><span data-stu-id="e53dc-103">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e53dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e53dc-104">Syntax</span></span>  
  
```  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e53dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e53dc-105">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="e53dc-106">[in] Identyfikator CLSID wersję struktury metadanych, ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="e53dc-106">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="e53dc-107">Ta wartość musi być CLSID_CorMetaDataRuntime dla platformy .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="e53dc-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="e53dc-108">[in] Flagi, które określają opcje.</span><span class="sxs-lookup"><span data-stu-id="e53dc-108">[in] Flags that specify options.</span></span> <span data-ttu-id="e53dc-109">Ta wartość musi mieć wartość zero dla programu .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="e53dc-109">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="e53dc-110">[in] IID interfejsu żądaną metadanych ma zostać zwrócona; obiekt wywołujący użyje interfejsu można utworzyć nowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="e53dc-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="e53dc-111">Wartość `riid` należy określić jeden z interfejsów "Dodaj".</span><span class="sxs-lookup"><span data-stu-id="e53dc-111">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="e53dc-112">Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit lub IID_IMetaDataEmit2.</span><span class="sxs-lookup"><span data-stu-id="e53dc-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="e53dc-113">[out] Wskaźnik do interfejsu zwrócone.</span><span class="sxs-lookup"><span data-stu-id="e53dc-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e53dc-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e53dc-114">Remarks</span></span>  
 `DefineScope` <span data-ttu-id="e53dc-115">Tworzy zestaw tabel metadanych w pamięci, a następnie generuje unikatowy identyfikator GUID (identyfikator wersji modułu lub identyfikatora MVID) metadanych i tworzy wpis w tabeli modułu dla jednostki kompilacji jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="e53dc-115">creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="e53dc-116">Możesz dołączyć atrybuty do zakresu metadanych jako całość przy użyciu [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) lub [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) metodę, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="e53dc-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e53dc-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e53dc-117">Requirements</span></span>  
 <span data-ttu-id="e53dc-118">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e53dc-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e53dc-119">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="e53dc-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e53dc-120">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e53dc-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="e53dc-121">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e53dc-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e53dc-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e53dc-122">See also</span></span>

- [<span data-ttu-id="e53dc-123">IMetaDataDispenser — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e53dc-123">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="e53dc-124">IMetaDataDispenserEx — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e53dc-124">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="e53dc-125">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e53dc-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="e53dc-126">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e53dc-126">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e53dc-127">IMetaDataEmit2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e53dc-127">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
