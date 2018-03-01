---
title: s_isDebuggerCheckDisabledForTestPurposes pola
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
robots: noindex,nofollow
ms.workload:
- dotnet
ms.openlocfilehash: 67da38d958d153ebe526f298785b39afb7be6513
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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

**Namespace:**<xref:System.Windows.Diagnostics>

**Zestaw:** PresentationCore (w plików PresentationCore.dll)

**Wersje programu .NET framework:** dostępne od wersji 4.6.
