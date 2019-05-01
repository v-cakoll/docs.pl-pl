---
title: _CorExeMain2 — Funkcja
ms.date: 03/30/2017
api_name:
- _CorExeMain2
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain2
helpviewer_keywords:
- _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f968d84ae695eb1da127538ebdc5e4f55d6ebf39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985858"
---
# <a name="corexemain2-function"></a><span data-ttu-id="c3b50-102">_CorExeMain2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="c3b50-102">_CorExeMain2 Function</span></span>
<span data-ttu-id="c3b50-103">Uruchamia punkt wejścia w określonym kodzie mapowanym w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c3b50-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="c3b50-104">Ta funkcja jest wywoływana przez program ładujący systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="c3b50-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3b50-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3b50-105">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3b50-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3b50-106">Parameters</span></span>  
 `pUnmappedPE`  
 <span data-ttu-id="c3b50-107">[in] Wskaźnik do kodzie mapowanym w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c3b50-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="c3b50-108">[in] Liczba elementów, które `pUnmappedPE` może przechowywać.</span><span class="sxs-lookup"><span data-stu-id="c3b50-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="c3b50-109">[in] Wskaźnik na nazwę obrazu pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="c3b50-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="c3b50-110">[in] Nazwa pliku modułu ładującego.</span><span class="sxs-lookup"><span data-stu-id="c3b50-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="c3b50-111">[in] Parametry wiersza polecenia, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="c3b50-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3b50-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c3b50-112">Requirements</span></span>  
 <span data-ttu-id="c3b50-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3b50-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3b50-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c3b50-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3b50-115">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c3b50-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c3b50-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3b50-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3b50-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3b50-117">See also</span></span>

- [<span data-ttu-id="c3b50-118">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="c3b50-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
