---
title: Debugowanie statycznych funkcji globalnych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7fde0941959619f4832019806401be0ffddb81e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
