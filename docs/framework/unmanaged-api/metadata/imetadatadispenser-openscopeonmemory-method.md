---
title: IMetaDataDispenser::OpenScopeOnMemory — Metoda
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: reference
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
caps.latest.revision: 11
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1d206863736387df04157ed752a6269b22a884b9
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="91d67-102">IMetaDataDispenser::OpenScopeOnMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="91d67-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="91d67-103">Otwiera to obszar pamięci, która zawiera istniejące metadane.</span><span class="sxs-lookup"><span data-stu-id="91d67-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="91d67-104">Oznacza to ta metoda powoduje otwarcie określonego obszaru pamięci, w którym istniejących danych jest traktowany jak metadanych.</span><span class="sxs-lookup"><span data-stu-id="91d67-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91d67-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="91d67-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="91d67-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="91d67-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="91d67-107">[in] Wskaźnik, który określa adres początkowy obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="91d67-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="91d67-108">[in] Rozmiar obszaru pamięci w bajtach.</span><span class="sxs-lookup"><span data-stu-id="91d67-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="91d67-109">[in] Wartość [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) wyliczeniu, aby określić otwierania trybu (do odczytu, zapisu i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="91d67-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="91d67-110">[in] Uzyskanie identyfikatora IID interfejsu odpowiednie metadane zwrócone; obiekt wywołujący będą używać interfejsu do zaimportowania (odczyt) albo Emituj metadanych (Zapisz).</span><span class="sxs-lookup"><span data-stu-id="91d67-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="91d67-111">Wartość `riid` należy określić jeden z interfejsów "import" lub "Emituj".</span><span class="sxs-lookup"><span data-stu-id="91d67-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="91d67-112">Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 lub IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="91d67-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="91d67-113">[out] Wskaźnik do interfejsu zwrócony.</span><span class="sxs-lookup"><span data-stu-id="91d67-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91d67-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91d67-114">Remarks</span></span>  
 <span data-ttu-id="91d67-115">Przy użyciu metod z jednego z interfejsów "import", lub dodać do przy użyciu metod z jednego z interfejsów "Emituj" można tworzyć zapytania w pamięci kopie metadanych.</span><span class="sxs-lookup"><span data-stu-id="91d67-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="91d67-116">`OpenScopeOnMemory` Metoda jest podobna do [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) metody, z wyjątkiem tego, że metadane odsetek już istnieje w pamięci, a nie w pliku na dysku.</span><span class="sxs-lookup"><span data-stu-id="91d67-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="91d67-117">Jeśli docelowy obszar pamięci nie zawiera wspólnych metadanych języka wspólnego (CLR) `OpenScopeOnMemory` metoda zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="91d67-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91d67-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91d67-118">Requirements</span></span>  
 <span data-ttu-id="91d67-119">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91d67-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91d67-120">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="91d67-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="91d67-121">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="91d67-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="91d67-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91d67-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91d67-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91d67-123">See Also</span></span>  
 [<span data-ttu-id="91d67-124">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="91d67-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="91d67-125">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="91d67-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="91d67-126">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="91d67-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="91d67-127">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="91d67-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="91d67-128">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="91d67-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="91d67-129">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="91d67-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="91d67-130">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="91d67-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="91d67-131">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="91d67-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
