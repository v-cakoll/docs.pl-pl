---
title: IMetaDataAssemblyImport::GetExportedTypeProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
ms.openlocfilehash: 15b58e01d4ce99f19f510c760819471b84380b45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177756"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="ea325-102">IMetaDataAssemblyImport::GetExportedTypeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="ea325-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="ea325-103">Pobiera zestaw właściwości eksportowanego typu z określonym podpisem metadanych.</span><span class="sxs-lookup"><span data-stu-id="ea325-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea325-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea325-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,
    [out] LPWSTR            szName,
    [in]  ULONG             cchName,
    [out] ULONG             *pchName,
    [out] mdToken           *ptkImplementation,
    [out] mdTypeDef         *ptkTypeDef,
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea325-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea325-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="ea325-106">[w] Token `mdExportedType` metadanych reprezentujący eksportowany typ.</span><span class="sxs-lookup"><span data-stu-id="ea325-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="ea325-107">[na zewnątrz] Nazwa wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="ea325-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ea325-108">[w] Rozmiar, w szerokich `szName`znaków, z .</span><span class="sxs-lookup"><span data-stu-id="ea325-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="ea325-109">[na zewnątrz] Liczba szerokich znaków rzeczywiście zwróconych w`szName`</span><span class="sxs-lookup"><span data-stu-id="ea325-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="ea325-110">[na zewnątrz] Token `mdFile` `mdAssemblyRef`, `mdExportedType` lub metadanych, który zawiera lub umożliwia dostęp do właściwości eksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="ea325-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="ea325-111">[na zewnątrz] Wskaźnik do `mdTypeDef` tokenu, który reprezentuje typ w pliku.</span><span class="sxs-lookup"><span data-stu-id="ea325-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="ea325-112">[na zewnątrz] Wskaźnik do flag, które opisują metadane zastosowane do eksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="ea325-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="ea325-113">Wartość flag może być jedną lub kilkoma [wartościami CorTypeAttr.](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="ea325-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea325-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ea325-114">Requirements</span></span>  
 <span data-ttu-id="ea325-115">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea325-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea325-116">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="ea325-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ea325-117">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ea325-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ea325-118">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea325-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea325-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea325-119">See also</span></span>

- [<span data-ttu-id="ea325-120">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ea325-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
