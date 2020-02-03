---
title: Funkcja ProcessUnhandledException — dokumentacja interfejsu API Unmanaged WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: 757e5ac3aa2dc4c87b210b026998523bd82045c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743924"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="4eb4c-102">ProcessUnhandledException — funkcja (odwołanie do niezarządzanego interfejsu API platformy WPF)</span><span class="sxs-lookup"><span data-stu-id="4eb4c-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="4eb4c-103">Ten interfejs API obsługuje infrastrukturę Windows Presentation Foundation (WPF) i nie jest przeznaczony do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4eb4c-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="4eb4c-104">Używane przez infrastrukturę Windows Presentation Foundation (WPF) do obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="4eb4c-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4eb4c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4eb4c-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="4eb4c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4eb4c-106">Parameters</span></span>  
 <span data-ttu-id="4eb4c-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="4eb4c-107">errorMsg</span></span>  
 <span data-ttu-id="4eb4c-108">Komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="4eb4c-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4eb4c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4eb4c-109">Requirements</span></span>  
 <span data-ttu-id="4eb4c-110">**Platformy:** Zobacz [wymagania systemowe .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4eb4c-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4eb4c-111">**BIBLIOTECE**</span><span class="sxs-lookup"><span data-stu-id="4eb4c-111">**DLL:**</span></span>  
  
 <span data-ttu-id="4eb4c-112">W .NET Framework 3,0 i 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="4eb4c-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="4eb4c-113">W .NET Framework 4 i nowszych: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="4eb4c-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="4eb4c-114">**Wersja .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4eb4c-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eb4c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4eb4c-115">See also</span></span>

- [<span data-ttu-id="4eb4c-116">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="4eb4c-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
