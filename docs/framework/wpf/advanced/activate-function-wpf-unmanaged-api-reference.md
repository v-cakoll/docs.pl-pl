---
title: Aktywuj funkcję — dokumentacja interfejsu API Unmanaged WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Activate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: 9c0a235e8b94294ab82da88e43f7446c29739c12
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734510"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="6dc1b-102">Activate — funkcja (odwołanie do niezarządzanego interfejsu API platformy WPF)</span><span class="sxs-lookup"><span data-stu-id="6dc1b-102">Activate Function (WPF Unmanaged API Reference)</span></span>

<span data-ttu-id="6dc1b-103">Ten interfejs API obsługuje infrastrukturę Windows Presentation Foundation (WPF) i nie jest przeznaczony do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6dc1b-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>

<span data-ttu-id="6dc1b-104">Używany przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="6dc1b-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>

## <a name="syntax"></a><span data-ttu-id="6dc1b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6dc1b-105">Syntax</span></span>

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a><span data-ttu-id="6dc1b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6dc1b-106">Parameters</span></span>

`pParameters`\
<span data-ttu-id="6dc1b-107">Wskaźnik do parametrów aktywacji okna.</span><span class="sxs-lookup"><span data-stu-id="6dc1b-107">A pointer to the window's activation parameters.</span></span>

`ppInner`\
<span data-ttu-id="6dc1b-108">Wskaźnik do adresu bufora pojedynczego elementu, który zawiera wskaźnik do obiektu <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>.</span><span class="sxs-lookup"><span data-stu-id="6dc1b-108">A pointer to the address of a single-element buffer that contains a pointer to an <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> object.</span></span>

## <a name="requirements"></a><span data-ttu-id="6dc1b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6dc1b-109">Requirements</span></span>

<span data-ttu-id="6dc1b-110">**Platformy:** Zobacz [wymagania systemowe .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dc1b-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="6dc1b-111">**BIBLIOTECE**</span><span class="sxs-lookup"><span data-stu-id="6dc1b-111">**DLL:**</span></span>

<span data-ttu-id="6dc1b-112">W .NET Framework 3,0 i 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="6dc1b-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>

<span data-ttu-id="6dc1b-113">W .NET Framework 4 i nowszych: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="6dc1b-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>

<span data-ttu-id="6dc1b-114">**Wersja .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dc1b-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6dc1b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6dc1b-115">See also</span></span>

- [<span data-ttu-id="6dc1b-116">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="6dc1b-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
