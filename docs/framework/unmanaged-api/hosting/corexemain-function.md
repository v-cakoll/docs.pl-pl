---
title: "_CorExeMain — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: _CorExeMain
helpviewer_keywords: _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8c341d578a45d72804d9ac33e2aefe513fd33922
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corexemain-function"></a><span data-ttu-id="2a644-102">_CorExeMain — Funkcja</span><span class="sxs-lookup"><span data-stu-id="2a644-102">_CorExeMain Function</span></span>
<span data-ttu-id="2a644-103">Inicjuje środowisko uruchomieniowe języka wspólnego (CLR), lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu pliku wykonywalnego i rozpoczyna się wykonanie.</span><span class="sxs-lookup"><span data-stu-id="2a644-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a644-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a644-104">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="2a644-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a644-105">Remarks</span></span>  
 <span data-ttu-id="2a644-106">Ta funkcja jest wywoływana przez moduł ładujący w procesy utworzone z zarządzanych zestawów pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="2a644-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="2a644-107">Dla zestawów DLL wywołuje moduł ładujący [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) zamiast tego działania.</span><span class="sxs-lookup"><span data-stu-id="2a644-107">For DLL assemblies, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="2a644-108">Moduł ładujący systemu operacyjnego wywołuje tę metodę, niezależnie od punkt wejścia określony w pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="2a644-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="2a644-109">W Windows 98, Windows ME, Windows NT i system Windows 2000 `_CorExeMain` funkcja jest wywoływana bezpośrednio za pomocą naprawy w modułu ładującego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="2a644-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="2a644-110">We wszystkich innych wersjach systemu Windows jest ona wywoływana bezpośrednio przez moduł ładujący systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="2a644-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="2a644-111">Aby uzyskać dodatkowe informacje, zobacz sekcję uwag w [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="2a644-111">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a644-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a644-112">Requirements</span></span>  
 <span data-ttu-id="2a644-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a644-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a644-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2a644-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2a644-115">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2a644-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2a644-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a644-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a644-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a644-117">See Also</span></span>  
 [<span data-ttu-id="2a644-118">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="2a644-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
