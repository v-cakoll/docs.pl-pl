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
# <a name="activate-function-wpf-unmanaged-api-reference"></a>Aktywowanie funkcji (niezarządzany wykaz interfejsów API WPF.)

Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.

Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemem windows.

## <a name="syntax"></a>Składnia

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a>Parametry

`pParameters`\
Wskaźnik do okna parametry aktywacji.

`ppInner`\
Wskaźnik na adres buforu Jednoelementowy, który zawiera wskaźnik do <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> obiektu.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [.NET Framework System Requirements](../../get-started/system-requirements.md).

**DLL:**

W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll

W programie .NET Framework 4 i nowszych wersji: PresentationHost_v0400.dll

**Wersja programu .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [Niezarządzane interfejsy API WPF — informacje](wpf-unmanaged-api-reference.md)
