---
title: Debugowanie statycznych funkcji globalnych
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2403d736d031aab52525fc12b5071e764a8bde1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-global-static-functions"></a>Debugowanie statycznych funkcji globalnych
W tej sekcji opisano niezarządzane statyczne funkcje globalne, które używa interfejsu API debugowania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [_EFN_GetManagedExcepStack, funkcja](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 Podany adres obiektu zarządzanym wyjątku zwraca ciąg wersji śladu stosu znajdująca się wewnątrz.  
  
 [_EFN_GetManagedObjectFieldInfo, funkcja](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 Pobiera przesunięcie od początku obiektu, do pola i wartość do pola, używając udostępnionego obiektu wskaźnik i nazwy pola.  
  
 [_EFN_GetManagedObjectName, funkcja](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 Pobiera nazwę typu przy użyciu wskaźnika podanego obiektu zarządzanego.  
  
 [_EFN_StackTrace, funkcja](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 Udostępnia reprezentację tekst ślad stosu zarządzanych i tablicę `CONTEXT` rejestruje, jeden dla każdego przejścia między niezarządzanych i kod zarządzany.  
  
 [CLRDataCreateInstance, funkcja](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 Metoda wywoływana przez wspólne języka wspólnego (CLR) danych dostęp do usługi można utworzyć obiektu określonego interfejsu dla procesu określonego obiektu docelowego.  
  
 [PFN_CLRDataCreateInstance, wskaźnik funkcji](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 Punkty do funkcji, która jest wywoływana przez danych CLR dostęp do usług można utworzyć obiektu określonego interfejsu dla procesu określonego obiektu docelowego.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Klasy coclass debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
