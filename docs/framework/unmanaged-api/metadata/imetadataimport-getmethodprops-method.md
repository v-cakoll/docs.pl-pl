---
title: IMetaDataImport::GetMethodProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
ms.openlocfilehash: 4a258ce9121a287929ca5bc39c480f1ca2596e78
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437465"
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="8a75c-102">IMetaDataImport::GetMethodProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="8a75c-102">IMetaDataImport::GetMethodProps Method</span></span>
<span data-ttu-id="8a75c-103">Pobiera metadane skojarzone z metodą przywoływaną przez określony token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="8a75c-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a75c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a75c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a75c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a75c-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="8a75c-106">podczas Token MethodDef reprezentujący metodę zwrócenia metadanych dla.</span><span class="sxs-lookup"><span data-stu-id="8a75c-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="8a75c-107">określoną Wskaźnik do tokenu TypeDef, który reprezentuje typ implementujący metodę.</span><span class="sxs-lookup"><span data-stu-id="8a75c-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="8a75c-108">określoną Wskaźnik do buforu, który ma nazwę metody.</span><span class="sxs-lookup"><span data-stu-id="8a75c-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="8a75c-109">podczas Żądany rozmiar `szMethod`.</span><span class="sxs-lookup"><span data-stu-id="8a75c-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="8a75c-110">określoną Wskaźnik do rozmiaru w szerokich znakach `szMethod`lub w przypadku obcinania, rzeczywista liczba znaków dwubajtowych w nazwie metody.</span><span class="sxs-lookup"><span data-stu-id="8a75c-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="8a75c-111">określoną Wskaźnik do wszystkich flag skojarzonych z metodą.</span><span class="sxs-lookup"><span data-stu-id="8a75c-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="8a75c-112">określoną Wskaźnik do binarnego podpisu metadanych metody.</span><span class="sxs-lookup"><span data-stu-id="8a75c-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="8a75c-113">określoną Wskaźnik do rozmiaru w bajtach `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="8a75c-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="8a75c-114">określoną Wskaźnik do względnego adresu wirtualnego metody.</span><span class="sxs-lookup"><span data-stu-id="8a75c-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="8a75c-115">określoną Wskaźnik do dowolnych flag implementacji dla metody.</span><span class="sxs-lookup"><span data-stu-id="8a75c-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a75c-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a75c-116">Requirements</span></span>  
 <span data-ttu-id="8a75c-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a75c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a75c-118">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8a75c-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a75c-119">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8a75c-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a75c-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a75c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a75c-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a75c-121">See also</span></span>

- [<span data-ttu-id="8a75c-122">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a75c-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8a75c-123">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a75c-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
