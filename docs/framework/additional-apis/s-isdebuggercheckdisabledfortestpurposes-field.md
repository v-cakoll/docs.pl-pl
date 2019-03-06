---
title: s_isDebuggerCheckDisabledForTestPurposes Field
ms.date: 03/30/2017
ms.technology:
- dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
ms.openlocfilehash: b6490919163a7c4a618bf9a8d0e2aa145f60eda1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372311"
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a>s_isDebuggerCheckDisabledForTestPurposes Field

To pole prywatne w `System.Windows.Diagnostics.VisualDiagnostics` klasa jest używana przez program Visual Studio, aby ustalić, czy wewnętrzny dla debugera aktywnego będą sprawdzane.

## <a name="syntax"></a>Składnia

```csharp
private static bool s_isDebuggerCheckDisabledForTestPurposes
```

> [!WARNING]
> Interfejsy API w `System.Windows.Diagnostics.VisualDiagnostics` klasy są dostępne tylko, gdy aplikacja jest uruchomiona w debugerze. Ustaw `s_isDebuggerCheckDisabledForTestPurposes` do `true` dostęp do interfejsów API poza debugera.
>
> Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.

## <a name="requirements"></a>Wymagania

**Namespace:** <xref:System.Windows.Diagnostics>

**Zestaw:** PresentationCore (w PresentationCore.dll)

**Wersje programu .NET framework:** Dostępne od wersji 4.6.