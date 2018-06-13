---
title: Funkcje wywołania zwrotnego
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4494eda29ca6065a157869ec2f93b4875391824
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397393"
---
# <a name="callback-functions"></a>Funkcje wywołania zwrotnego
Funkcja wywołania zwrotnego jest kod w zarządzanej aplikacji, która pomaga w funkcji niezarządzanej DLL wykonania zadania. Wywołania funkcji wywołania zwrotnego przekazywania pośrednio z zarządzanych aplikacji, za pomocą funkcji DLL i z powrotem do zarządzaną implementację. Niektóre z wielu funkcji DLL wywoływana z platformą wywołania funkcja wywołania zwrotnego w kodzie zarządzanym do prawidłowego działania.  
  
 Aby wywołać większość funkcji DLL z kodu zarządzanego, tworzenie zarządzanej definicji funkcji, a następnie wywołać ją. Proces jest prosta.  
  
 Przy użyciu funkcji DLL, która wymaga funkcji wywołania zwrotnego ma kilka dodatkowych kroków. Najpierw należy określić, czy funkcja wymaga wywołania zwrotnego, analizując dokumentacji dla funkcji. Następnie należy utworzyć działanie funkcji wywołania zwrotnego w zarządzanych aplikacji. Ponadto wywołanie funkcji DLL przekazanie wskaźnika do funkcji wywołania zwrotnego jako argument. Poniższej ilustracji przedstawiono następujące kroki.  
  
 ![Wywołanie platformy wywołania zwrotnego](../../../docs/framework/interop/media/pinvokecallback.gif "pinvokecallback")  
Funkcja wywołania zwrotnego i wdrażanie  
  
 Funkcje wywołania zwrotnego idealnie nadają się do użytku w sytuacjach, w których zadanie jest wykonywane wielokrotnie. Innego użycie wspólnych jest wyliczenie funkcje takie jak **EnumFontFamilies**, **EnumPrinters**, i **EnumWindows** w interfejsie API Win32. **EnumWindows** funkcja wylicza wszystkie istniejące systemu windows na komputerze, wywołanie funkcji wywołania zwrotnego do wykonywania zadań na każde okno. Aby uzyskać instrukcje i przykładem, zobacz [porady: Implementowanie funkcji wywołania zwrotnego](../../../docs/framework/interop/how-to-implement-callback-functions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Implementowanie funkcji wywołania zwrotnego](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 [Wywołanie funkcji DLL](../../../docs/framework/interop/calling-a-dll-function.md)
