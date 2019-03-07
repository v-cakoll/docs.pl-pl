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
ms.openlocfilehash: 3a95e8e68361f060d843247f400043a79dc28889
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466872"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="4e7ac-102">ProcessUnhandledException, funkcja (niezarządzany wykaz interfejsów API WPF.)</span><span class="sxs-lookup"><span data-stu-id="4e7ac-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="4e7ac-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4e7ac-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="4e7ac-104">Używana przez infrastrukturę Windows Presentation Foundation (WPF) do obsługi wyjątku.</span><span class="sxs-lookup"><span data-stu-id="4e7ac-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e7ac-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e7ac-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e7ac-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e7ac-106">Parameters</span></span>  
 <span data-ttu-id="4e7ac-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="4e7ac-107">errorMsg</span></span>  
 <span data-ttu-id="4e7ac-108">Komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="4e7ac-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e7ac-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4e7ac-109">Requirements</span></span>  
 <span data-ttu-id="4e7ac-110">**Platformy:** Zobacz [.NET Framework System Requirements](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e7ac-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e7ac-111">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="4e7ac-111">**DLL:**</span></span>  
  
 <span data-ttu-id="4e7ac-112">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="4e7ac-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="4e7ac-113">W programie .NET Framework 4 i nowszych wersji: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="4e7ac-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="4e7ac-114">**Wersja programu .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e7ac-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e7ac-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e7ac-115">See also</span></span>
- [<span data-ttu-id="4e7ac-116">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="4e7ac-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
