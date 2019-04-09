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
ms.openlocfilehash: d9dda1fb38546138d52b5fe61754d5497e676c37
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113500"
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="75897-102">IMetaDataImport2::GetPEKind — Metoda</span><span class="sxs-lookup"><span data-stu-id="75897-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="75897-103">Pobiera wartość identyfikujący rodzaj kodu w pliku wykonalnego (PE) pliku, zazwyczaj pliku DLL lub EXE, który jest zdefiniowany w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="75897-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75897-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="75897-104">Syntax</span></span>  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75897-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="75897-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="75897-106">[out] Wskaźnik do wartości [corpekind —](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) wyliczenie opisujące pliku PE.</span><span class="sxs-lookup"><span data-stu-id="75897-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="75897-107">[out] Wskaźnik do wartość, która identyfikuje architektury maszyny.</span><span class="sxs-lookup"><span data-stu-id="75897-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="75897-108">Zobacz następną sekcję uzyskać odpowiednie wartości.</span><span class="sxs-lookup"><span data-stu-id="75897-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75897-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="75897-109">Remarks</span></span>  
 <span data-ttu-id="75897-110">Wartość przywołana przez `pdwMachine` parametr może być jedną z następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="75897-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="75897-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="75897-111">Value</span></span>|<span data-ttu-id="75897-112">Architektura komputera</span><span class="sxs-lookup"><span data-stu-id="75897-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="75897-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="75897-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="75897-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="75897-114">0x014C</span></span>|<span data-ttu-id="75897-115">x86</span><span class="sxs-lookup"><span data-stu-id="75897-115">x86</span></span>|  
|<span data-ttu-id="75897-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="75897-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="75897-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="75897-117">0x0200</span></span>|<span data-ttu-id="75897-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="75897-118">Intel IPF</span></span>|  
|<span data-ttu-id="75897-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="75897-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="75897-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="75897-120">0x8664</span></span>|<span data-ttu-id="75897-121">X64</span><span class="sxs-lookup"><span data-stu-id="75897-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75897-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75897-122">Requirements</span></span>  
 <span data-ttu-id="75897-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75897-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75897-124">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="75897-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75897-125">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="75897-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="75897-126">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="75897-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="75897-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75897-127">See also</span></span>

- [<span data-ttu-id="75897-128">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="75897-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="75897-129">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="75897-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="75897-130">CorPEKind — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="75897-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
