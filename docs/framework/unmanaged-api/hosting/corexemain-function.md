---
title: _CorExeMain — Funkcja
ms.date: 03/30/2017
api_name:
- _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain
helpviewer_keywords:
- _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7407db297a827004c851b904b2da8652778cb08
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756419"
---
# <a name="corexemain-function"></a><span data-ttu-id="da683-102">_CorExeMain — Funkcja</span><span class="sxs-lookup"><span data-stu-id="da683-102">_CorExeMain Function</span></span>
<span data-ttu-id="da683-103">Inicjuje środowisko uruchomieniowe języka wspólnego (CLR), lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu pliku wykonywalnego i rozpoczyna wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="da683-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da683-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="da683-104">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="da683-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="da683-105">Remarks</span></span>  
 <span data-ttu-id="da683-106">Ta funkcja jest wywoływana przez moduł ładujący w procesy utworzone z zarządzanych zestawów pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="da683-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="da683-107">Dla zestawów DLL wywołuje moduł ładujący [_cordllmain —](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) zamiast tego funkcji.</span><span class="sxs-lookup"><span data-stu-id="da683-107">For DLL assemblies, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="da683-108">Program ładujący systemu operacyjnego wywołuje tę metodę, niezależnie od tego, w punkcie wejścia określonym w pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="da683-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="da683-109">W Windows 98, Windows ME, Windows NT i Windows 2000 `_CorExeMain` funkcja jest wywoływana, pośrednio za pośrednictwem naprawy w moduł ładujący systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="da683-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="da683-110">We wszystkich innych wersjach systemu Windows jest wywoływana bezpośrednio przez program ładujący systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="da683-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="da683-111">Aby uzyskać dodatkowe informacje, zobacz sekcję Uwagi w [_corvalidateimage —](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="da683-111">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da683-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="da683-112">Requirements</span></span>  
 <span data-ttu-id="da683-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da683-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da683-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="da683-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="da683-115">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="da683-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="da683-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da683-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da683-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="da683-117">See also</span></span>

- [<span data-ttu-id="da683-118">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="da683-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
