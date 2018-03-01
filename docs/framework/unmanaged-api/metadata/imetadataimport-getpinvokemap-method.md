---
title: "IMetaDataImport::GetPinvokeMap — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.GetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a28d628040a35d309515703563239a5f802dc4a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="5e15d-102">IMetaDataImport::GetPinvokeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="5e15d-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="5e15d-103">Pobiera element ModuleRef token reprezentujący zestaw docelowy wywołania funkcji PInvoke.</span><span class="sxs-lookup"><span data-stu-id="5e15d-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e15d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e15d-104">Syntax</span></span>  
  
```  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e15d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e15d-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="5e15d-106">[in] Token FieldDef lub MethodDef można pobrać metadanych mapowania funkcji PInvoke.</span><span class="sxs-lookup"><span data-stu-id="5e15d-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="5e15d-107">[out] Wskaźnik do flagi używany do mapowania.</span><span class="sxs-lookup"><span data-stu-id="5e15d-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="5e15d-108">Ta wartość jest maską bitów z [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5e15d-108">This value is a bitmask from the [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="5e15d-109">[out] Nazwa docelowego niezarządzanej DLL.</span><span class="sxs-lookup"><span data-stu-id="5e15d-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="5e15d-110">[in] Rozmiar w znaki dwubajtowe `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="5e15d-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="5e15d-111">[out] Liczba zwracanych w znaki dwubajtowe `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="5e15d-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="5e15d-112">[out] Wskaźnik do tokenu element ModuleRef, który reprezentuje biblioteki obiektów docelowych niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="5e15d-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e15d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e15d-113">Requirements</span></span>  
 <span data-ttu-id="5e15d-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e15d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e15d-115">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5e15d-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5e15d-116">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5e15d-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5e15d-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e15d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e15d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e15d-118">See Also</span></span>  
 [<span data-ttu-id="5e15d-119">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e15d-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="5e15d-120">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e15d-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
