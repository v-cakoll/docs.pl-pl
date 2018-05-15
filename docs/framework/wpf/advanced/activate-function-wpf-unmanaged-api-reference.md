---
title: Funkcja (WPF niezarządzany wykaz interfejsów API)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Acrivate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: 4931f64a525f14ad5b0b69c582a81cd15d98e541
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="f45a6-102">Funkcja (WPF niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="f45a6-102">Activate Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="f45a6-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f45a6-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="f45a6-104">Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemu windows.</span><span class="sxs-lookup"><span data-stu-id="f45a6-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f45a6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f45a6-105">Syntax</span></span>  
  
```cpp  
void Activate(  
    const ActivateParameters* pParameters,  
    __deref_out_ecount(1) LPUNKNOWN* ppInner,  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f45a6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f45a6-106">Parameters</span></span>  
 <span data-ttu-id="f45a6-107">pParameters</span><span class="sxs-lookup"><span data-stu-id="f45a6-107">pParameters</span></span>  
 <span data-ttu-id="f45a6-108">Wskaźnik do okna parametrów aktywacji.</span><span class="sxs-lookup"><span data-stu-id="f45a6-108">A pointer to the window's activation parameters.</span></span>  
  
 <span data-ttu-id="f45a6-109">ppInner</span><span class="sxs-lookup"><span data-stu-id="f45a6-109">ppInner</span></span>  
 <span data-ttu-id="f45a6-110">Wskaźnik do adres buforu jeden element, który zawiera wskaźnik do <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f45a6-110">A pointer to the address of a single-element buffer that contains a pointer to an <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f45a6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f45a6-111">Requirements</span></span>  
 <span data-ttu-id="f45a6-112">**Platformy:** zobacz [wymagania systemowe programu .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f45a6-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f45a6-113">**BIBLIOTEKI DLL:**</span><span class="sxs-lookup"><span data-stu-id="f45a6-113">**DLL:**</span></span>  
  
 <span data-ttu-id="f45a6-114">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="f45a6-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="f45a6-115">W wersji programu .NET Framework 4 i nowszych: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="f45a6-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="f45a6-116">**.NET framework w wersji:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f45a6-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f45a6-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f45a6-117">See Also</span></span>  
 [<span data-ttu-id="f45a6-118">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="f45a6-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
