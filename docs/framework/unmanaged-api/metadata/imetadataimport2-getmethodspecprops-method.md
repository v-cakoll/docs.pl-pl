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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c35212e7d261a5b385823fdaa345f6fbd638571c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079347"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="a0ca0-102">IMetaDataImport2::GetMethodSpecProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="a0ca0-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="a0ca0-103">Sygnatura metadanych metody odwołuje się określona MethodSpec pobiera token.</span><span class="sxs-lookup"><span data-stu-id="a0ca0-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0ca0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0ca0-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,   
   [out] ULONG            *pcbSigBlob  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="a0ca0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0ca0-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="a0ca0-106">[in] Token MethodSpec, który reprezentuje wystąpienia metody.</span><span class="sxs-lookup"><span data-stu-id="a0ca0-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="a0ca0-107">[out] Wskaźnik do MethodDef lub MethodRef token, który reprezentuje definicję metody.</span><span class="sxs-lookup"><span data-stu-id="a0ca0-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="a0ca0-108">[out] Wskaźnik do binarnych metadanych podpis metody.</span><span class="sxs-lookup"><span data-stu-id="a0ca0-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="a0ca0-109">[out] Rozmiar w bajtach z `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="a0ca0-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0ca0-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a0ca0-110">Requirements</span></span>  
 <span data-ttu-id="a0ca0-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0ca0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0ca0-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="a0ca0-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a0ca0-113">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a0ca0-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="a0ca0-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a0ca0-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a0ca0-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0ca0-115">See also</span></span>

- [<span data-ttu-id="a0ca0-116">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a0ca0-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="a0ca0-117">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a0ca0-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
