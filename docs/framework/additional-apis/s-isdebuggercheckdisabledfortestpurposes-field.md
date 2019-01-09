---
title: s_isDebuggerCheckDisabledForTestPurposes, pole
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
ms.openlocfilehash: f490ccb4675a434e3f3336723e321f256b10093d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149179"
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a><span data-ttu-id="32f0f-102">s_isDebuggerCheckDisabledForTestPurposes, pole</span><span class="sxs-lookup"><span data-stu-id="32f0f-102">s_isDebuggerCheckDisabledForTestPurposes Field</span></span>

<span data-ttu-id="32f0f-103">To pole prywatne w `System.Windows.Diagnostics.VisualDiagnostics` klasa jest używana przez program Visual Studio, aby ustalić, czy wewnętrzny dla debugera aktywnego będą sprawdzane.</span><span class="sxs-lookup"><span data-stu-id="32f0f-103">This private field in the `System.Windows.Diagnostics.VisualDiagnostics` class is used by Visual Studio to determine whether an internal check for an active debugger will be performed.</span></span>

## <a name="syntax"></a><span data-ttu-id="32f0f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32f0f-104">Syntax</span></span>
  
```csharp  
private static bool s_isDebuggerCheckDisabledForTestPurposes
```
  
> [!WARNING]
>  <span data-ttu-id="32f0f-105">Interfejsy API w `System.Windows.Diagnostics.VisualDiagnostics` klasy są dostępne tylko, gdy aplikacja jest uruchomiona w debugerze.</span><span class="sxs-lookup"><span data-stu-id="32f0f-105">API's in the `System.Windows.Diagnostics.VisualDiagnostics` class are only available when an application is running under a debugger.</span></span> <span data-ttu-id="32f0f-106">Ustaw `s_isDebuggerCheckDisabledForTestPurposes` do `true` dostęp do interfejsów API poza debugera.</span><span class="sxs-lookup"><span data-stu-id="32f0f-106">Set `s_isDebuggerCheckDisabledForTestPurposes` to `true` to access the APIs outside of a debugger.</span></span>  
>   
>  <span data-ttu-id="32f0f-107">Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="32f0f-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>  

## <a name="requirements"></a><span data-ttu-id="32f0f-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32f0f-108">Requirements</span></span>

<span data-ttu-id="32f0f-109">**Namespace:** <xref:System.Windows.Diagnostics></span><span class="sxs-lookup"><span data-stu-id="32f0f-109">**Namespace:** <xref:System.Windows.Diagnostics></span></span>

<span data-ttu-id="32f0f-110">**Zestaw:** PresentationCore (w PresentationCore.dll)</span><span class="sxs-lookup"><span data-stu-id="32f0f-110">**Assembly:** PresentationCore (in PresentationCore.dll)</span></span>

<span data-ttu-id="32f0f-111">**Wersje programu .NET framework:** Dostępne od wersji 4.6.</span><span class="sxs-lookup"><span data-stu-id="32f0f-111">**.NET Framework versions:** Available since 4.6.</span></span>