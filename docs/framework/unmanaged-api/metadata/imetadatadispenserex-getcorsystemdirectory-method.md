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
ms.openlocfilehash: a76c17e663fdf6555ed878cca1b86b6a9395730e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008797"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="cfd87-102">IMetaDataDispenserEx::GetCORSystemDirectory — Metoda</span><span class="sxs-lookup"><span data-stu-id="cfd87-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="cfd87-103">Pobiera katalog, który przechowuje bieżące środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="cfd87-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="cfd87-104">Ta metoda jest obsługiwana tylko dla debugerów out-of-process.</span><span class="sxs-lookup"><span data-stu-id="cfd87-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="cfd87-105">Jeśli wywoływana z innego składnika, zwróci E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="cfd87-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfd87-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="cfd87-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,
    [in]  DWORD       cchBuffer,
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfd87-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="cfd87-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="cfd87-108">określoną Bufor, w którym ma zostać odebrana nazwa katalogu.</span><span class="sxs-lookup"><span data-stu-id="cfd87-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="cfd87-109">podczas Rozmiar, w bajtach, z `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="cfd87-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="cfd87-110">określoną Liczba bajtów, które faktycznie zostały zwrócone `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="cfd87-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfd87-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cfd87-111">Requirements</span></span>  
 <span data-ttu-id="cfd87-112">**Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfd87-112">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfd87-113">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cfd87-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cfd87-114">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cfd87-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cfd87-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfd87-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfd87-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cfd87-116">See also</span></span>

- [<span data-ttu-id="cfd87-117">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="cfd87-117">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="cfd87-118">IMetaDataDispenser — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cfd87-118">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
