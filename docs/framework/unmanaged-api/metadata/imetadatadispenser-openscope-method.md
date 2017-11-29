---
title: "IMetaDataDispenser::OpenScope — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenser.OpenScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09c057f42bb849b89d78d2d32af6637640ad22ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="4df9d-102">IMetaDataDispenser::OpenScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="4df9d-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="4df9d-103">Otwiera istniejący plik na dysku, a następnie mapuje metadanych do pamięci.</span><span class="sxs-lookup"><span data-stu-id="4df9d-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4df9d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4df9d-104">Syntax</span></span>  
  
```  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4df9d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4df9d-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="4df9d-106">[in] Nazwa pliku, który ma zostać otwarty.</span><span class="sxs-lookup"><span data-stu-id="4df9d-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="4df9d-107">Plik musi zawierać wspólnych języka wspólnego (CLR) metadanych.</span><span class="sxs-lookup"><span data-stu-id="4df9d-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="4df9d-108">[in] Wartość [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) wyliczeniu, aby określić otwierania trybu (do odczytu, zapisu i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="4df9d-108">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="4df9d-109">[in] Uzyskanie identyfikatora IID interfejsu odpowiednie metadane zwrócone; obiekt wywołujący będą używać interfejsu do zaimportowania (odczyt) albo Emituj metadanych (Zapisz).</span><span class="sxs-lookup"><span data-stu-id="4df9d-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="4df9d-110">Wartość `riid` należy określić jeden z interfejsów "import" lub "Emituj".</span><span class="sxs-lookup"><span data-stu-id="4df9d-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="4df9d-111">Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 lub IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="4df9d-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="4df9d-112">[out] Wskaźnik do interfejsu zwrócony.</span><span class="sxs-lookup"><span data-stu-id="4df9d-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4df9d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4df9d-113">Remarks</span></span>  
 <span data-ttu-id="4df9d-114">Przy użyciu metod z jednego z interfejsów "import", lub dodać do przy użyciu metod z jednego z interfejsów "Emituj" można tworzyć zapytania w pamięci kopie metadanych.</span><span class="sxs-lookup"><span data-stu-id="4df9d-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="4df9d-115">Jeśli plik docelowy nie zawiera metadanych CLR `OpenScope` metoda zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="4df9d-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="4df9d-116">W programie .NET Framework w wersji 1.0 i 1.1, jeśli zakres wersji jest otwarty z `dwOpenFlags` wartość ofRead, jest uprawniona do udostępniania.</span><span class="sxs-lookup"><span data-stu-id="4df9d-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="4df9d-117">Oznacza to, że jeśli kolejnych wywołań `OpenScope` przebiegu nazwy pliku, który został uprzednio otwarty zostanie ponownie użyty istniejący zakres i nie jest tworzony nowy zestaw struktur danych.</span><span class="sxs-lookup"><span data-stu-id="4df9d-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="4df9d-118">Jednak problemy mogą wystąpić z powodu tego udostępniania.</span><span class="sxs-lookup"><span data-stu-id="4df9d-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="4df9d-119">W programie .NET Framework w wersji 2.0, zakresy otwarta z `dwOpenFlags` ustawioną ofRead nie będą udostępniane.</span><span class="sxs-lookup"><span data-stu-id="4df9d-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="4df9d-120">Użyj wartości ofReadOnly umożliwia zakresu do udostępnienia.</span><span class="sxs-lookup"><span data-stu-id="4df9d-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="4df9d-121">Po udostępnieniu zakres kwerendy używające "odczytu/zapisu" interfejsy metadanych nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="4df9d-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4df9d-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4df9d-122">Requirements</span></span>  
 <span data-ttu-id="4df9d-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4df9d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4df9d-124">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4df9d-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4df9d-125">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4df9d-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4df9d-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4df9d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4df9d-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4df9d-127">See Also</span></span>  
 [<span data-ttu-id="4df9d-128">IMetaDataDispenser — interfejs</span><span class="sxs-lookup"><span data-stu-id="4df9d-128">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="4df9d-129">IMetaDataDispenserEx — interfejs</span><span class="sxs-lookup"><span data-stu-id="4df9d-129">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="4df9d-130">IMetaDataAssemblyEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="4df9d-130">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="4df9d-131">IMetaDataAssemblyImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="4df9d-131">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="4df9d-132">IMetaDataEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="4df9d-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="4df9d-133">IMetaDataEmit2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="4df9d-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="4df9d-134">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="4df9d-134">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="4df9d-135">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="4df9d-135">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
