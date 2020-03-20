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
ms.openlocfilehash: fb673666543bea3df44005ee3b20d311524f51d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175918"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="2058a-102">IMetaDataDispenserEx::GetCORSystemDirectory — Metoda</span><span class="sxs-lookup"><span data-stu-id="2058a-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="2058a-103">Pobiera katalog, który przechowuje bieżący środowiska wykonawczego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="2058a-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="2058a-104">Ta metoda jest obsługiwana tylko do użytku przez debugery poza procesem.</span><span class="sxs-lookup"><span data-stu-id="2058a-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="2058a-105">Jeśli zostanie wywołana z innego składnika, zwróci E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="2058a-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2058a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="2058a-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,
    [in]  DWORD       cchBuffer,
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2058a-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="2058a-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="2058a-108">[na zewnątrz] Bufor do odbierania nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="2058a-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="2058a-109">[w] Rozmiar w bajtach `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="2058a-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="2058a-110">[na zewnątrz] Liczba bajtów faktycznie `szBuffer`zwróconych w .</span><span class="sxs-lookup"><span data-stu-id="2058a-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2058a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2058a-111">Requirements</span></span>  
 <span data-ttu-id="2058a-112">**Platforma:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2058a-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2058a-113">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="2058a-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2058a-114">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2058a-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2058a-115">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2058a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2058a-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2058a-116">See also</span></span>

- [<span data-ttu-id="2058a-117">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="2058a-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="2058a-118">IMetaDataDispenser — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2058a-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
