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
ms.openlocfilehash: da38c04f5d67dc0220b1828ba0e5cdeb84346bb6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137946"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="80ba7-102">IMetaDataAssemblyImport::GetFileProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="80ba7-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="80ba7-103">Pobiera właściwości pliku za pomocą podpisu określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="80ba7-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80ba7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80ba7-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="80ba7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80ba7-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="80ba7-106">[in] `mdFile` Token metadanych, który reprezentuje plik dla którego można pobrać właściwości.</span><span class="sxs-lookup"><span data-stu-id="80ba7-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="80ba7-107">[out] Prosta nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="80ba7-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="80ba7-108">[in] Rozmiar w szerokie znaki z `szName`.</span><span class="sxs-lookup"><span data-stu-id="80ba7-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="80ba7-109">[out] Liczba szerokie znaki rzeczywistego zwrotu w `szName`.</span><span class="sxs-lookup"><span data-stu-id="80ba7-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="80ba7-110">[out] Wskaźnik do wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="80ba7-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="80ba7-111">Jest to skrót, przy użyciu algorytmu SHA-1 w pliku.</span><span class="sxs-lookup"><span data-stu-id="80ba7-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="80ba7-112">[out] Liczba szerokie znaki w wartości zwracane wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="80ba7-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="80ba7-113">[out] Wskaźnik flagi, które opisują metadane zastosowane do pliku.</span><span class="sxs-lookup"><span data-stu-id="80ba7-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="80ba7-114">Wartość flagi składa się z co najmniej jeden [corfileflags —](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="80ba7-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80ba7-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80ba7-115">Requirements</span></span>  
 <span data-ttu-id="80ba7-116">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80ba7-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80ba7-117">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="80ba7-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80ba7-118">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80ba7-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="80ba7-119">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="80ba7-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="80ba7-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80ba7-120">See also</span></span>

- [<span data-ttu-id="80ba7-121">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="80ba7-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
