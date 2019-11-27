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
ms.openlocfilehash: 6b5b3b3b5a3613668f4470f48083ae010cc9d336
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445255"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="0d45d-102">IMetaDataImport2::GetMethodSpecProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="0d45d-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="0d45d-103">Pobiera sygnaturę metadanych metody przywoływanej przez określony token elementu MethodSpec.</span><span class="sxs-lookup"><span data-stu-id="0d45d-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d45d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d45d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,   
   [out] ULONG            *pcbSigBlob  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="0d45d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d45d-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="0d45d-106">podczas Token elementu MethodSpec, który reprezentuje Tworzenie wystąpienia metody.</span><span class="sxs-lookup"><span data-stu-id="0d45d-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="0d45d-107">określoną Wskaźnik do tokenu MethodDef lub MethodRef, który reprezentuje definicję metody.</span><span class="sxs-lookup"><span data-stu-id="0d45d-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="0d45d-108">określoną Wskaźnik do binarnego podpisu metadanych metody.</span><span class="sxs-lookup"><span data-stu-id="0d45d-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="0d45d-109">określoną Rozmiar w bajtach `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="0d45d-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d45d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0d45d-110">Requirements</span></span>  
 <span data-ttu-id="0d45d-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d45d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d45d-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0d45d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0d45d-113">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0d45d-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0d45d-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d45d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d45d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d45d-115">See also</span></span>

- [<span data-ttu-id="0d45d-116">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0d45d-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="0d45d-117">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="0d45d-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
