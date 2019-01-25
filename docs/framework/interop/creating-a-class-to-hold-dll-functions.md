---
title: Tworzenie klasy utrzymującej funkcje DLL
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5718c70597acc6919c697a9033e8593865e60a2d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745041"
---
# <a name="creating-a-class-to-hold-dll-functions"></a>Tworzenie klasy utrzymującej funkcje DLL
Zawijanie często używanych funkcji DLL w klasie zarządzanej jest efektywne podejście do hermetyzacji funkcje platformy. Chociaż nie jest wymagane, aby to zrobić w każdym przypadku, zapewniając otoka klasy jest wygodne, ponieważ Definiowanie funkcji DLL może być skomplikowane i podatne na błędy. Jeśli programujesz w języku Visual Basic lub C#, należy zadeklarować funkcji DLL w obrębie klasy lub w module języka Visual Basic.  
  
 W obrębie klasy można zdefiniować metody statycznej dla każdej funkcji DLL, który ma zostać wywołana. Definicja może zawierać dodatkowe informacje, takie jak zestaw znaków lub konwencji wywoływania, używane do przekazywania argumentów metody; pomijając te informacje, możesz wybrać ustawienia domyślne. Aby uzyskać pełną listę opcji deklaracji i domyślne ustawienia, zobacz [tworzenie prototypów w kodzie zarządzany](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).  
  
 Po opakowaniu można wywołać metody w klasie, jak wywołanie metody statycznej na inne klasy. Obsługuje wywołania platformy bazowej automatycznie wyeksportowanej funkcji.  
  
 Podczas projektowania klas zarządzanych dla platformy wywołać, należy wziąć pod uwagę relacji między klasami i funkcji DLL. Możesz na przykład:  
  
-   Deklarowanie funkcji DLL w ramach istniejącej klasy.  
  
-   Utwórz klasę poszczególnych dla każdej funkcji DLL, utrzymywanie funkcji w izolowanej i łatwe do znalezienia.  
  
-   Utwórz jedną klasę zbiór powiązanych funkcji DLL, które tworzą logiczne grupowanie i zmniejszyć obciążenie.  
  
 Możesz nazwać klasy i jego metod, jak należy. Aby uzyskać przykłady pokazujące, jak utworzyć. Na podstawie NET deklaracje do użycia z platformą wywołania, zobacz [Marshaling danych za pomocą wywołania platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Zobacz także
- [Wykorzystywanie niezarządzanych funkcji DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
- [Identyfikowanie funkcji w bibliotekach DLL](../../../docs/framework/interop/identifying-functions-in-dlls.md)
- [Tworzenie prototypów w kodzie zarządzanym](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [Wywołanie funkcji DLL](../../../docs/framework/interop/calling-a-dll-function.md)
