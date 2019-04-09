---
title: IMetaDataDispenserEx::GetCORSystemDirectory — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetCORSystemDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3dbfca942d61cd5667293d11f358f06bd000fa2e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118004"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="829c4-102">IMetaDataDispenserEx::GetCORSystemDirectory — Metoda</span><span class="sxs-lookup"><span data-stu-id="829c4-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="829c4-103">Pobiera katalog, który zawiera bieżące środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="829c4-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="829c4-104">Ta metoda jest obsługiwana tylko do użytku przez debugery spoza procesu.</span><span class="sxs-lookup"><span data-stu-id="829c4-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="829c4-105">Wywoływana z innego składnika, zwróci E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="829c4-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="829c4-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="829c4-106">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,   
    [in]  DWORD       cchBuffer,   
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="829c4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="829c4-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="829c4-108">[out] Bufor odbioru nazwę katalogu.</span><span class="sxs-lookup"><span data-stu-id="829c4-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="829c4-109">[in] Rozmiar w bajtach z `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="829c4-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="829c4-110">[out] Liczba bajtów zwróconych w rzeczywistości w `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="829c4-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="829c4-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="829c4-111">Requirements</span></span>  
 <span data-ttu-id="829c4-112">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="829c4-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="829c4-113">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="829c4-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="829c4-114">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="829c4-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="829c4-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="829c4-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="829c4-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="829c4-116">See also</span></span>

- [<span data-ttu-id="829c4-117">IMetaDataDispenserEx — Interfejs</span><span class="sxs-lookup"><span data-stu-id="829c4-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="829c4-118">IMetaDataDispenser — Interfejs</span><span class="sxs-lookup"><span data-stu-id="829c4-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
