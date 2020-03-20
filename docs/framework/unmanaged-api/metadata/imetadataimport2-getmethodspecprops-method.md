---
title: IMetaDataImport2::GetMethodSpecProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetMethodSpecProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetMethodSpecProps
helpviewer_keywords:
- GetMethodSpecProps method [.NET Framework metadata]
- IMetaDataImport2::GetMethodSpecProps method [.NET Framework metadata]
ms.assetid: 9544b711-e669-4eaf-8630-ee862e5e4489
topic_type:
- apiref
ms.openlocfilehash: 0bfbfec930c193ea05a01bd5bd9f46d2ec6714b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175294"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="640ac-102">IMetaDataImport2::GetMethodSpecProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="640ac-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="640ac-103">Pobiera podpis metadanych metody, do którego odwołuje się określony token MethodSpec.</span><span class="sxs-lookup"><span data-stu-id="640ac-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="640ac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="640ac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,
   [out] ULONG            *pcbSigBlob  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="640ac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="640ac-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="640ac-106">[w] A MethodSpec token, który reprezentuje wystąpienie metody.</span><span class="sxs-lookup"><span data-stu-id="640ac-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="640ac-107">[na zewnątrz] Wskaźnik do MethodDef lub MethodRef token, który reprezentuje definicję metody.</span><span class="sxs-lookup"><span data-stu-id="640ac-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="640ac-108">[na zewnątrz] Wskaźnik do podpisu binarnych metadanych metody.</span><span class="sxs-lookup"><span data-stu-id="640ac-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="640ac-109">[na zewnątrz] Rozmiar w bajtach `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="640ac-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="640ac-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="640ac-110">Requirements</span></span>  
 <span data-ttu-id="640ac-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="640ac-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="640ac-112">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="640ac-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="640ac-113">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="640ac-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="640ac-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="640ac-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="640ac-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="640ac-115">See also</span></span>

- [<span data-ttu-id="640ac-116">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="640ac-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="640ac-117">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="640ac-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
