---
title: Funkcje wywołania zwrotnego
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
ms.openlocfilehash: 8b8bb4dff4f73247282060c0b4fd778ae0169b1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181518"
---
# <a name="callback-functions"></a>Funkcje wywołania zwrotnego
Funkcja wywołania zwrotnego to kod w ramach zarządzanej aplikacji, który pomaga niezarządzanej funkcji DLL wykonać zadanie. Wywołania funkcji wywołania zwrotnego przechodzą pośrednio z zarządzanej aplikacji, za pośrednictwem funkcji DLL i z powrotem do implementacji zarządzanej. Niektóre z wielu funkcji DLL wywoływanych za pomocą wywołania platformy wymagają funkcji wywołania zwrotnego w kodzie zarządzanym, aby działać poprawnie.  
  
 Aby wywołać większość funkcji DLL z kodu zarządzanego, należy utworzyć zarządzaną definicję funkcji, a następnie wywołać go. Proces jest prosty.  
  
 Za pomocą funkcji DLL, która wymaga funkcji wywołania zwrotnego ma kilka dodatkowych kroków. Najpierw należy określić, czy funkcja wymaga wywołania zwrotnego, patrząc na dokumentację funkcji. Następnie należy utworzyć funkcję wywołania zwrotnego w aplikacji zarządzanej. Na koniec wywołać funkcję DLL, przekazując wskaźnik do funkcji wywołania zwrotnego jako argument.

 Na poniższej ilustracji podsumowano kroki funkcji wywołania zwrotnego i implementacji:  
  
 ![Diagram przedstawiający proces wywołania zwrotnego na platformie.](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 Funkcje wywołania zwrotnego są idealne do użycia w sytuacjach, w których zadanie jest wykonywane wielokrotnie. Innym typowym zastosowaniem są funkcje wyliczenia, takie jak **EnumFontFamilies**, **EnumPrinters**i **EnumWindows** w interfejsie API systemu Windows. **Funkcja EnumWindows wylicza** wszystkie istniejące okna na komputerze, wywołując funkcję wywołania zwrotnego w celu wykonania zadania w każdym oknie. Aby uzyskać instrukcje i przykład, zobacz [Jak: Implementowanie funkcji wywołania zwrotnego](how-to-implement-callback-functions.md).  
  
## <a name="see-also"></a>Zobacz też

- [Porady: implementowanie funkcji wywołania zwrotnego](how-to-implement-callback-functions.md)
- [Wywołanie funkcji DLL](calling-a-dll-function.md)
