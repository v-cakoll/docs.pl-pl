---
title: "IMetaDataImport2::GetPEKind — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetPEKind
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e8dc31877ba3550fa8faf610b831dfd2e7b313ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="71f20-102">IMetaDataImport2::GetPEKind — Metoda</span><span class="sxs-lookup"><span data-stu-id="71f20-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="71f20-103">Pobiera wartość identyfikujący rodzaj kod przenośny plik wykonywalny (PE) pliku, zwykle biblioteki DLL lub EXE pliku, który jest zdefiniowany w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="71f20-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71f20-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="71f20-104">Syntax</span></span>  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71f20-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="71f20-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="71f20-106">[out] Wskaźnik do wartości [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) wyliczenie opisujące pliku PE.</span><span class="sxs-lookup"><span data-stu-id="71f20-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="71f20-107">[out] Wskaźnik do wartość, która identyfikuje Architektura maszyny.</span><span class="sxs-lookup"><span data-stu-id="71f20-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="71f20-108">W następnej sekcji prawidłowych wartości.</span><span class="sxs-lookup"><span data-stu-id="71f20-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71f20-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71f20-109">Remarks</span></span>  
 <span data-ttu-id="71f20-110">Wartość przywołana przez `pdwMachine` parametr może być jedną z następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="71f20-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="71f20-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="71f20-111">Value</span></span>|<span data-ttu-id="71f20-112">Architektura komputera</span><span class="sxs-lookup"><span data-stu-id="71f20-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="71f20-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="71f20-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="71f20-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="71f20-114">0x014C</span></span>|<span data-ttu-id="71f20-115">x86</span><span class="sxs-lookup"><span data-stu-id="71f20-115">x86</span></span>|  
|<span data-ttu-id="71f20-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="71f20-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="71f20-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="71f20-117">0x0200</span></span>|<span data-ttu-id="71f20-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="71f20-118">Intel IPF</span></span>|  
|<span data-ttu-id="71f20-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="71f20-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="71f20-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="71f20-120">0x8664</span></span>|<span data-ttu-id="71f20-121">X64</span><span class="sxs-lookup"><span data-stu-id="71f20-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="71f20-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="71f20-122">Requirements</span></span>  
 <span data-ttu-id="71f20-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71f20-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71f20-124">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="71f20-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="71f20-125">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="71f20-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="71f20-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71f20-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71f20-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71f20-127">See Also</span></span>  
 [<span data-ttu-id="71f20-128">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="71f20-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="71f20-129">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="71f20-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="71f20-130">CorPEKind, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="71f20-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
