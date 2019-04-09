---
title: ForwardTranslateAccelerator, funkcja (niezarządzany wykaz interfejsów API WPF.)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: 4bb7e665bb836dc5f95b14f39179f1d4b9f8173d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080257"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="58791-102">ForwardTranslateAccelerator, funkcja (niezarządzany wykaz interfejsów API WPF.)</span><span class="sxs-lookup"><span data-stu-id="58791-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="58791-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="58791-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="58791-104">Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemem windows.</span><span class="sxs-lookup"><span data-stu-id="58791-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58791-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="58791-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="58791-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="58791-106">Parameters</span></span>  
 <span data-ttu-id="58791-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="58791-107">pMsg</span></span>  
 <span data-ttu-id="58791-108">Wskaźnik do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="58791-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="58791-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="58791-109">appUnhandled</span></span>  
 `true` <span data-ttu-id="58791-110">gdy aplikacja został już podany Państwo, by obsłużyć komunikat wejściowy, ale nie został obsłużony w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="58791-110">when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58791-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="58791-111">Requirements</span></span>  
 <span data-ttu-id="58791-112">**Platformy:** Zobacz [.NET Framework System Requirements](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58791-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 **<span data-ttu-id="58791-113">DLL:</span><span class="sxs-lookup"><span data-stu-id="58791-113">DLL:</span></span>**  
  
 <span data-ttu-id="58791-114">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="58791-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="58791-115">W programie .NET Framework 4 i nowszych wersji: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="58791-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 **<span data-ttu-id="58791-116">Wersja programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="58791-116">.NET Framework Version:</span></span>** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="58791-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58791-117">See also</span></span>

- [<span data-ttu-id="58791-118">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="58791-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
