---
title: ICLRRuntimeInfo::LoadErrorString — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadErrorString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type:
- apiref
ms.openlocfilehash: da6efae38cd70a68feea56b12e86be23fde7f0cb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762191"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="6306e-102">ICLRRuntimeInfo::LoadErrorString — Metoda</span><span class="sxs-lookup"><span data-stu-id="6306e-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="6306e-103">Tłumaczy wartość HRESULT na odpowiedni komunikat o błędzie dla określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="6306e-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="6306e-104">Ta metoda zastępuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="6306e-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="6306e-105">LoadStringRC —</span><span class="sxs-lookup"><span data-stu-id="6306e-105">LoadStringRC</span></span>](loadstringrc-function.md)  
  
- [<span data-ttu-id="6306e-106">LoadStringRCEx —</span><span class="sxs-lookup"><span data-stu-id="6306e-106">LoadStringRCEx</span></span>](loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="6306e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="6306e-107">Syntax</span></span>  
  
```cpp  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6306e-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="6306e-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="6306e-109">podczas WYNIK HRESULT do przetłumaczenia.</span><span class="sxs-lookup"><span data-stu-id="6306e-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="6306e-110">określoną Ciąg komunikatu skojarzony z podaną wartością HRESULT.</span><span class="sxs-lookup"><span data-stu-id="6306e-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="6306e-111">[in. out] Rozmiar, `pwzbuffer` Aby uniknąć przekroczeń buforu.</span><span class="sxs-lookup"><span data-stu-id="6306e-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="6306e-112">Jeśli `pwzbuffer` ma wartość null, `pcchBuffer` zapewnia oczekiwany rozmiar, `pwzbuffer` który umożliwia wstępne przydzielanie.</span><span class="sxs-lookup"><span data-stu-id="6306e-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="6306e-113">podczas Identyfikator kultury.</span><span class="sxs-lookup"><span data-stu-id="6306e-113">[in] The culture identifier.</span></span> <span data-ttu-id="6306e-114">Aby użyć domyślnej kultury, należy określić-1.</span><span class="sxs-lookup"><span data-stu-id="6306e-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6306e-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6306e-115">Return Value</span></span>  
 <span data-ttu-id="6306e-116">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="6306e-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6306e-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6306e-117">HRESULT</span></span>|<span data-ttu-id="6306e-118">Opis</span><span class="sxs-lookup"><span data-stu-id="6306e-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6306e-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="6306e-119">S_OK</span></span>|<span data-ttu-id="6306e-120">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6306e-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="6306e-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="6306e-121">E_POINTER</span></span>|<span data-ttu-id="6306e-122">`pcchBuffer`ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="6306e-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="6306e-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6306e-123">E_INVALIDARG</span></span>|<span data-ttu-id="6306e-124">`pwzBuffer`ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="6306e-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6306e-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6306e-125">Requirements</span></span>  
 <span data-ttu-id="6306e-126">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6306e-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6306e-127">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="6306e-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6306e-128">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6306e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6306e-129">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6306e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6306e-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6306e-130">See also</span></span>

- [<span data-ttu-id="6306e-131">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="6306e-131">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="6306e-132">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6306e-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="6306e-133">Hosting</span><span class="sxs-lookup"><span data-stu-id="6306e-133">Hosting</span></span>](index.md)
