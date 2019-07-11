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
ms.openlocfilehash: f03a2dfa60f2fbdce317d96a9e5b23c6f017dc3d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777744"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="7ec02-102">IMetaDataDispenserEx::GetCORSystemDirectory — Metoda</span><span class="sxs-lookup"><span data-stu-id="7ec02-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="7ec02-103">Pobiera katalog, który zawiera bieżące środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="7ec02-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="7ec02-104">Ta metoda jest obsługiwana tylko do użytku przez debugery spoza procesu.</span><span class="sxs-lookup"><span data-stu-id="7ec02-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="7ec02-105">Wywoływana z innego składnika, zwróci E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="7ec02-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ec02-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ec02-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,   
    [in]  DWORD       cchBuffer,   
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ec02-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="7ec02-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="7ec02-108">[out] Bufor odbioru nazwę katalogu.</span><span class="sxs-lookup"><span data-stu-id="7ec02-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="7ec02-109">[in] Rozmiar w bajtach z `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="7ec02-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="7ec02-110">[out] Liczba bajtów zwróconych w rzeczywistości w `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="7ec02-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ec02-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7ec02-111">Requirements</span></span>  
 <span data-ttu-id="7ec02-112">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ec02-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ec02-113">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7ec02-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7ec02-114">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7ec02-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7ec02-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ec02-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ec02-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ec02-116">See also</span></span>

- [<span data-ttu-id="7ec02-117">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="7ec02-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="7ec02-118">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="7ec02-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
