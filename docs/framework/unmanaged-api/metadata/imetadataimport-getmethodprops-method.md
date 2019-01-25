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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ca43ebc257ee4eb9d0ef17f3399e87c03b9f9c3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740011"
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="8aafc-102">IMetaDataImport::GetMethodProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="8aafc-102">IMetaDataImport::GetMethodProps Method</span></span>
<span data-ttu-id="8aafc-103">Pobiera metadane skojarzone z metody odwołuje się określona MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="8aafc-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aafc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8aafc-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="8aafc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8aafc-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="8aafc-106">[in] Token MethodDef, który reprezentuje metodę, można zwrócić metadanych dla.</span><span class="sxs-lookup"><span data-stu-id="8aafc-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="8aafc-107">[out] Wskaźnik do TypeDef token, który reprezentuje typ, który implementuje metodę.</span><span class="sxs-lookup"><span data-stu-id="8aafc-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="8aafc-108">[out] Wskaźnik do buforu, który ma nazwę metody.</span><span class="sxs-lookup"><span data-stu-id="8aafc-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="8aafc-109">[in] Żądany rozmiar `szMethod`.</span><span class="sxs-lookup"><span data-stu-id="8aafc-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="8aafc-110">[out] Wskaźnik do rozmiaru znaków `szMethod`, lub w przypadku obcinania, rzeczywista liczba znaków dwubajtowych w polu Nazwa metody.</span><span class="sxs-lookup"><span data-stu-id="8aafc-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="8aafc-111">[out] Wskaźnik flagi, powiązany z metodą.</span><span class="sxs-lookup"><span data-stu-id="8aafc-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="8aafc-112">[out] Wskaźnik do binarnych metadanych podpis metody.</span><span class="sxs-lookup"><span data-stu-id="8aafc-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="8aafc-113">[out] Wskaźnik do rozmiar w bajtach `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="8aafc-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="8aafc-114">[out] Wskaźnik do wirtualnej adres względny metody.</span><span class="sxs-lookup"><span data-stu-id="8aafc-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="8aafc-115">[out] Wskaźnik do flag implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="8aafc-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8aafc-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8aafc-116">Requirements</span></span>  
 <span data-ttu-id="8aafc-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8aafc-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aafc-118">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="8aafc-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8aafc-119">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8aafc-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8aafc-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aafc-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aafc-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8aafc-121">See also</span></span>
- [<span data-ttu-id="8aafc-122">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="8aafc-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8aafc-123">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8aafc-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
