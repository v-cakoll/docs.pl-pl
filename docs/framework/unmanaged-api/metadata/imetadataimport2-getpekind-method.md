---
title: IMetaDataImport2::GetPEKind — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ad18aaca1caef242832bbdae9a1094b2ef2d7be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572464"
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="7bfd8-102">IMetaDataImport2::GetPEKind — Metoda</span><span class="sxs-lookup"><span data-stu-id="7bfd8-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="7bfd8-103">Pobiera wartość identyfikujący rodzaj kodu w pliku wykonalnego (PE) pliku, zazwyczaj pliku DLL lub EXE, który jest zdefiniowany w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="7bfd8-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bfd8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7bfd8-104">Syntax</span></span>  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7bfd8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7bfd8-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="7bfd8-106">[out] Wskaźnik do wartości [corpekind —](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) wyliczenie opisujące pliku PE.</span><span class="sxs-lookup"><span data-stu-id="7bfd8-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="7bfd8-107">[out] Wskaźnik do wartość, która identyfikuje architektury maszyny.</span><span class="sxs-lookup"><span data-stu-id="7bfd8-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="7bfd8-108">Zobacz następną sekcję uzyskać odpowiednie wartości.</span><span class="sxs-lookup"><span data-stu-id="7bfd8-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bfd8-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7bfd8-109">Remarks</span></span>  
 <span data-ttu-id="7bfd8-110">Wartość przywołana przez `pdwMachine` parametr może być jedną z następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="7bfd8-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="7bfd8-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="7bfd8-111">Value</span></span>|<span data-ttu-id="7bfd8-112">Architektura komputera</span><span class="sxs-lookup"><span data-stu-id="7bfd8-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="7bfd8-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="7bfd8-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="7bfd8-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="7bfd8-114">0x014C</span></span>|<span data-ttu-id="7bfd8-115">x86</span><span class="sxs-lookup"><span data-stu-id="7bfd8-115">x86</span></span>|  
|<span data-ttu-id="7bfd8-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="7bfd8-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="7bfd8-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="7bfd8-117">0x0200</span></span>|<span data-ttu-id="7bfd8-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="7bfd8-118">Intel IPF</span></span>|  
|<span data-ttu-id="7bfd8-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="7bfd8-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="7bfd8-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="7bfd8-120">0x8664</span></span>|<span data-ttu-id="7bfd8-121">X64</span><span class="sxs-lookup"><span data-stu-id="7bfd8-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7bfd8-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7bfd8-122">Requirements</span></span>  
 <span data-ttu-id="7bfd8-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bfd8-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bfd8-124">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7bfd8-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7bfd8-125">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7bfd8-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7bfd8-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bfd8-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bfd8-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7bfd8-127">See also</span></span>
- [<span data-ttu-id="7bfd8-128">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7bfd8-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="7bfd8-129">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="7bfd8-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7bfd8-130">CorPEKind, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="7bfd8-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
