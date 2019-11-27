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
ms.openlocfilehash: 82302124828a2dab73b445128d7d847e112edd36
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448216"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="2e9e3-102">IMetaDataAssemblyImport::GetExportedTypeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="2e9e3-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="2e9e3-103">Pobiera zestaw właściwości wyeksportowanego typu z określonym podpisem metadanych.</span><span class="sxs-lookup"><span data-stu-id="2e9e3-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e9e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e9e3-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2e9e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e9e3-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="2e9e3-106">podczas `mdExportedType` token metadanych reprezentujący wyeksportowany typ.</span><span class="sxs-lookup"><span data-stu-id="2e9e3-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="2e9e3-107">określoną Nazwa wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="2e9e3-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="2e9e3-108">podczas Rozmiar, w postaci znaków dwubajtowych, `szName`.</span><span class="sxs-lookup"><span data-stu-id="2e9e3-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="2e9e3-109">określoną Liczba znaków dwubajtowych w rzeczywistości zwracanych w `szName`</span><span class="sxs-lookup"><span data-stu-id="2e9e3-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="2e9e3-110">określoną `mdFile`, `mdAssemblyRef`lub `mdExportedType` token metadanych, który zawiera lub zezwala na dostęp do właściwości wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="2e9e3-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="2e9e3-111">określoną Wskaźnik do tokenu `mdTypeDef`, który reprezentuje typ w pliku.</span><span class="sxs-lookup"><span data-stu-id="2e9e3-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="2e9e3-112">określoną Wskaźnik do flag opisujących metadane zastosowane do wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="2e9e3-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="2e9e3-113">Wartość flag może być jedną lub większą liczbą wartości [CorTypeAttr —](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="2e9e3-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e9e3-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2e9e3-114">Requirements</span></span>  
 <span data-ttu-id="2e9e3-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e9e3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e9e3-116">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2e9e3-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2e9e3-117">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2e9e3-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2e9e3-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e9e3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e9e3-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e9e3-119">See also</span></span>

- [<span data-ttu-id="2e9e3-120">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="2e9e3-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
