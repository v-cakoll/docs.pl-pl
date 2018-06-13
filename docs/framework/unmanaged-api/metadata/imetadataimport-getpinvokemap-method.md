---
title: IMetaDataImport::GetPinvokeMap — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2174537e9605ad35e4f6f878954e318c7032b080
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448351"
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="a59ac-102">IMetaDataImport::GetPinvokeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="a59ac-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="a59ac-103">Pobiera element ModuleRef token reprezentujący zestaw docelowy wywołania funkcji PInvoke.</span><span class="sxs-lookup"><span data-stu-id="a59ac-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a59ac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a59ac-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="a59ac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a59ac-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a59ac-106">[in] Token FieldDef lub MethodDef można pobrać metadanych mapowania funkcji PInvoke.</span><span class="sxs-lookup"><span data-stu-id="a59ac-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="a59ac-107">[out] Wskaźnik do flagi używany do mapowania.</span><span class="sxs-lookup"><span data-stu-id="a59ac-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="a59ac-108">Ta wartość jest maską bitów z [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a59ac-108">This value is a bitmask from the [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="a59ac-109">[out] Nazwa docelowego niezarządzanej DLL.</span><span class="sxs-lookup"><span data-stu-id="a59ac-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="a59ac-110">[in] Rozmiar w znaki dwubajtowe `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="a59ac-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="a59ac-111">[out] Liczba zwracanych w znaki dwubajtowe `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="a59ac-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="a59ac-112">[out] Wskaźnik do tokenu element ModuleRef, który reprezentuje biblioteki obiektów docelowych niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="a59ac-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a59ac-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a59ac-113">Requirements</span></span>  
 <span data-ttu-id="a59ac-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a59ac-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a59ac-115">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a59ac-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a59ac-116">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a59ac-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a59ac-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a59ac-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a59ac-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a59ac-118">See Also</span></span>  
 [<span data-ttu-id="a59ac-119">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="a59ac-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a59ac-120">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a59ac-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
