---
title: "Tworzenie klasy utrzymującej funkcje DLL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ac3c3542e46168f5903ff0425740a29f16253733
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-class-to-hold-dll-functions"></a>Tworzenie klasy utrzymującej funkcje DLL
Zawijanie często używanych funkcji DLL w klasie zarządzanej jest efektywnym sposobem Hermetyzowanie funkcjonalność platformy. Chociaż nie jest to konieczne, aby to zrobić w każdym przypadku, podając otoki klasy jest wygodne, ponieważ definiujący funkcje DLL może być skomplikowane i podatne na błędy. Programowanie w Visual Basic lub C# musisz zadeklarować funkcji DLL w obrębie klasy lub module języka Visual Basic.  
  
 W obrębie klasy należy zdefiniować statycznej metody dla każdej funkcji DLL, który ma zostać wywołana. Definicja może zawierać dodatkowe informacje, takie jak zestaw znaków lub Konwencja wywoływania używany do przekazywania argumenty metody; pomijając te informacje, wybierz ustawienia domyślne. Pełną listę opcji deklaracji i domyślne ustawienia, zobacz [tworzenie prototypów w kodzie zarządzane](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).  
  
 Po opakowaniu mogą wywoływać metod w funkcji, jak wywoływać metod w statycznej funkcji. Wywołanie platformy uchwytów odpowiadającego wyeksportowanej funkcji automatycznie.  
  
 Podczas projektowania zarządzanej klasy dla platformy wywołania, należy wziąć pod uwagę relacje między klasy i funkcje biblioteki DLL. Możesz na przykład:  
  
-   Deklarowanie funkcji DLL w ramach istniejącej klasy.  
  
-   Utwórz poszczególnych klas dla każdej funkcji DLL, zachowanie funkcji w izolowanej i łatwe do odnalezienia.  
  
-   Utwórz jedną klasę dla zestawu powiązanych funkcji DLL tworzą logiczne grupy i zmniejsza obciążenie.  
  
 Można określić nazwę klasy i metody jako użytkownik należy. Aby uzyskać przykłady pokazujące, które pokazują, jak utworzyć. Deklaracje opartych na potrzeby używania z platformy invoke, zobacz [organizowanie danych za pomocą wywołania platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wykorzystywanie niezarządzanych funkcji DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [Identyfikowanie funkcji w bibliotekach DLL](../../../docs/framework/interop/identifying-functions-in-dlls.md)  
 [Tworzenie prototypów w kodzie zarządzanym](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [Wywoływanie funkcji DLL](../../../docs/framework/interop/calling-a-dll-function.md)
