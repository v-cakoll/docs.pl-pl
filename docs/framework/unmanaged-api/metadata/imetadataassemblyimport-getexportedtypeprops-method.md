---
title: "IMetaDataAssemblyImport::GetExportedTypeProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetExportedTypeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e142d0c77493ac1e9ab2bf485d8e111af4fb3ddb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="cd419-102">IMetaDataAssemblyImport::GetExportedTypeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="cd419-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="cd419-103">Pobiera zestaw właściwości wyeksportowanego typu podpisem określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="cd419-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd419-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd419-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="cd419-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd419-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="cd419-106">[in] `mdExportedType` Token metadanych, który reprezentuje wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="cd419-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="cd419-107">[out] Nazwa wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="cd419-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="cd419-108">[in] Rozmiar w znaki dwubajtowe z `szName`.</span><span class="sxs-lookup"><span data-stu-id="cd419-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="cd419-109">[out] Liczba faktycznie zwracane w znaki dwubajtowe`szName`</span><span class="sxs-lookup"><span data-stu-id="cd419-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="cd419-110">[out] `mdFile`, `mdAssemblyRef`, Lub `mdExportedType` token metadanych, który zawiera lub udziela dostępu do właściwości wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="cd419-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="cd419-111">[out] Wskaźnik do `mdTypeDef` token, który reprezentuje typ pliku.</span><span class="sxs-lookup"><span data-stu-id="cd419-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="cd419-112">[out] Wskaźnik do flag, które opisują metadanych stosowane do wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="cd419-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="cd419-113">Wartość flagi może być co najmniej jeden [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="cd419-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd419-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd419-114">Requirements</span></span>  
 <span data-ttu-id="cd419-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd419-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd419-116">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cd419-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd419-117">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cd419-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cd419-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd419-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd419-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd419-119">See Also</span></span>  
 [<span data-ttu-id="cd419-120">IMetaDataAssemblyImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="cd419-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
