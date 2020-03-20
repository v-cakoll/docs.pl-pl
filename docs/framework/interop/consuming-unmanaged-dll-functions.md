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
ms.openlocfilehash: 7ec1f129dcc19300dd5a4e7c5e627d9e0edf29a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399974"
---
# <a name="consuming-unmanaged-dll-functions"></a>Wykorzystywanie niezarządzanych funkcji DLL
Wywołanie platformy to usługa, która umożliwia kodowi zarządzanemu wywoływanie niezarządzanych funkcji zaimplementowanych w bibliotekach łączy dynamicznych (bibliotek dll), takich jak te w interfejsie API systemu Windows. Lokalizuje i wywołuje wyeksportowane funkcji i marshals jego argumenty (liczby całkowite, ciągi, tablice, struktury i tak dalej) w całej granicy współdziałania w razie potrzeby.  
  
 W tej sekcji przedstawiono zadania związane z korzystaniem z niezarządzanych funkcji DLL i zawiera więcej informacji na temat wywoływania platformy. Oprócz następujących zadań istnieją ogólne zagadnienia i łącze zawierające dodatkowe informacje i przykłady.  
  
#### <a name="to-consume-exported-dll-functions"></a>Aby korzystać z eksportowanych funkcji biblioteki DLL  
  
1. [Identyfikowanie funkcji w bibliotekach DLL](identifying-functions-in-dlls.md).  
  
     Minimalnie należy określić nazwę funkcji i nazwę biblioteki DLL, która ją zawiera.  
  
2. [Utwórz klasę do przechowywania funkcji DLL](creating-a-class-to-hold-dll-functions.md).  
  
     Można użyć istniejącej klasy, utworzyć indywidualną klasę dla każdej funkcji niezarządzanej lub utworzyć jedną klasę zawierającą zestaw powiązanych funkcji niezarządzanych.  
  
3. [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md).  
  
     [Visual Basic] Użyj **Declare** instrukcji z **funkcji** i **Lib** słowa kluczowego. W niektórych rzadkich przypadkach można użyć **DllImportAttribute** z **shared function** słowa kluczowego. Przypadki te są wyjaśnione w dalszej części tej sekcji.  
  
     [C#] Użyj **DllImportAttribute** do identyfikowania biblioteki DLL i funkcji. Oznacz metodę za pomocą modyfikatorów **statycznych** i **extern.**  
  
     [C++] Użyj **DllImportAttribute** do identyfikowania biblioteki DLL i funkcji. Oznacz metodę otoki lub funkcję za pomocą **eksternu "C"**.  
  
4. [Wywołanie funkcji DLL](calling-a-dll-function.md).  
  
     Wywołanie metody w klasie zarządzanej, jak każda inna metoda zarządzana. [Przekazywanie struktur](passing-structures.md) i [implementowanie funkcji wywołania zwrotnego](callback-functions.md) są szczególnymi przypadkami.  
  
 Przykłady, które pokazują, jak konstruować . Deklaracje oparte na sieci, które mają być używane z wywołaniem platformy, zobacz [Kierowanie danych za pomocą platformy Invoke](marshaling-data-with-platform-invoke.md).  
  
## <a name="a-closer-look-at-platform-invoke"></a>Bliższe spojrzenie na platformę wywołać  
 Wywołanie platformy opiera się na metadanych, aby zlokalizować eksportowane funkcje i marshal ich argumentów w czasie wykonywania. Ten proces przedstawiono na poniższej ilustracji.  
  
 ![Diagram, który pokazuje wywołanie wywołania platformy.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 Gdy platforma wywołać niezarządzaną funkcję, wykonuje następującą sekwencję akcji:  
  
1. Lokalizuje bibliotekę DLL zawierającą funkcję.  
  
2. Ładuje bibliotekę DLL do pamięci.  
  
3. Lokalizuje adres funkcji w pamięci i wypycha jego argumenty na stosie, rozsyłania danych zgodnie z wymaganiami.  
  
    > [!NOTE]
    > Lokalizowanie i ładowanie biblioteki DLL i lokalizowanie adresu funkcji w pamięci występuje tylko przy pierwszym wywołaniu funkcji.  
  
4. Przenosi kontrolę do funkcji niezarządzanej.  
  
 Platforma wywołać zgłasza wyjątki generowane przez funkcję niezarządzane do zarządzanego wywołującego.

## <a name="see-also"></a>Zobacz też

- [Współdziałanie z kodem niezarządzanym](index.md)
- [Przykłady wywołań platformy](platform-invoke-examples.md)
- [Organizowanie międzyoperacyjne](interop-marshaling.md)
