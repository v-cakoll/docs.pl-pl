---
title: Marshaling ciągów
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, samples
- platform invoke, marshaling data
- data marshaling, strings
- data marshaling, samples
- data marshaling, platform invoke
- marshaling. strings
- marshaling, platform invoke
- sample applications [.NET Framework], marshaling strings
ms.assetid: e21b078b-70fb-4905-be26-c097ab2433ff
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc4f40ab954a3bb31e0b55aad8c00ed2ee63f6c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514897"
---
# <a name="marshaling-strings"></a>Marshaling ciągów
Wywołanie platformy parametry ciągu kopii, konwersję z formatu .NET Framework (Unicode) do formatu niezarządzane (ANSI), jeśli to konieczne. Ponieważ ciągi zarządzane są niezmienne, wywołanie platformy nie kopiuje ich powrót po awarii z niezarządzanej pamięci do pamięci zarządzanej, gdy funkcja zwraca.  
  
 Poniższej tabeli wymieniono opcje marshaling dla ciągów, w tym artykule opisano ich użycie i Link do odpowiedniego przykładowe .NET Framework.  
  
|String|Opis|Przykład|  
|------------|-----------------|------------|  
|Według wartości.|Przekazuje parametry, tak jak parametry.|[MsgBox](msgbox-sample.md)|  
|W wyniku.|Zwraca ciągi z niezarządzanego kodu.|[Ciągi](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))|  
|Przez odwołanie.|Przekazuje ciągi jako We/Wy przy użyciu parametrów <xref:System.Text.StringBuilder>.|[Bufory](https://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100))|  
|W strukturze przez wartość.|Przekazuje parametry to struktura, która jest parametrem In.|[Struktury](https://msdn.microsoft.com/library/96a62265-dcf9-4608-bc0a-1f762ab9f48e(v=vs.100))|  
|W strukturze przez odwołanie **(char\*)**.|Przekazuje parametry to struktura, która jest parametrem we/wy. Niezarządzanej funkcji oczekuje wskaźnika do buforu znaków i rozmiar buforu jest elementem członkowskim struktury.|[Ciągi](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))|  
|W strukturze przez odwołanie **(char[])**.|Przekazuje parametry to struktura, która jest parametrem we/wy. Niezarządzanej funkcji oczekuje osadzonego buforu znaku.|[OSInfo](https://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455(v=vs.100))|  
|W klasie według wartości **(char\*)**.|Przekazuje parametry w klasie (klasy jest parametrem We/Wy). Niezarządzanej funkcji oczekuje wskaźnika do buforu znaków.|[OpenFileDlg](https://msdn.microsoft.com/library/b7dea792-cb92-4baf-ac7b-6a24803e6c75(v=vs.100))|  
|W klasie według wartości **(char[])**.|Przekazuje parametry w klasie (klasy jest parametrem We/Wy). Niezarządzanej funkcji oczekuje osadzonego buforu znaku.|[OSInfo](https://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455(v=vs.100))|  
|Jako tablicę ciągów według wartości.|Tworzy tablicę ciągów, który jest przekazywany przez wartość.|[Tablice](marshaling-different-types-of-arrays.md)|  
|Jako tablica struktur, które zawierają ciągi według wartości.|Tworzy tablicę, struktur, które zawierają ciągi i tablicy jest przekazywany przez wartość.|[Tablice](marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Zobacz także
- [Marshaling danych w wywołaniu platformy](marshaling-data-with-platform-invoke.md)
- [Typy danych w wywołaniu platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))
- [Marshaling klas, struktur i unii](marshaling-classes-structures-and-unions.md)
- [Organizowanie tablic typów](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))
- [Różne przykłady organizowania](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))
