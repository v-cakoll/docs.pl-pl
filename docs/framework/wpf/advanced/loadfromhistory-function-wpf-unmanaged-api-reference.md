---
title: Funkcja LoadFromHistory — odwołanie do niezarządzanego interfejsu API WPF WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: be9b8658614e678b4370044a753554859d230fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141578"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="8e550-102">Funkcja LoadFromHistory (odwołanie do niezarządzanego interfejsu API WPF WPF)</span><span class="sxs-lookup"><span data-stu-id="8e550-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="8e550-103">Ten interfejs API obsługuje infrastrukturę Programu Windows Presentation Foundation (WPF) i nie jest przeznaczony do użycia bezpośrednio z kodu.</span><span class="sxs-lookup"><span data-stu-id="8e550-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="8e550-104">Używane przez Windows Presentation Foundation (WPF) infrastruktury do zarządzania systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="8e550-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e550-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e550-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e550-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8e550-106">Parameters</span></span>  
 <span data-ttu-id="8e550-107">pHistoryStream (Strumień historii)</span><span class="sxs-lookup"><span data-stu-id="8e550-107">pHistoryStream</span></span>  
 <span data-ttu-id="8e550-108">Wskaźnik do strumienia informacji o historii.</span><span class="sxs-lookup"><span data-stu-id="8e550-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="8e550-109">pBindCtx (właśc.</span><span class="sxs-lookup"><span data-stu-id="8e550-109">pBindCtx</span></span>  
 <span data-ttu-id="8e550-110">Wskaźnik do kontekstu powiązania.</span><span class="sxs-lookup"><span data-stu-id="8e550-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e550-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8e550-111">Requirements</span></span>  
 <span data-ttu-id="8e550-112">**Platformy:** Zobacz [.NET Framework Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e550-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e550-113">**Dll:**</span><span class="sxs-lookup"><span data-stu-id="8e550-113">**DLL:**</span></span>  
  
 <span data-ttu-id="8e550-114">W pliku .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="8e550-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="8e550-115">W pliku .NET Framework 4 i nowszym: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="8e550-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="8e550-116">**Wersja programu .NET Framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e550-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e550-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e550-117">See also</span></span>

- [<span data-ttu-id="8e550-118">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="8e550-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
