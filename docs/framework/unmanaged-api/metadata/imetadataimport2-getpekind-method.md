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
ms.openlocfilehash: 9fc963f38a845db67bb5b5d377ecabf9a40c359f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="390a0-102">IMetaDataImport2::GetPEKind — Metoda</span><span class="sxs-lookup"><span data-stu-id="390a0-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="390a0-103">Pobiera wartość identyfikujący rodzaj kod przenośny plik wykonywalny (PE) pliku, zwykle biblioteki DLL lub EXE pliku, który jest zdefiniowany w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="390a0-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="390a0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="390a0-104">Syntax</span></span>  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="390a0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="390a0-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="390a0-106">[out] Wskaźnik do wartości [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) wyliczenie opisujące pliku PE.</span><span class="sxs-lookup"><span data-stu-id="390a0-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="390a0-107">[out] Wskaźnik do wartość, która identyfikuje Architektura maszyny.</span><span class="sxs-lookup"><span data-stu-id="390a0-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="390a0-108">W następnej sekcji prawidłowych wartości.</span><span class="sxs-lookup"><span data-stu-id="390a0-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="390a0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="390a0-109">Remarks</span></span>  
 <span data-ttu-id="390a0-110">Wartość przywołana przez `pdwMachine` parametr może być jedną z następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="390a0-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="390a0-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="390a0-111">Value</span></span>|<span data-ttu-id="390a0-112">Architektura komputera</span><span class="sxs-lookup"><span data-stu-id="390a0-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="390a0-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="390a0-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="390a0-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="390a0-114">0x014C</span></span>|<span data-ttu-id="390a0-115">x86</span><span class="sxs-lookup"><span data-stu-id="390a0-115">x86</span></span>|  
|<span data-ttu-id="390a0-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="390a0-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="390a0-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="390a0-117">0x0200</span></span>|<span data-ttu-id="390a0-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="390a0-118">Intel IPF</span></span>|  
|<span data-ttu-id="390a0-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="390a0-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="390a0-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="390a0-120">0x8664</span></span>|<span data-ttu-id="390a0-121">x64</span><span class="sxs-lookup"><span data-stu-id="390a0-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="390a0-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="390a0-122">Requirements</span></span>  
 <span data-ttu-id="390a0-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="390a0-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="390a0-124">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="390a0-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="390a0-125">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="390a0-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="390a0-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="390a0-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="390a0-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="390a0-127">See Also</span></span>  
 [<span data-ttu-id="390a0-128">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="390a0-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="390a0-129">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="390a0-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="390a0-130">CorPEKind — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="390a0-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
