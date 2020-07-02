---
title: Identyfikowanie funkcji w bibliotekach DLL
description: Zidentyfikuj funkcje w bibliotekach DLL. Tożsamość funkcji biblioteki DLL składa się z nazwy funkcji lub liczby porządkowej oraz nazwy pliku DLL, w której można znaleźć implementację.
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
ms.openlocfilehash: 054d1351a9ee6adab17117c9f423aa26d0d9ed59
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622734"
---
# <a name="identifying-functions-in-dlls"></a>Identyfikowanie funkcji w bibliotekach DLL
Tożsamość funkcji DLL składa się z następujących elementów:  
  
- Nazwa funkcji lub liczba porządkowa  
  
- Nazwa pliku DLL, w którym można znaleźć implementację  
  
 Na przykład określenie funkcji **MessageBox** w User32.dll identyfikuje funkcję (**MessageBox**) i jej lokalizację (User32.dll, User32 lub User32). Interfejs programowania aplikacji systemu Microsoft Windows (Windows API) może zawierać dwie wersje każdej funkcji, która obsługuje znaki i ciągi: 1-bajtowego znaku ANSI i 2-bajtowego znaku Unicode. Gdy nie zostanie określony, zestaw znaków reprezentowany przez pole jest <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> wartością domyślną ANSI. Niektóre funkcje mogą mieć więcej niż dwie wersje.  
  
 **MessageBox** jest punktem wejścia ANSI dla funkcji **MessageBox** ; **MessageBoxW** to wersja Unicode. Można wyświetlić listę nazw funkcji dla konkretnej biblioteki DLL, takiej jak user32.dll, uruchamiając wiele narzędzi wiersza polecenia. Na przykład można użyć lub, `dumpbin /exports user32.dll` `link /dump /exports user32.dll` Aby uzyskać nazwy funkcji.  
  
 Można zmienić nazwę funkcji niezarządzanej na dowolnie w kodzie, tak długo, jak mapowanie nowej nazwy do oryginalnego punktu wejścia w bibliotece DLL. Aby uzyskać instrukcje dotyczące zmiany nazwy niezarządzanej funkcji DLL w zarządzanym kodzie źródłowym, zobacz [Określanie punktu wejścia](specifying-an-entry-point.md).  
  
 Wywołanie platformy umożliwia sterowanie znaczną częścią systemu operacyjnego przez wywoływanie funkcji w interfejsie API systemu Windows i innych bibliotekach DLL. Oprócz interfejsu API systemu Windows istnieje wiele innych interfejsów API i bibliotek DLL dostępnych dla użytkownika za pomocą wywołania platformy.  
  
 W poniższej tabeli opisano kilka często używanych bibliotek DLL w interfejsie API systemu Windows.  
  
|DLL|Opis zawartości|  
|---------|-----------------------------|  
|GDI32.dll|Funkcje GDI (GDI) dla danych wyjściowych urządzenia, takie jak te na potrzeby rysowania i zarządzania czcionkami.|  
|Kernel32.dll|Funkcje systemu operacyjnego niskiego poziomu dla zarządzania pamięcią i obsługi zasobów.|  
|User32.dll|Funkcje zarządzania systemu Windows do obsługi komunikatów, czasomierzy, menu i komunikacji.|  
  
 Aby uzyskać pełną dokumentację dotyczącą interfejsu API systemu Windows, zobacz zestaw SDK platformy. Przykłady, które demonstrują sposób konstruowania. Deklaracje oparte na sieci, które mają być używane z wywołaniem platformy, można znaleźć w temacie [kierowanie danych za pomocą wywołania platformy](marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wykorzystywanie niezarządzanych funkcji DLL](consuming-unmanaged-dll-functions.md)
- [Określanie punktu wejścia](specifying-an-entry-point.md)
- [Tworzenie klasy utrzymującej funkcje DLL](creating-a-class-to-hold-dll-functions.md)
- [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md)
- [Wywołanie funkcji DLL](calling-a-dll-function.md)
