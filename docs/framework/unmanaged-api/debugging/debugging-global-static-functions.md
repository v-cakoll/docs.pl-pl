---
title: Debugowanie statycznych funkcji globalnych
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
ms.openlocfilehash: 965724c1e937fa62f05c33b0dcf8a5c8b9e1b029
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124319"
---
# <a name="debugging-global-static-functions"></a>Debugowanie statycznych funkcji globalnych
W tej sekcji opisano niezarządzane globalne funkcje statyczne używane przez interfejs API debugowania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [_EFN_GetManagedExcepStack, funkcja](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 Dany adres obiektu wyjątku zarządzanego zwraca wersję ciągu śledzenia stosu zawartych wewnątrz.  
  
 [_EFN_GetManagedObjectFieldInfo, funkcja](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 Pobiera przesunięcie od początku obiektu do pola i wartości pola przy użyciu podanego wskaźnika obiektu i nazwy pola.  
  
 [_EFN_GetManagedObjectName, funkcja](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 Pobiera nazwę typu za pomocą podanego wskaźnika obiektu zarządzanego.  
  
 [_EFN_StackTrace, funkcja](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 Przedstawia tekstową reprezentację zarządzanego śledzenia stosu i tablicę `CONTEXT` rekordów, po jednym dla każdego przejścia między niezarządzanym i zarządzanym kodem.  
  
 [CLRDataCreateInstance, funkcja](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 Wywoływane przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) w celu utworzenia określonego obiektu interfejsu dla określonego procesu docelowego.  
  
 [PFN_CLRDataCreateInstance, wskaźnik funkcji](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 Wskazuje funkcję, która jest wywoływana przez usługi dostępu do danych CLR w celu utworzenia określonego obiektu interfejsu dla określonego procesu docelowego.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Klasy coclass debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
