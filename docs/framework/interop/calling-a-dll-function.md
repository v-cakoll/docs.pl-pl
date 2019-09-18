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
ms.openlocfilehash: b842f44711d38a996b9d710dbe8bd369d30c5443
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051887"
---
# <a name="calling-a-dll-function"></a>Wywołanie funkcji DLL
Chociaż wywoływanie niezarządzanych funkcji DLL jest niemal identyczne z wywoływaniem innego kodu zarządzanego, istnieją różnice, które mogą sprawiać, że funkcje DLL pozornie pomyleją się w pierwszej kolejności. W tej sekcji przedstawiono tematy opisujące niektóre nietypowe problemy związane z wywoływaniem.  
  
 Struktury zwracane przez wywołania wywołania platformy muszą być typami danych, które mają taką samą reprezentację w kodzie zarządzanym i niezarządzanym. Typy takie są nazywane *danych kopiowalnych* , ponieważ nie wymagają konwersji (zobacz [typy danych kopiowalnych i danych kopiowalnych](blittable-and-non-blittable-types.md)). Aby wywołać funkcję, która ma strukturę niedanych kopiowalnychną jako typ zwracany, można zdefiniować typ pomocnika danych kopiowalnych o takim samym rozmiarze co typ inny niż danych kopiowalnych i przekonwertować dane po powrocie funkcji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przekazywanie struktur](passing-structures.md)  
 Identyfikuje problemy z przekazywaniem struktur danych ze wstępnie zdefiniowanym układem.  
  
 [Funkcje wywołania zwrotnego](callback-functions.md)  
 Zawiera podstawowe informacje na temat funkcji wywołania zwrotnego.  
  
 [Instrukcje: Implementowanie funkcji wywołania zwrotnego](how-to-implement-callback-functions.md)  
 Opisuje sposób implementowania funkcji wywołania zwrotnego w kodzie zarządzanym.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wykorzystywanie niezarządzanych funkcji DLL](consuming-unmanaged-dll-functions.md)  
 Opisuje sposób wywoływania niezarządzanych funkcji DLL przy użyciu wywołania platformy.  
  
 [Marshaling danych w wywołaniu platformy](marshaling-data-with-platform-invoke.md)  
 Opisuje sposób deklarowania parametrów metody i przekazywania argumentów do funkcji wyeksportowanych przez niezarządzane biblioteki.
