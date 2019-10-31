---
title: Funkcje wywołania zwrotnego
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
ms.openlocfilehash: 0fbf6df93e3ef9ee6380ed35f98018d157599e2a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123741"
---
# <a name="callback-functions"></a>Funkcje wywołania zwrotnego
Funkcja wywołania zwrotnego jest kodem w aplikacji zarządzanej, która ułatwia wykonywanie zadania przez niezarządzaną funkcję DLL. Wywołania funkcji wywołania zwrotnego są przekazywane pośrednio z aplikacji zarządzanej za pośrednictwem funkcji DLL i z powrotem do zarządzanej implementacji. Niektóre z wielu funkcji DLL wywoływanych za pomocą wywołania platformy wymagają poprawnego działania funkcji wywołania zwrotnego w kodzie zarządzanym.  
  
 Aby wywołać większość funkcji DLL z kodu zarządzanego, należy utworzyć zarządzaną definicję funkcji, a następnie wywołać ją. Proces jest prosty.  
  
 Użycie funkcji DLL, która wymaga funkcji wywołania zwrotnego, zawiera kilka dodatkowych kroków. Najpierw należy określić, czy funkcja wymaga wywołania zwrotnego, przeglądając dokumentację funkcji. Następnie musisz utworzyć funkcję wywołania zwrotnego w aplikacji zarządzanej. Na koniec należy wywołać funkcję DLL, przekazując wskaźnik do funkcji wywołania zwrotnego jako argument. 
 
 Poniższa ilustracja zawiera podsumowanie funkcji wywołania zwrotnego i kroków implementacji:  
  
 ![Diagram przedstawiający proces wywołania zwrotnego platformy.](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 Funkcje wywołania zwrotnego są idealne do użycia w sytuacjach, w których zadanie jest wykonywane wielokrotnie. Innym typowym użyciem jest z funkcjami wyliczania, takimi jak **EnumFontFamilies**, **EnumPrinters**i **EnumWindows** w interfejsie API systemu Windows. Funkcja **EnumWindows** wylicza wszystkie istniejące okna na komputerze, wywołując funkcję wywołania zwrotnego do wykonania zadania w poszczególnych oknach. Aby uzyskać instrukcje i przykład, zobacz [How to: Implementuj funkcje wywołania zwrotnego](how-to-implement-callback-functions.md).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Implementowanie funkcji wywołania zwrotnego](how-to-implement-callback-functions.md)
- [Wywołanie funkcji DLL](calling-a-dll-function.md)
