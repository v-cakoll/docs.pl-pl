---
title: Aktywowanie funkcji (niezarządzany wykaz interfejsów API WPF.)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Acrivate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: 6410b05a1b858a7b75c9bff3220d47505beabd7c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357277"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="bb210-102">Aktywowanie funkcji (niezarządzany wykaz interfejsów API WPF.)</span><span class="sxs-lookup"><span data-stu-id="bb210-102">Activate Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="bb210-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="bb210-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="bb210-104">Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemem windows.</span><span class="sxs-lookup"><span data-stu-id="bb210-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb210-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb210-105">Syntax</span></span>  
  
```cpp  
void Activate(  
    const ActivateParameters* pParameters,  
    __deref_out_ecount(1) LPUNKNOWN* ppInner,  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb210-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb210-106">Parameters</span></span>  
 <span data-ttu-id="bb210-107">pParameters</span><span class="sxs-lookup"><span data-stu-id="bb210-107">pParameters</span></span>  
 <span data-ttu-id="bb210-108">Wskaźnik do okna parametry aktywacji.</span><span class="sxs-lookup"><span data-stu-id="bb210-108">A pointer to the window's activation parameters.</span></span>  
  
 <span data-ttu-id="bb210-109">ppInner</span><span class="sxs-lookup"><span data-stu-id="bb210-109">ppInner</span></span>  
 <span data-ttu-id="bb210-110">Wskaźnik na adres buforu Jednoelementowy, który zawiera wskaźnik do <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="bb210-110">A pointer to the address of a single-element buffer that contains a pointer to an <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb210-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb210-111">Requirements</span></span>  
 <span data-ttu-id="bb210-112">**Platformy:** Zobacz [.NET Framework System Requirements](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb210-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb210-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="bb210-113">**DLL:**</span></span>  
  
 <span data-ttu-id="bb210-114">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="bb210-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="bb210-115">W programie .NET Framework 4 i nowszych wersji: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="bb210-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="bb210-116">**Wersja programu .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb210-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb210-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb210-117">See also</span></span>
- [<span data-ttu-id="bb210-118">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="bb210-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
