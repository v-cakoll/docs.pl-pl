---
title: Debugowanie statycznych funkcji globalnych
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
ms.openlocfilehash: c20d8719b63cb40074dc740506ae4a3c0fc3a251
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793778"
---
# <a name="debugging-global-static-functions"></a>Debugowanie statycznych funkcji globalnych
W tej sekcji opisano niezarządzane globalne funkcje statyczne używane przez interfejs API debugowania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [_EFN_GetManagedExcepStack, funkcja](efn-getmanagedexcepstack-function.md)  
 Dany adres obiektu wyjątku zarządzanego zwraca wersję ciągu śledzenia stosu zawartych wewnątrz.  
  
 [_EFN_GetManagedObjectFieldInfo, funkcja](efn-getmanagedobjectfieldinfo-function.md)  
 Pobiera przesunięcie od początku obiektu do pola i wartości pola przy użyciu podanego wskaźnika obiektu i nazwy pola.  
  
 [_EFN_GetManagedObjectName, funkcja](efn-getmanagedobjectname-function.md)  
 Pobiera nazwę typu za pomocą podanego wskaźnika obiektu zarządzanego.  
  
 [_EFN_StackTrace, funkcja](efn-stacktrace-function.md)  
 Przedstawia tekstową reprezentację zarządzanego śledzenia stosu i tablicę `CONTEXT` rekordów, po jednym dla każdego przejścia między niezarządzanym i zarządzanym kodem.  
  
 [CLRDataCreateInstance, funkcja](clrdatacreateinstance-function.md)  
 Wywoływane przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) w celu utworzenia określonego obiektu interfejsu dla określonego procesu docelowego.  
  
 [PFN_CLRDataCreateInstance, wskaźnik funkcji](pfn-clrdatacreateinstance-function-pointer.md)  
 Wskazuje funkcję, która jest wywoływana przez usługi dostępu do danych CLR w celu utworzenia określonego obiektu interfejsu dla określonego procesu docelowego.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Klasy coclass debugowania](debugging-coclasses.md)  
  
 [Debugowanie, interfejsy](debugging-interfaces.md)  
  
 [Debugowanie, wyliczenia](debugging-enumerations.md)  
  
 [Struktury debugowania](debugging-structures.md)
