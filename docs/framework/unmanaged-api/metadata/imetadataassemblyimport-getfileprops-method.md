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
ms.openlocfilehash: 78c192f10f629a0c1316ae7af7fc774819f4de8f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007484"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="a4488-102">IMetaDataAssemblyImport::GetFileProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="a4488-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="a4488-103">Pobiera właściwości pliku z określonym podpisem metadanych.</span><span class="sxs-lookup"><span data-stu-id="a4488-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4488-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a4488-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a4488-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4488-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="a4488-106">podczas `mdFile`Token metadanych reprezentujący plik, dla którego mają zostać pobrane właściwości.</span><span class="sxs-lookup"><span data-stu-id="a4488-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="a4488-107">określoną Prosta nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="a4488-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="a4488-108">podczas Rozmiar, w postaci szerokich znaków, z `szName` .</span><span class="sxs-lookup"><span data-stu-id="a4488-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="a4488-109">określoną Liczba znaków dwubajtowych, które są w rzeczywistości zwracane `szName` .</span><span class="sxs-lookup"><span data-stu-id="a4488-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="a4488-110">określoną Wskaźnik do wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="a4488-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="a4488-111">Jest to skrót, przy użyciu algorytmu SHA-1 pliku.</span><span class="sxs-lookup"><span data-stu-id="a4488-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="a4488-112">określoną Liczba znaków dwubajtowych w zwracanej wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="a4488-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="a4488-113">określoną Wskaźnik do flag, które opisują metadane zastosowane do pliku.</span><span class="sxs-lookup"><span data-stu-id="a4488-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="a4488-114">Wartość flags jest kombinacją co najmniej jednej wartości [CorFileFlags —](corfileflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="a4488-114">The flags value is a combination of one or more [CorFileFlags](corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4488-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a4488-115">Requirements</span></span>  
 <span data-ttu-id="a4488-116">**Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4488-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4488-117">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a4488-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a4488-118">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a4488-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a4488-119">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4488-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4488-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4488-120">See also</span></span>

- [<span data-ttu-id="a4488-121">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a4488-121">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
