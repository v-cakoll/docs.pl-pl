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
ms.openlocfilehash: c458fef77b49f522ca21dd5487731f4d43588cea
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437100"
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="ec77b-102">IMetaDataImport::GetPinvokeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="ec77b-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="ec77b-103">Pobiera token typu ModuleRef reprezentujący zestaw docelowy wywołania PInvoke.</span><span class="sxs-lookup"><span data-stu-id="ec77b-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec77b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec77b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec77b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec77b-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="ec77b-106">podczas Token FieldDef lub MethodDef, aby uzyskać metadane mapowania funkcji PInvoke dla.</span><span class="sxs-lookup"><span data-stu-id="ec77b-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="ec77b-107">określoną Wskaźnik do flag użytych do mapowania.</span><span class="sxs-lookup"><span data-stu-id="ec77b-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="ec77b-108">Ta wartość jest maska bitowa z wyliczenia [CorPinvokeMap —](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ec77b-108">This value is a bitmask from the [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="ec77b-109">określoną Nazwa niezarządzanej docelowej biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="ec77b-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="ec77b-110">podczas Rozmiar w szerokich znakach `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="ec77b-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="ec77b-111">określoną Liczba znaków dwubajtowych zwracanych w `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="ec77b-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="ec77b-112">określoną Wskaźnik do tokenu elementu ModuleRef, który reprezentuje niezarządzaną bibliotekę obiektów docelowych.</span><span class="sxs-lookup"><span data-stu-id="ec77b-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec77b-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ec77b-113">Requirements</span></span>  
 <span data-ttu-id="ec77b-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec77b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec77b-115">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ec77b-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec77b-116">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ec77b-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ec77b-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec77b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec77b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec77b-118">See also</span></span>

- [<span data-ttu-id="ec77b-119">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec77b-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ec77b-120">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec77b-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
