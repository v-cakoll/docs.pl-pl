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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6e157c758b472ea89e21c1ed1ba8c17693c20a3d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777792"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="e3ede-102">IMetaDataDispenser::OpenScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="e3ede-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="e3ede-103">Otwiera istniejący plik na dysku i mapuje jego metadane do pamięci.</span><span class="sxs-lookup"><span data-stu-id="e3ede-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3ede-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3ede-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3ede-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3ede-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="e3ede-106">[in] Nazwa pliku, który ma zostać otwarty.</span><span class="sxs-lookup"><span data-stu-id="e3ede-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="e3ede-107">Plik musi zawierać wspólnego języka wspólnego (CLR) metadanych.</span><span class="sxs-lookup"><span data-stu-id="e3ede-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="e3ede-108">[in] Wartość [coropenflags —](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) wyliczeniu, aby określić tryb (Odczyt, zapis i tak dalej) otwierania.</span><span class="sxs-lookup"><span data-stu-id="e3ede-108">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="e3ede-109">[in] IID interfejsu żądaną metadanych ma zostać zwrócona; obiekt wywołujący użyje interfejsu do zaimportowania (odczyt) lub emitować metadane (Zapisz).</span><span class="sxs-lookup"><span data-stu-id="e3ede-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="e3ede-110">Wartość `riid` należy określić jeden z interfejsów "import" lub "Dodaj".</span><span class="sxs-lookup"><span data-stu-id="e3ede-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="e3ede-111">Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 lub IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="e3ede-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="e3ede-112">[out] Wskaźnik do interfejsu zwrócone.</span><span class="sxs-lookup"><span data-stu-id="e3ede-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3ede-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3ede-113">Remarks</span></span>  
 <span data-ttu-id="e3ede-114">Kopia w pamięci metadanych mogą być przeszukiwane przy użyciu metod z jednego z interfejsów "import" lub dodane do przy użyciu metod z jednego z interfejsów "Dodaj".</span><span class="sxs-lookup"><span data-stu-id="e3ede-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="e3ede-115">Jeśli plik docelowy nie zawiera metadanych CLR `OpenScope` metoda zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="e3ede-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="e3ede-116">W programie .NET Framework w wersji 1.0 i w wersji 1.1, jeśli zakres jest otwierany przy użyciu `dwOpenFlags` wartość ofRead, jest uprawniony do udostępniania.</span><span class="sxs-lookup"><span data-stu-id="e3ede-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="e3ede-117">Oznacza to jeśli jest to kolejne wywołania `OpenScope` — dostęp próbny nazwę pliku, który był wcześniej otwarty, istniejący zakres jest ponownie i nie powstaje nowy zestaw struktur danych.</span><span class="sxs-lookup"><span data-stu-id="e3ede-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="e3ede-118">Jednak problemy mogą wystąpić z powodu udostępnianie to.</span><span class="sxs-lookup"><span data-stu-id="e3ede-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="e3ede-119">W programie .NET Framework 2.0, zakresy otwartej z `dwOpenFlags` równa ofRead nie będą udostępniane.</span><span class="sxs-lookup"><span data-stu-id="e3ede-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="e3ede-120">Użyj wartości ofReadOnly, aby zezwolić na zakres, który ma zostać udostępniony.</span><span class="sxs-lookup"><span data-stu-id="e3ede-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="e3ede-121">Po udostępnieniu zakres zapytań, które używają "odczytu/zapisu" interfejsy metadanych nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="e3ede-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3ede-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3ede-122">Requirements</span></span>  
 <span data-ttu-id="e3ede-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3ede-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3ede-124">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="e3ede-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e3ede-125">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e3ede-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e3ede-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3ede-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3ede-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3ede-127">See also</span></span>

- [<span data-ttu-id="e3ede-128">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3ede-128">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="e3ede-129">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3ede-129">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="e3ede-130">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3ede-130">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="e3ede-131">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3ede-131">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="e3ede-132">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3ede-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e3ede-133">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3ede-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="e3ede-134">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3ede-134">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e3ede-135">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3ede-135">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
