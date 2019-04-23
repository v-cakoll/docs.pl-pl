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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079347"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="b6343-102">IMetaDataImport2::GetMethodSpecProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="b6343-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="b6343-103">Sygnatura metadanych metody odwołuje się określona MethodSpec pobiera token.</span><span class="sxs-lookup"><span data-stu-id="b6343-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6343-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6343-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,   
   [out] ULONG            *pcbSigBlob  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="b6343-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6343-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="b6343-106">[in] Token MethodSpec, który reprezentuje wystąpienia metody.</span><span class="sxs-lookup"><span data-stu-id="b6343-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="b6343-107">[out] Wskaźnik do MethodDef lub MethodRef token, który reprezentuje definicję metody.</span><span class="sxs-lookup"><span data-stu-id="b6343-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="b6343-108">[out] Wskaźnik do binarnych metadanych podpis metody.</span><span class="sxs-lookup"><span data-stu-id="b6343-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="b6343-109">[out] Rozmiar w bajtach z `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="b6343-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6343-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6343-110">Requirements</span></span>  
 <span data-ttu-id="b6343-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6343-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6343-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b6343-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6343-113">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b6343-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6343-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6343-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6343-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6343-115">See also</span></span>

- [<span data-ttu-id="b6343-116">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6343-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="b6343-117">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6343-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
