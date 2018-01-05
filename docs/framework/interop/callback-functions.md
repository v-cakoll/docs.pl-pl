---
title: "Funkcje wywołania zwrotnego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c4f39160e817ce04c5c15fb8299852a052d36c25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
