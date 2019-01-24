---
title: ProcessUnhandledException, funkcja (niezarządzany wykaz interfejsów API WPF.)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: 73480f7cd8be7bcb5296782a8503eb689442a14c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54578643"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="73763-102">ProcessUnhandledException, funkcja (niezarządzany wykaz interfejsów API WPF.)</span><span class="sxs-lookup"><span data-stu-id="73763-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="73763-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="73763-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="73763-104">Używana przez infrastrukturę Windows Presentation Foundation (WPF) do obsługi wyjątku.</span><span class="sxs-lookup"><span data-stu-id="73763-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73763-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="73763-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73763-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="73763-106">Parameters</span></span>  
 <span data-ttu-id="73763-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="73763-107">errorMsg</span></span>  
 <span data-ttu-id="73763-108">Komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="73763-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73763-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73763-109">Requirements</span></span>  
 <span data-ttu-id="73763-110">**Platformy:** Zobacz [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73763-110">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73763-111">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="73763-111">**DLL:**</span></span>  
  
 <span data-ttu-id="73763-112">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="73763-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="73763-113">W programie .NET Framework 4 i nowszych wersji: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="73763-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="73763-114">**Wersja programu .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73763-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73763-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73763-115">See also</span></span>
- [<span data-ttu-id="73763-116">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="73763-116">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
