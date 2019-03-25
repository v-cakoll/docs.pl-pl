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
ms.openlocfilehash: cfe2be8784fd4baf6ce9e603da1c6e2388126b5a
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409331"
---
# <a name="identifying-functions-in-dlls"></a>Identyfikowanie funkcji w bibliotekach DLL
Tożsamość funkcji DLL składa się z następujących elementów:  
  
-   Nazwa funkcji lub liczbę porządkową  
  
-   Nazwa pliku DLL, w którym można znaleźć implementacji  
  
 Na przykład określenie **MessageBox** funkcji w bibliotece User32.dll identyfikuje funkcję (**MessageBox**) i jego lokalizacji (User32.dll, User32 lub user32). Interfejs (Windows API) programu Microsoft Windows może zawierać dwie wersje każdej funkcji, który obsługuje znaków i ciągów: 1-bajtowych wartości znakowych wersji ANSI i wersji 2-bajtowych wartości znakowych Unicode. Jeśli nie zostanie podany, zestaw znaków, reprezentowane przez <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> pola i wartość domyślna to ANSI. Niektóre funkcje mogą mieć więcej niż dwie wersje.  
  
 **MessageBoxA** jest punktem wejścia ANSI dla **MessageBox** funkcji; **MessageBoxW** jest wersją Unicode. Możesz wyświetlić listę nazw funkcji dla określonej biblioteki DLL, takie jak user32.dll, uruchamiając szeroką gamą narzędzi wiersza polecenia. Na przykład, można użyć `dumpbin /exports user32.dll` lub `link /dump /exports user32.dll` można uzyskać nazwy funkcji.  
  
 Możesz zmienić nazwę funkcji niezarządzanej, wedle uznania w kodzie tak długo, jak mapować Nowa nazwa do oryginalnego punktu wejścia w DLL. Aby uzyskać instrukcje dotyczące zmiany nazwy niezarządzanych funkcji DLL w zarządzanym kodzie źródłowym, zobacz [Określanie punktu wejścia](../../../docs/framework/interop/specifying-an-entry-point.md).  
  
 Umożliwia wywołania platformy do kontrolowania znaczna część systemu operacyjnego przez wywołanie funkcji interfejsu Windows API i inne biblioteki dll. Oprócz interfejsu API Windows istnieje wiele innych interfejsów API i wywołania biblioteki dll, dostępne za pośrednictwem platformy.  
  
 W poniższej tabeli opisano kilka często używanych bibliotek DLL w interfejsie API Windows.  
  
|DLL|Opis zawartości|  
|---------|-----------------------------|  
|GDI32.dll|Grafika funkcje interfejs urządzenia (GDI) dla urządzenia, dane wyjściowe, takie jak te dla zarządzania związane z rysowaniem i czcionki.|  
|Kernel32.dll|Funkcje niskiego poziomu systemu operacyjnego, zarządzanie pamięcią i obsługi zasobów.|  
|User32.dll|Funkcje zarządzania Windows do obsługi komunikatów, czasomierze, menu i komunikacji.|  
  
 Aby uzyskać pełną dokumentację interfejsu API Windows zobacz zestaw SDK platformy. Aby uzyskać przykłady pokazujące, jak utworzyć. Na podstawie NET deklaracje do użycia z platformą wywołania, zobacz [Marshaling danych za pomocą wywołania platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Zobacz także
- [Wykorzystywanie niezarządzanych funkcji DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
- [Określanie punktu wejścia](../../../docs/framework/interop/specifying-an-entry-point.md)
- [Tworzenie klasy utrzymującej funkcje DLL](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md)
- [Tworzenie prototypów w kodzie zarządzanym](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [Wywołanie funkcji DLL](../../../docs/framework/interop/calling-a-dll-function.md)
