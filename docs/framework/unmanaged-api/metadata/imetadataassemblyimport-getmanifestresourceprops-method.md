---
title: IMetaDataAssemblyImport::GetManifestResourceProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
ms.openlocfilehash: d87d0d46ede65cf44c84edba92fe246174088a4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177663"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="02d7b-102">IMetaDataAssemblyImport::GetManifestResourceProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="02d7b-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="02d7b-103">Pobiera zestaw właściwości zasobu manifestu z określonym podpisem metadanych.</span><span class="sxs-lookup"><span data-stu-id="02d7b-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02d7b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="02d7b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] mdToken              *ptkImplementation,
    [out] DWORD                *pdwOffset,
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02d7b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="02d7b-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="02d7b-106">[w] Token, `mdManifestResource` który reprezentuje zasób, dla którego można uzyskać właściwości.</span><span class="sxs-lookup"><span data-stu-id="02d7b-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="02d7b-107">[na zewnątrz] Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="02d7b-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="02d7b-108">[w] Rozmiar, w szerokich znaków, z `szName`.</span><span class="sxs-lookup"><span data-stu-id="02d7b-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="02d7b-109">[na zewnątrz] Wskaźnik do liczby szerokich znaków rzeczywiście `szName`zwrócony w .</span><span class="sxs-lookup"><span data-stu-id="02d7b-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="02d7b-110">[na zewnątrz] Wskaźnik do `mdFile` tokenu `mdAssemblyRef` lub tokenu, który reprezentuje plik lub zestaw, odpowiednio, który zawiera zasób.</span><span class="sxs-lookup"><span data-stu-id="02d7b-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="02d7b-111">[na zewnątrz] Wskaźnik do wartości, która określa przesunięcie na początku zasobu w pliku.</span><span class="sxs-lookup"><span data-stu-id="02d7b-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="02d7b-112">[na zewnątrz] Wskaźnik do flag, które opisują metadane zastosowane do zasobu.</span><span class="sxs-lookup"><span data-stu-id="02d7b-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="02d7b-113">Wartość flag jest kombinacją co najmniej jednej wartości [CorManifestResourceFlags.](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="02d7b-113">The flags value is a combination of one or more [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02d7b-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="02d7b-114">Requirements</span></span>  
 <span data-ttu-id="02d7b-115">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02d7b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02d7b-116">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="02d7b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="02d7b-117">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="02d7b-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="02d7b-118">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02d7b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02d7b-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02d7b-119">See also</span></span>

- [<span data-ttu-id="02d7b-120">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="02d7b-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
