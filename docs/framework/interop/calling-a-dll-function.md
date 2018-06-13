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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387136"
---
# <a name="calling-a-dll-function"></a>Wywołanie funkcji DLL
Wywoływanie niezarządzanych funkcji DLL jest niemal identyczny jak wywołanie innego kodu zarządzanego, istnieją różnice, które mogą ułatwić funkcji DLL wydaje się być mylące na początku. W tej sekcji przedstawiono tematach opisano niektóre z nietypowych problemów związanych z wywołaniem.  
  
 Struktury, które są zwracane z platformy wywołania wywołania musi być typów danych, które mają taką samą reprezentację w kodzie zarządzane i niezarządzane. Takie typy są nazywane *typy kopiowalne* , ponieważ nie wymaga konwersji (zobacz [Kopiowalne i typy Kopiowalne inne niż](../../../docs/framework/interop/blittable-and-non-blittable-types.md)). Aby wywołać funkcję, która ma strukturę niekopiowalne jako jej typu zwracanego, można zdefiniować typu pomocnika kopiowalne ten sam rozmiar jako typ niekopiowalne i Konwertuj dane po funkcja zwraca wartość.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przekazywanie struktur](../../../docs/framework/interop/passing-structures.md)  
 Identyfikuje problemy przekazywanie struktur danych z układem wstępnie zdefiniowane.  
  
 [Funkcje wywołania zwrotnego](../../../docs/framework/interop/callback-functions.md)  
 Zawiera podstawowe informacje o funkcji wywołania zwrotnego.  
  
 [Instrukcje: Implementowanie funkcji wywołania zwrotnego](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 Opisuje sposób Implementowanie funkcji wywołania zwrotnego w kodzie zarządzanym.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wykorzystywanie niezarządzanych funkcji DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 Opisuje sposób wywoływania niezarządzanego wywołanie funkcji DLL przy użyciu platformy.  
  
 [Marshaling danych w wywołaniu platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 Opisuje sposób deklarowanie parametrów metod i przekazywanie argumentów do funkcji wyeksportowane przez niezarządzanych bibliotek.
