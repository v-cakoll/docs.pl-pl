---
title: s_isDebuggerCheckDisabledForTestPurposes pola
ms.date: 03/30/2017
ms.technology:
- dotnet-wpf
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
robots: noindex,nofollow
ms.openlocfilehash: fbbd8d33ea163efaad1417ab4a1435df729e4897
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a>s_isDebuggerCheckDisabledForTestPurposes pola

To pole prywatne w `System.Windows.Diagnostics.VisualDiagnostics` klasa jest używana przez program Visual Studio, aby określić, czy wewnętrzny dla aktywny debuger będą sprawdzane.

## <a name="syntax"></a>Składnia
  
```csharp  
private static bool s_isDebuggerCheckDisabledForTestPurposes
```
  
> [!WARNING]
>  Interfejsu API w `System.Windows.Diagnostics.VisualDiagnostics` klasy są dostępne tylko, gdy aplikacja jest uruchomiona w debugerze. Ustaw `s_isDebuggerCheckDisabledForTestPurposes` do `true` dostępu do interfejsów API poza debugera.  
>   
>  Firma Microsoft obsługuje Użyj tego pola w aplikacji produkcyjnej, w żadnym przypadku.  

## <a name="requirements"></a>Wymagania

**Namespace:** <xref:System.Windows.Diagnostics>

**Zestaw:** PresentationCore (w plików PresentationCore.dll)

**Wersje programu .NET framework:** dostępne od wersji 4.6.
