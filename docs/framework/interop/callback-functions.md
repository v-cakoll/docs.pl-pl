---
title: Funkcje wywołania zwrotnego
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65f5e11a8fb40527387c14cdd8dec7f0bfc5c697
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196999"
---
# <a name="callback-functions"></a>Funkcje wywołania zwrotnego
Funkcja wywołania zwrotnego jest kod w zarządzanej aplikacji, która pomaga niezarządzanych funkcji DLL ukończenia zadania. Wywołania do funkcji wywołania zwrotnego przekazać pośrednio z aplikacji zarządzanych, za pomocą funkcji DLL i z powrotem do zarządzaną implementację. Niektóre z wielu funkcji DLL o nazwie z platformą wywołania wymagają funkcji wywołania zwrotnego w kodzie zarządzanym działać prawidłowo.  
  
 Aby wywołać większość funkcji DLL z kodu zarządzanego, tworzenie zarządzanych definicji funkcji, a następnie wywołać ją. Ten proces jest bardzo proste.  
  
 Za pomocą funkcji biblioteki DLL, która wymaga funkcji wywołania zwrotnego ma kilka dodatkowych kroków. Najpierw należy określić, czy funkcja wymaga wywołania zwrotnego, analizując w dokumentacji dotyczącej funkcji. Następnie należy utworzyć funkcję wywołania zwrotnego w zarządzanej aplikacji. Na koniec wywołania funkcji DLL przekazywania wskaźnika do funkcji wywołania zwrotnego jako argument. 
 
 Poniższa ilustracja zawiera podsumowanie kroków funkcji i implementacji wywołania zwrotnego:  
  
 ![Diagram przedstawiający platformy wywołania zwrotnego procesu.](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 Funkcje wywołania zwrotnego to idealne rozwiązanie w sytuacjach, w których zadanie jest wykonywane wielokrotnie. Inny wspólne użycie jest przy użyciu funkcji wyliczania, takich jak **EnumFontFamilies**, **EnumPrinters**, i **EnumWindows** w interfejsie API Windows. **EnumWindows** funkcja wylicza wszystkie istniejące systemu windows na komputerze, w wywołaniu funkcji wywołania zwrotnego do wykonywania zadań na każde okno. Aby uzyskać instrukcje i przykłady, zobacz [jak: Implementowanie funkcji wywołania zwrotnego](../../../docs/framework/interop/how-to-implement-callback-functions.md).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Implementowanie funkcji wywołania zwrotnego](../../../docs/framework/interop/how-to-implement-callback-functions.md)
- [Wywołanie funkcji DLL](../../../docs/framework/interop/calling-a-dll-function.md)
