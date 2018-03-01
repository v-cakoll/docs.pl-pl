---
title: "Funkcja ProcessUnhandledException (WPF niezarządzany wykaz interfejsów API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9bc43b42c2e671e13076ba87ce72e054bd65d107
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="f5ff4-102">Funkcja ProcessUnhandledException (WPF niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="f5ff4-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="f5ff4-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f5ff4-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="f5ff4-104">Używany przez infrastrukturę Windows Presentation Foundation (WPF) dla obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="f5ff4-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5ff4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5ff4-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5ff4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5ff4-106">Parameters</span></span>  
 <span data-ttu-id="f5ff4-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="f5ff4-107">errorMsg</span></span>  
 <span data-ttu-id="f5ff4-108">Komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="f5ff4-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5ff4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5ff4-109">Requirements</span></span>  
 <span data-ttu-id="f5ff4-110">**Platformy:** zobacz [wymagania systemowe programu .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5ff4-110">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5ff4-111">**BIBLIOTEKI DLL:**</span><span class="sxs-lookup"><span data-stu-id="f5ff4-111">**DLL:**</span></span>  
  
 <span data-ttu-id="f5ff4-112">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="f5ff4-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="f5ff4-113">W wersji programu .NET Framework 4 i nowszych: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="f5ff4-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="f5ff4-114">**Wersja platformy .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5ff4-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5ff4-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5ff4-115">See Also</span></span>  
 [<span data-ttu-id="f5ff4-116">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="f5ff4-116">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
