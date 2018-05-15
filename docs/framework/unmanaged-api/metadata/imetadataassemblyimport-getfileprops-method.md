---
title: IMetaDataAssemblyImport::GetFileProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f147fef90d7a9033bdfd07b75e5c33efd2c6881f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="795e3-102">IMetaDataAssemblyImport::GetFileProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="795e3-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="795e3-103">Pobiera właściwości pliku podpisem określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="795e3-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="795e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="795e3-104">Syntax</span></span>  
  
```  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,   
    [out] LPWSTR      szName,   
    [in]  ULONG       cchName,   
    [out] ULONG       *pchName,   
    [out] const void  **ppbHashValue,   
    [out] ULONG       *pcbHashValue,   
    [out] DWORD       *pdwFileFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="795e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="795e3-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="795e3-106">[in] `mdFile` Token metadanych, który reprezentuje plik, dla którego można pobrać właściwości.</span><span class="sxs-lookup"><span data-stu-id="795e3-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="795e3-107">[out] Prosta nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="795e3-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="795e3-108">[in] Rozmiar w znaki dwubajtowe z `szName`.</span><span class="sxs-lookup"><span data-stu-id="795e3-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="795e3-109">[out] Liczba znaki dwubajtowe faktycznie zwracane w `szName`.</span><span class="sxs-lookup"><span data-stu-id="795e3-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="795e3-110">[out] Wskaźnik do wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="795e3-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="795e3-111">Jest to wartość skrótu, za pomocą algorytmu SHA-1, w pliku.</span><span class="sxs-lookup"><span data-stu-id="795e3-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="795e3-112">[out] Liczba szerokości znaków w wartości zwracane wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="795e3-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="795e3-113">[out] Wskaźnik do flag, które opisują zastosowane w pliku metadanych.</span><span class="sxs-lookup"><span data-stu-id="795e3-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="795e3-114">Wartość flagi składa się z co najmniej jeden [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="795e3-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="795e3-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="795e3-115">Requirements</span></span>  
 <span data-ttu-id="795e3-116">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="795e3-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="795e3-117">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="795e3-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="795e3-118">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="795e3-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="795e3-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="795e3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="795e3-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="795e3-120">See Also</span></span>  
 [<span data-ttu-id="795e3-121">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="795e3-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
