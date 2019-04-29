---
title: Wywołanie funkcji DLL
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98d363b6c0838ff1211d969391f04ce8ccddd003
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643572"
---
# <a name="calling-a-dll-function"></a>Wywołanie funkcji DLL
Wywoływanie niezarządzanych funkcji DLL jest niemal identyczne do wywoływania innego kodu zarządzanego, istnieją różnice, które mogą ułatwić funkcji DLL wydawać się niejasne na początku. Ta sekcja wprowadza tematach opisano niektóre nietypowe problemy związane z wywołaniem.  
  
 Wywołania struktury, które są zwracane z platformy musi być typy danych, które mają tę samą reprezentację w kodzie zarządzanym i niezarządzanym. Typy takie są nazywane *kopiowalnymi* , ponieważ nie wymaga konwersji (zobacz [Kopiowalne i typy danych Kopiowalnych inne niż](../../../docs/framework/interop/blittable-and-non-blittable-types.md)). Aby wywołać funkcję, która ma strukturę niekopiowalnych jako jego typem zwracanym, może definiowaniu typu Pomocnika danych kopiowalnych taki sam rozmiar jak typ niekopiowalnych i konwersji danych, po powrocie funkcji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przekazywanie struktur](../../../docs/framework/interop/passing-structures.md)  
 Identyfikuje problemy dotyczące przekazywania struktur danych przy użyciu wstępnie zdefiniowanego układu.  
  
 [Funkcje wywołania zwrotnego](../../../docs/framework/interop/callback-functions.md)  
 Zawiera podstawowe informacje o funkcjach wywołania zwrotnego.  
  
 [Instrukcje: Implementowanie funkcji wywołania zwrotnego](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 Opisuje sposób implementacji funkcji wywołania zwrotnego w kodzie zarządzanym.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wykorzystywanie niezarządzanych funkcji DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 W tym artykule opisano sposób wywoływania niezarządzanego wywoływanie funkcji DLL za pomocą platformy.  
  
 [Marshaling danych w wywołaniu platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 W tym artykule opisano, jak deklarować parametrów metod i przekazywać argumenty do funkcji eksportowanych przez niezarządzanych bibliotek.
