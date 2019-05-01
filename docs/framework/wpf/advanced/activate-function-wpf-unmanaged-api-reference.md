---
title: Aktywowanie funkcji (niezarządzany wykaz interfejsów API WPF.)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Activate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: ee231653815bd5ef75d58979034e3b3be9f5ba54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777172"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="9d3a0-102">Aktywowanie funkcji (niezarządzany wykaz interfejsów API WPF.)</span><span class="sxs-lookup"><span data-stu-id="9d3a0-102">Activate Function (WPF Unmanaged API Reference)</span></span>

<span data-ttu-id="9d3a0-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>

<span data-ttu-id="9d3a0-104">Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemem windows.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>

## <a name="syntax"></a><span data-ttu-id="9d3a0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d3a0-105">Syntax</span></span>

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a><span data-ttu-id="9d3a0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d3a0-106">Parameters</span></span>

`pParameters`\
<span data-ttu-id="9d3a0-107">Wskaźnik do okna parametry aktywacji.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-107">A pointer to the window's activation parameters.</span></span>

`ppInner`\
<span data-ttu-id="9d3a0-108">Wskaźnik na adres buforu Jednoelementowy, który zawiera wskaźnik do <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-108">A pointer to the address of a single-element buffer that contains a pointer to an <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> object.</span></span>

## <a name="requirements"></a><span data-ttu-id="9d3a0-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d3a0-109">Requirements</span></span>

<span data-ttu-id="9d3a0-110">**Platformy:** Zobacz [.NET Framework System Requirements](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d3a0-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="9d3a0-111">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="9d3a0-111">**DLL:**</span></span>

<span data-ttu-id="9d3a0-112">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="9d3a0-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>

<span data-ttu-id="9d3a0-113">W programie .NET Framework 4 i nowszych wersji: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="9d3a0-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>

<span data-ttu-id="9d3a0-114">**Wersja programu .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d3a0-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9d3a0-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d3a0-115">See also</span></span>

- [<span data-ttu-id="9d3a0-116">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="9d3a0-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
