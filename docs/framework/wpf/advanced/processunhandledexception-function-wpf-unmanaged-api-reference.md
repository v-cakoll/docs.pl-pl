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
ms.openlocfilehash: 0c8751454be6e0eed547c38e9d0bc7931abaec3d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196973"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="d813c-102">ProcessUnhandledException, funkcja (niezarządzany wykaz interfejsów API WPF.)</span><span class="sxs-lookup"><span data-stu-id="d813c-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="d813c-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d813c-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="d813c-104">Używana przez infrastrukturę Windows Presentation Foundation (WPF) do obsługi wyjątku.</span><span class="sxs-lookup"><span data-stu-id="d813c-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d813c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d813c-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="d813c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d813c-106">Parameters</span></span>  
 <span data-ttu-id="d813c-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="d813c-107">errorMsg</span></span>  
 <span data-ttu-id="d813c-108">Komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="d813c-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d813c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d813c-109">Requirements</span></span>  
 <span data-ttu-id="d813c-110">**Platformy:** Zobacz [.NET Framework System Requirements](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d813c-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d813c-111">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="d813c-111">**DLL:**</span></span>  
  
 <span data-ttu-id="d813c-112">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="d813c-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="d813c-113">W programie .NET Framework 4 i nowszych wersji: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="d813c-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="d813c-114">**Wersja programu .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d813c-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d813c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d813c-115">See also</span></span>

- [<span data-ttu-id="d813c-116">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="d813c-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
