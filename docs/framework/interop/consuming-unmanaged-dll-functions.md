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
ms.openlocfilehash: 50bfcf5c27236ca704a24f49128becfbee716c21
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463088"
---
# <a name="consuming-unmanaged-dll-functions"></a>Wykorzystywanie niezarządzanych funkcji DLL
Wywołanie platformy jest usługą, że umożliwia zarządzanemu kodowi wywoływanie funkcji niezarządzanych zaimplementowane w biblioteki dołączanej dynamicznie (dll), takich jak te w interfejsie API Windows. Lokalizuje i wywołuje eksportowanych funkcji i kieruje argumentów (liczby całkowite, ciągi, tablice, struktur i tak dalej) wewnątrz międzyoperacyjnej granicy, zgodnie z potrzebami.  
  
 Ta sekcja wprowadza zadań skojarzonych z wykorzystywanie niezarządzanych funkcji DLL i zawiera więcej informacji na temat platformy wywołania. Oprócz następujących zadań istnieją Ogólne zagadnienia i łącza, zapewniając dodatkowe informacje i przykłady.  
  
#### <a name="to-consume-exported-dll-functions"></a>Korzystanie z wyeksportowanych funkcji DLL  
  
1.  [Identyfikowanie funkcji w bibliotekach DLL](../../../docs/framework/interop/identifying-functions-in-dlls.md).  
  
     Minimalny zestaw należy określić nazwę funkcji i nazwa pliku dll, który go zawiera.  
  
2.  [Tworzenie klasy utrzymującej funkcje DLL](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).  
  
     Można użyć istniejącej klasy, tworzenia poszczególnych klas dla każdej funkcji niezarządzanej lub utworzyć jedną klasę, która zawiera zbiór powiązanych funkcji niezarządzanych.  
  
3.  [Tworzenie prototypów w kodzie zarządzanym](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).  
  
     [Visual Basic] Użyj **Declare** instrukcję, określając **funkcja** i **Lib** słów kluczowych. W rzadkich przypadkach można użyć **DllImportAttribute** z **funkcji udostępnionych** słów kluczowych. Te przypadki zostały omówione w dalszej części w tej sekcji.  
  
     [C#] Użyj **DllImportAttribute** do identyfikowania biblioteki DLL i funkcji. Oznacz metodę z **statyczne** i **extern** modyfikatorów.  
  
     [C++] Użyj **DllImportAttribute** do identyfikowania biblioteki DLL i funkcji. Oznaczenia metody otoki lub funkcją **extern "C"**.  
  
4.  [Wywoływanie funkcji DLL](../../../docs/framework/interop/calling-a-dll-function.md).  
  
     Wywołaj metodę w klasie zarządzanej tak jak każda inna metoda zarządzanych. [Przekazywanie struktur](../../../docs/framework/interop/passing-structures.md) i [Implementowanie funkcji wywołania zwrotnego](../../../docs/framework/interop/callback-functions.md) są specjalne przypadki.  
  
 Aby uzyskać przykłady pokazujące, jak utworzyć. Na podstawie NET deklaracje do użycia z platformą wywołania, zobacz [Marshaling danych za pomocą wywołania platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="a-closer-look-at-platform-invoke"></a>Im bliżej wywołania platformy  
 Wywołanie platformy opiera się na metadanych w celu zlokalizowania wyeksportowanych funkcji i kierowania ich argumentów w czasie wykonywania. Poniższa ilustracja przedstawia ten proces.  
  
 ![Diagram przedstawiający platformę wywołania wywołania.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 Gdy wywołanie platformy wywołania funkcji niezarządzanej, wykonuje następującą sekwencję czynności:  
  
1.  Lokalizuje biblioteki DLL zawierającej funkcję.  
  
2.  Ładuje bibliotekę DLL do pamięci.  
  
3.  Lokalizuje adres funkcji w pamięci, a następnie wypycha argumenty na stosie, organizowanie danych zgodnie z potrzebami.  
  
    > [!NOTE]
    >  Lokalizowanie i ładowanie biblioteki DLL i lokalizowanie adres funkcji w pamięci odbywa się tylko przy pierwszym wywołaniu funkcji.  
  
4.  Transfer kontroli do funkcji niezarządzanych.  
  
 Wywołanie platformy zgłasza wyjątki generowane przez funkcję niezarządzane do zarządzanego obiektu wywołującego.

## <a name="see-also"></a>Zobacz także
- [Współdziałanie z kodem niezarządzanym](../../../docs/framework/interop/index.md)
- [Przykłady wywołań platformy](../../../docs/framework/interop/platform-invoke-examples.md)
- [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
