---
title: Identyfikowanie funkcji w bibliotekach DLL
ms.date: 03/30/2017
helpviewer_keywords:
- platform invoke, identifying functions
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- identifying DLL functions
- DLL functions
ms.assetid: 3e3f6780-6d90-4413-bad7-ba641220364d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc160678817266dc649f60dc3f2cc77044c05691
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388622"
---
# <a name="identifying-functions-in-dlls"></a>Identyfikowanie funkcji w bibliotekach DLL
Tożsamość funkcji DLL składa się z następujących elementów:  
  
-   Nazwa funkcji lub numer  
  
-   Nazwa pliku biblioteki DLL, w którym można znaleźć implementacji  
  
 Na przykład określenie **MessageBox** funkcji w User32.dll identyfikuje funkcji (**MessageBox**) oraz jej lokalizację (User32.dll, User32 lub user32). Interfejsu programowania aplikacji (Win32 API) Microsoft Windows może zawierać dwóch wersji każdej funkcji, która obsługuje znaki i ciągi: ANSI 1-bajtowych wartości znakowych i wersja 2-bajtowych wartości znakowych Unicode. Jeśli zostanie określona, zestaw znaków reprezentowany przez <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> pola, wartość domyślna to ANSI. Niektóre funkcje mogą mieć więcej niż dwie wersje.  
  
 **MessageBoxA** jest punkt wejścia ANSI **MessageBox** funkcji; **MessageBoxW** jest to wersja Unicode. Można wyświetlić listę nazw funkcji dla określonej biblioteki DLL, takich jak user32.dll, uruchamiając różnych narzędzi wiersza polecenia. Na przykład można użyć `dumpbin /exports user32.dll` lub `link /dump /exports user32.dll` można uzyskać nazwy funkcji.  
  
 Można zmienić nazwę funkcji niezarządzanej do co chcesz w kodzie tak długo, jak należy mapować Nowa nazwa oryginalnego punktu wejścia w bibliotece DLL. Aby uzyskać instrukcje dotyczące zmiany nazwy funkcji niezarządzanej DLL w kodzie źródłowym zarządzanych, zobacz [Określanie punktu wejścia](../../../docs/framework/interop/specifying-an-entry-point.md).  
  
 Wywołanie platformy umożliwia kontrolę znaczna część systemu operacyjnego przez wywołanie funkcji Win32 API i inne biblioteki dll. Oprócz API Win32 istnieje wiele innych interfejsów API i wywołania bibliotek DLL dostępne za pośrednictwem platformy.  
  
 W poniższej tabeli opisano kilka typowych bibliotek DLL w interfejsie API Win32.  
  
|DLL|Opis elementu treści|  
|---------|-----------------------------|  
|Gdi32.dll|Grafika funkcje interfejs urządzenia (GDI) dla danych wyjściowych, takich jak te dotyczące zarządzania związane z rysowaniem i czcionki urządzenia.|  
|Kernel32.dll|Funkcje niskiego poziomu systemu operacyjnego dotyczące obsługi zasobów i zarządzania pamięcią.|  
|User32.dll|Funkcje zarządzania systemu Windows do obsługi wiadomości, czasomierze, menu i komunikacji.|  
  
 Pełna dokumentacja interfejsu API Win32 Zobacz zestawu SDK platformy. Aby uzyskać przykłady pokazujące, które pokazują, jak utworzyć. Deklaracje opartych na potrzeby używania z platformy invoke, zobacz [organizowanie danych za pomocą wywołania platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wykorzystywanie niezarządzanych funkcji DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [Określanie punktu wejścia](../../../docs/framework/interop/specifying-an-entry-point.md)  
 [Tworzenie klasy utrzymującej funkcje DLL](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md)  
 [Tworzenie prototypów w kodzie zarządzanym](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [Wywołanie funkcji DLL](../../../docs/framework/interop/calling-a-dll-function.md)
