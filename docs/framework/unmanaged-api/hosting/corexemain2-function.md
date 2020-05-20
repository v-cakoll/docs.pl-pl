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
ms.openlocfilehash: 8202fe4ec3ae6ef96440f203c5aea6db84744a72
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616585"
---
# <a name="_corexemain2-function"></a><span data-ttu-id="38b76-102">_CorExeMain2 — Funkcja</span><span class="sxs-lookup"><span data-stu-id="38b76-102">_CorExeMain2 Function</span></span>
<span data-ttu-id="38b76-103">Wykonuje punkt wejścia w określonym kodzie mapowanym w pamięci.</span><span class="sxs-lookup"><span data-stu-id="38b76-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="38b76-104">Ta funkcja jest wywoływana przez program ładujący systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="38b76-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38b76-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="38b76-105">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38b76-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="38b76-106">Parameters</span></span>  
 `pUnmappedPE`  
 <span data-ttu-id="38b76-107">podczas Wskaźnik do kodu mapowanego na pamięć.</span><span class="sxs-lookup"><span data-stu-id="38b76-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="38b76-108">podczas Liczba elementów, które `pUnmappedPE` mogą być przechowywane.</span><span class="sxs-lookup"><span data-stu-id="38b76-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="38b76-109">podczas Wskaźnik do nazwy obrazu wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="38b76-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="38b76-110">podczas Nazwa pliku modułu ładującego.</span><span class="sxs-lookup"><span data-stu-id="38b76-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="38b76-111">podczas Parametry wiersza polecenia, jeśli istnieją.</span><span class="sxs-lookup"><span data-stu-id="38b76-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38b76-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38b76-112">Requirements</span></span>  
 <span data-ttu-id="38b76-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38b76-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38b76-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="38b76-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="38b76-115">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="38b76-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="38b76-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38b76-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38b76-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38b76-117">See also</span></span>

- [<span data-ttu-id="38b76-118">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="38b76-118">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
