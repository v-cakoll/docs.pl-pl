---
title: IMetaDataImport::GetModuleRefProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type:
- apiref
ms.openlocfilehash: dce9b9c20cbc73c6a70a34afa6c348c23164ed9e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437318"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="19609-102">IMetaDataImport::GetModuleRefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="19609-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="19609-103">Pobiera nazwę modułu, do którego odwołuje się określony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="19609-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19609-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="19609-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,   
   [in]  ULONG               cchName,   
   [out] ULONG               *pchName   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19609-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="19609-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="19609-106">podczas Token metadanych elementu ModuleRef odwołujący się do modułu, w którym są uzyskiwane informacje o metadanych.</span><span class="sxs-lookup"><span data-stu-id="19609-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="19609-107">określoną Bufor przechowujący nazwę modułu.</span><span class="sxs-lookup"><span data-stu-id="19609-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="19609-108">podczas Żądany rozmiar `szName` w znaki dwubajtowe.</span><span class="sxs-lookup"><span data-stu-id="19609-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="19609-109">określoną Zwrócony rozmiar `szName` znaków dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="19609-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19609-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19609-110">Requirements</span></span>  
 <span data-ttu-id="19609-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19609-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19609-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="19609-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="19609-113">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="19609-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="19609-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19609-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19609-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19609-115">See also</span></span>

- [<span data-ttu-id="19609-116">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="19609-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="19609-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="19609-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
