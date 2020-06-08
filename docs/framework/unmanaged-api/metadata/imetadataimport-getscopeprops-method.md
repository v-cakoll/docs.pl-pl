---
title: IMetaDataImport::GetScopeProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
ms.openlocfilehash: 0916b6382bb9352616d85e21f423301dc6aa9fa9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490851"
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="75392-102">IMetaDataImport::GetScopeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="75392-102">IMetaDataImport::GetScopeProps Method</span></span>
<span data-ttu-id="75392-103">Pobiera nazwę i opcjonalnie identyfikator wersji zestawu lub modułu w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="75392-103">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75392-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="75392-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75392-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="75392-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="75392-106">określoną Bufor dla nazwy zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="75392-106">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="75392-107">podczas Rozmiar w postaci znaków dwubajtowych `szName` .</span><span class="sxs-lookup"><span data-stu-id="75392-107">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="75392-108">określoną Liczba znaków dwubajtowych zwracana w `szName` .</span><span class="sxs-lookup"><span data-stu-id="75392-108">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="75392-109">[out, opcjonalne] Wskaźnik do identyfikatora GUID, który jednoznacznie identyfikuje wersję zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="75392-109">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75392-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="75392-110">Remarks</span></span>  
 <span data-ttu-id="75392-111">Metoda [IMetaDataEmit:: SetModuleProps —](imetadataemit-setmoduleprops-method.md) służy do ustawiania tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="75392-111">The [IMetaDataEmit::SetModuleProps](imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75392-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75392-112">Requirements</span></span>  
 <span data-ttu-id="75392-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75392-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75392-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="75392-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75392-115">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="75392-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="75392-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75392-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75392-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75392-117">See also</span></span>

- [<span data-ttu-id="75392-118">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="75392-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="75392-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="75392-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
