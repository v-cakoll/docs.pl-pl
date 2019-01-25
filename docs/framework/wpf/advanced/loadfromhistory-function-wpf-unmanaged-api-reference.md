---
title: LoadFromHistory, funkcja (niezarządzany wykaz interfejsów API WPF.)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: 42be46d836a299139bded938237fe2a06e9794a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646936"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="ae4ac-102">LoadFromHistory, funkcja (niezarządzany wykaz interfejsów API WPF.)</span><span class="sxs-lookup"><span data-stu-id="ae4ac-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="ae4ac-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ae4ac-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="ae4ac-104">Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemem windows.</span><span class="sxs-lookup"><span data-stu-id="ae4ac-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae4ac-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae4ac-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae4ac-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae4ac-106">Parameters</span></span>  
 <span data-ttu-id="ae4ac-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="ae4ac-107">pHistoryStream</span></span>  
 <span data-ttu-id="ae4ac-108">Wskaźnik do strumienia danych historii.</span><span class="sxs-lookup"><span data-stu-id="ae4ac-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="ae4ac-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="ae4ac-109">pBindCtx</span></span>  
 <span data-ttu-id="ae4ac-110">Wskaźnik do kontekstu powiązania.</span><span class="sxs-lookup"><span data-stu-id="ae4ac-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae4ac-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae4ac-111">Requirements</span></span>  
 <span data-ttu-id="ae4ac-112">**Platformy:** Zobacz [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae4ac-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae4ac-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="ae4ac-113">**DLL:**</span></span>  
  
 <span data-ttu-id="ae4ac-114">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="ae4ac-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="ae4ac-115">W programie .NET Framework 4 i nowszych wersji: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="ae4ac-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="ae4ac-116">**Wersja programu .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae4ac-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae4ac-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae4ac-117">See also</span></span>
- [<span data-ttu-id="ae4ac-118">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="ae4ac-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
