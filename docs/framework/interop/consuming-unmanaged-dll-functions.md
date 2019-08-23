---
title: Wykorzystywanie niezarządzanych funkcji DLL
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- platform invoke, about platform invoke
- DLL functions, consuming unmanaged
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke
- DLL functions
ms.assetid: eca7606e-ebfb-4f47-b8d9-289903fdc045
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e9308d6bf0eefaa60af17a721cd1c26827469eb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946845"
---
# <a name="consuming-unmanaged-dll-functions"></a>Wykorzystywanie niezarządzanych funkcji DLL
Wywołanie platformy to usługa, która umożliwia kodowi zarządzanemu wywoływanie funkcji niezarządzanych wdrożonych w bibliotekach dołączanych dynamicznie (dll), takich jak te w interfejsie API systemu Windows. Lokalizuje i wywołuje wyeksportowaną funkcję i kierującie jej argumentów (liczbami całkowitymi, ciągami, tablicami, strukturami itd.) w granicach międzyoperacyjnych, zgodnie z wymaganiami.  
  
 W tej sekcji przedstawiono zadania związane z wykorzystywaniem niezarządzanych funkcji DLL i podano więcej informacji na temat wywołania platformy. Oprócz następujących zadań istnieją ogólne zagadnienia i link zawierający dodatkowe informacje i przykłady.  
  
#### <a name="to-consume-exported-dll-functions"></a>Aby korzystać z wyeksportowanych funkcji DLL  
  
1. [Zidentyfikuj funkcje w bibliotekach DLL](../../../docs/framework/interop/identifying-functions-in-dlls.md).  
  
     W minimalnym stopniu należy określić nazwę funkcji i nazwy biblioteki DLL, która ją zawiera.  
  
2. [Utwórz klasę, aby przechowywać funkcje DLL](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).  
  
     Można użyć istniejącej klasy, utworzyć pojedynczą klasę dla każdej funkcji niezarządzanej lub utworzyć jedną klasę, która zawiera zestaw powiązanych funkcji niezarządzanych.  
  
3. [Tworzenie prototypów w kodzie zarządzanym](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).  
  
     [Visual Basic] Użyj instrukcji **DECLARE** ze słowami kluczowymi **funkcji** i **lib** . W niektórych rzadkich przypadkach można użyć **DllImportAttribute** ze słowami kluczowymi **funkcji udostępnionych** . Te przypadki zostały omówione w dalszej części tej sekcji.  
  
     [C#] Użyj parametru **DllImportAttribute** , aby zidentyfikować bibliotekę DLL i funkcję. Oznacz metodę za pomocą modyfikatorów **static** i **extern** .  
  
     [C++] Użyj parametru **DllImportAttribute** , aby zidentyfikować bibliotekę DLL i funkcję. Oznacz metodę otoki lub funkcję **nieextern "C"** .  
  
4. [Wywoływanie funkcji DLL](../../../docs/framework/interop/calling-a-dll-function.md).  
  
     Wywołaj metodę w klasie zarządzanej, tak jak każdą inną zarządzaną metodę. [Przekazywanie struktur](../../../docs/framework/interop/passing-structures.md) i [Implementowanie funkcji wywołania zwrotnego](../../../docs/framework/interop/callback-functions.md) to specjalne przypadki.  
  
 Przykłady, które demonstrują sposób konstruowania. Deklaracje oparte na sieci, które mają być używane z wywołaniem platformy, można znaleźć w temacie [kierowanie danych za pomocą wywołania platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="a-closer-look-at-platform-invoke"></a>Bliższe spojrzenie na wywołanie platformy  
 Wywołanie platformy polega na metadanych, aby znaleźć eksportowane funkcje i zorganizować ich argumenty w czasie wykonywania. Na poniższej ilustracji przedstawiono ten proces.  
  
 ![Diagram przedstawiający wywołanie wywołania platformy.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 Gdy wywołanie platformy wywołuje niezarządzaną funkcję, wykonuje następującą sekwencję akcji:  
  
1. Lokalizuje bibliotekę DLL zawierającą funkcję.  
  
2. Ładuje bibliotekę DLL do pamięci.  
  
3. Lokalizuje adres funkcji w pamięci i wypychanie jej argumentów na stos, kierując dane zgodnie z potrzebami.  
  
    > [!NOTE]
    > Lokalizowanie i ładowanie biblioteki DLL oraz lokalizowanie adresu funkcji w pamięci występuje tylko po pierwszym wywołaniu funkcji.  
  
4. Przenosi kontrolę do funkcji niezarządzanej.  
  
 Wywołanie platformy zgłasza wyjątki wygenerowane przez niezarządzaną funkcję do zarządzanego obiektu wywołującego.

## <a name="see-also"></a>Zobacz także

- [Współdziałanie z kodem niezarządzanym](../../../docs/framework/interop/index.md)
- [Przykłady wywołań platformy](../../../docs/framework/interop/platform-invoke-examples.md)
- [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
