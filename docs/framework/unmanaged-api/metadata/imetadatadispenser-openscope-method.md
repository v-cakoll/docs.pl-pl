---
title: IMetaDataDispenser::OpenScope — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
ms.openlocfilehash: 5185fb6663910c85ce5dae1225b9b10c5dd8bb28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175944"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="e5d0c-102">IMetaDataDispenser::OpenScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="e5d0c-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="e5d0c-103">Otwiera istniejący plik na dysku i mapuje jego metadane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5d0c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5d0c-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5d0c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5d0c-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="e5d0c-106">[w] Nazwa pliku, który ma zostać otwarty.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="e5d0c-107">Plik musi zawierać metadane wspólnego środowiska wykonawczego języka (CLR).</span><span class="sxs-lookup"><span data-stu-id="e5d0c-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="e5d0c-108">[w] Wartość [wyliczenia CorOpenFlags,](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) aby określić tryb (odczyt, zapis i tak dalej) do otwarcia.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-108">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="e5d0c-109">[w] Identyfikator żądanego interfejsu metadanych do zwrócona; wywołujący użyje interfejsu do importowania (odczytu) lub emitowania (zapisu) metadanych.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="e5d0c-110">Wartość `riid` musi określać jeden z interfejsów "import" lub "emituj".</span><span class="sxs-lookup"><span data-stu-id="e5d0c-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="e5d0c-111">Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 lub IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="e5d0c-112">[na zewnątrz] Wskaźnik do zwróconego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5d0c-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5d0c-113">Remarks</span></span>  
 <span data-ttu-id="e5d0c-114">Kopię metadanych w pamięci można zbadać przy użyciu metod z jednego z interfejsów "importuj" lub dodać do przy użyciu metod z jednego z interfejsów "emituj".</span><span class="sxs-lookup"><span data-stu-id="e5d0c-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="e5d0c-115">Jeśli plik docelowy nie zawiera metadanych CLR, metoda zakończy się niepowodzeniem. `OpenScope`</span><span class="sxs-lookup"><span data-stu-id="e5d0c-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="e5d0c-116">W .NET Framework w wersji 1.0 i wersji 1.1, jeśli zakres jest otwarty z `dwOpenFlags` zestawem doread, kwalifikuje się do udostępniania.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="e5d0c-117">Oznacza to, że `OpenScope` jeśli kolejne wywołania przekazania w nazwie pliku, który został wcześniej otwarty, istniejący zakres jest ponownie i nowy zestaw struktur danych nie jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="e5d0c-118">Jednak problemy mogą pojawić się z powodu tego udostępniania.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="e5d0c-119">W .NET Framework w wersji 2.0 `dwOpenFlags` zakresy otwarte z zestawem doread nie są już współużytkowane.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="e5d0c-120">Użyj ofReadOnly wartość, aby umożliwić zakres do udostępnienia.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="e5d0c-121">Gdy zakres jest współużytkowany, kwerendy, które używają interfejsów metadanych "odczyt/zapis" zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5d0c-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5d0c-122">Requirements</span></span>  
 <span data-ttu-id="e5d0c-123">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5d0c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5d0c-124">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="e5d0c-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5d0c-125">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e5d0c-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5d0c-126">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5d0c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5d0c-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5d0c-127">See also</span></span>

- [<span data-ttu-id="e5d0c-128">IMetaDataDispenser — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e5d0c-128">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="e5d0c-129">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5d0c-129">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="e5d0c-130">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e5d0c-130">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="e5d0c-131">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e5d0c-131">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="e5d0c-132">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e5d0c-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e5d0c-133">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5d0c-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="e5d0c-134">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e5d0c-134">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e5d0c-135">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5d0c-135">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
