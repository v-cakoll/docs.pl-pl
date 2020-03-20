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
ms.openlocfilehash: dae4a36537eeac58ffb17ebc1b78d935ec807cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175983"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="ff680-102">IMetaDataAssemblyImport::GetFileProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="ff680-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="ff680-103">Pobiera właściwości pliku z określonym podpisem metadanych.</span><span class="sxs-lookup"><span data-stu-id="ff680-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff680-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff680-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="ff680-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff680-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="ff680-106">[w] Token `mdFile` metadanych, który reprezentuje plik, dla którego można uzyskać właściwości.</span><span class="sxs-lookup"><span data-stu-id="ff680-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="ff680-107">[na zewnątrz] Prosta nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="ff680-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ff680-108">[w] Rozmiar, w szerokich znaków, z `szName`.</span><span class="sxs-lookup"><span data-stu-id="ff680-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="ff680-109">[na zewnątrz] Liczba szerokich znaków rzeczywiście `szName`zwrócona w .</span><span class="sxs-lookup"><span data-stu-id="ff680-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="ff680-110">[na zewnątrz] Wskaźnik do wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="ff680-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="ff680-111">Jest to skrót, przy użyciu algorytmu SHA-1, pliku.</span><span class="sxs-lookup"><span data-stu-id="ff680-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="ff680-112">[na zewnątrz] Liczba znaków szerokich w zwróconej wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="ff680-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="ff680-113">[na zewnątrz] Wskaźnik do flag, które opisują metadane zastosowane do pliku.</span><span class="sxs-lookup"><span data-stu-id="ff680-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="ff680-114">Wartość flag jest kombinacją co najmniej jednej wartości [CorFileFlags.](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="ff680-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff680-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ff680-115">Requirements</span></span>  
 <span data-ttu-id="ff680-116">**Platforma:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff680-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff680-117">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="ff680-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff680-118">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff680-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ff680-119">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff680-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff680-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff680-120">See also</span></span>

- [<span data-ttu-id="ff680-121">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ff680-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
