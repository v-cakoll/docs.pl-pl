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
ms.openlocfilehash: cc5324683daa9a02a6a89b2a3fb57ee9fd5dbe72
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136959"
---
# <a name="_corexemain2-function"></a><span data-ttu-id="5b5b0-102">_CorExeMain2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="5b5b0-102">_CorExeMain2 Function</span></span>
<span data-ttu-id="5b5b0-103">Wykonuje punkt wejścia w określonym kodzie mapowanym w pamięci.</span><span class="sxs-lookup"><span data-stu-id="5b5b0-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="5b5b0-104">Ta funkcja jest wywoływana przez program ładujący systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="5b5b0-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b5b0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b5b0-105">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b5b0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b5b0-106">Parameters</span></span>  
 `pUnmappedPE`  
 <span data-ttu-id="5b5b0-107">podczas Wskaźnik do kodu mapowanego na pamięć.</span><span class="sxs-lookup"><span data-stu-id="5b5b0-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="5b5b0-108">podczas Liczba elementów, `pUnmappedPE` mogą być przechowywane.</span><span class="sxs-lookup"><span data-stu-id="5b5b0-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="5b5b0-109">podczas Wskaźnik do nazwy obrazu wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="5b5b0-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="5b5b0-110">podczas Nazwa pliku modułu ładującego.</span><span class="sxs-lookup"><span data-stu-id="5b5b0-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="5b5b0-111">podczas Parametry wiersza polecenia, jeśli istnieją.</span><span class="sxs-lookup"><span data-stu-id="5b5b0-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b5b0-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5b5b0-112">Requirements</span></span>  
 <span data-ttu-id="5b5b0-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b5b0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b5b0-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5b5b0-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5b5b0-115">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5b5b0-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5b5b0-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b5b0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b5b0-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b5b0-117">See also</span></span>

- [<span data-ttu-id="5b5b0-118">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="5b5b0-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
