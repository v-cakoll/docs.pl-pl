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
ms.openlocfilehash: a4480d54390aea2771e2939b0a0825f6c49c3564
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084979"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="b34ce-102">LoadFromHistory, funkcja (niezarządzany wykaz interfejsów API WPF.)</span><span class="sxs-lookup"><span data-stu-id="b34ce-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="b34ce-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b34ce-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="b34ce-104">Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemem windows.</span><span class="sxs-lookup"><span data-stu-id="b34ce-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b34ce-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b34ce-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="b34ce-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b34ce-106">Parameters</span></span>  
 <span data-ttu-id="b34ce-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="b34ce-107">pHistoryStream</span></span>  
 <span data-ttu-id="b34ce-108">Wskaźnik do strumienia danych historii.</span><span class="sxs-lookup"><span data-stu-id="b34ce-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="b34ce-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="b34ce-109">pBindCtx</span></span>  
 <span data-ttu-id="b34ce-110">Wskaźnik do kontekstu powiązania.</span><span class="sxs-lookup"><span data-stu-id="b34ce-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b34ce-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b34ce-111">Requirements</span></span>  
 <span data-ttu-id="b34ce-112">**Platformy:** Zobacz [.NET Framework System Requirements](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b34ce-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 **<span data-ttu-id="b34ce-113">DLL:</span><span class="sxs-lookup"><span data-stu-id="b34ce-113">DLL:</span></span>**  
  
 <span data-ttu-id="b34ce-114">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="b34ce-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="b34ce-115">W programie .NET Framework 4 i nowszych wersji: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="b34ce-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 **<span data-ttu-id="b34ce-116">Wersja programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b34ce-116">.NET Framework Version:</span></span>** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b34ce-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b34ce-117">See also</span></span>

- [<span data-ttu-id="b34ce-118">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="b34ce-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
