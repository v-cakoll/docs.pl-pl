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
# <a name="activate-function-wpf-unmanaged-api-reference"></a>Activate — funkcja (odwołanie do niezarządzanego interfejsu API platformy WPF)

Ten interfejs API obsługuje infrastrukturę Windows Presentation Foundation (WPF) i nie jest przeznaczony do użycia bezpośrednio w kodzie.

Używany przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemem Windows.

## <a name="syntax"></a>Składnia

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a>Parametry

`pParameters`\
Wskaźnik do parametrów aktywacji okna.

`ppInner`\
Wskaźnik do adresu bufora pojedynczego elementu, który zawiera wskaźnik do obiektu <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe .NET Framework](../../get-started/system-requirements.md).

**BIBLIOTECE**

W .NET Framework 3,0 i 3,5: PresentationHostDLL. dll

W .NET Framework 4 i nowszych: PresentationHost_v0400. dll

**Wersja .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [Niezarządzane interfejsy API WPF — informacje](wpf-unmanaged-api-reference.md)
