---
title: s_isDebuggerCheckDisabledForTestPurposes pola
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
api_name: System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location: PresentationCore.dll
api_type: Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
robots: noindex,nofollow
ms.openlocfilehash: 97e5d32bff3e3150b56e8d9492aacc40f09f2afe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
