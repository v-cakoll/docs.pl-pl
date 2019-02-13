---
title: Organizowanie ciągów
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
ms.openlocfilehash: 4640d37ad6c30746e203c26c2c1cd71eb70e7579
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56218570"
---
# <a name="marshaling-strings"></a>Organizowanie ciągów
Wywołanie platformy parametry ciągu kopii, konwersję z formatu .NET Framework (Unicode) do formatu niezarządzane (ANSI), jeśli to konieczne. Ponieważ ciągi zarządzane są niezmienne, wywołanie platformy nie kopiuje ich powrót po awarii z niezarządzanej pamięci do pamięci zarządzanej, gdy funkcja zwraca.  
  
 Poniższej tabeli wymieniono opcje marshaling dla ciągów, w tym artykule opisano ich użycie i Link do odpowiedniego przykładowe .NET Framework.  
  
|String|Opis|Przykład|  
|------------|-----------------|------------|  
|Według wartości.|Przekazuje parametry, tak jak parametry.|[MsgBox](msgbox-sample.md)|  
|W wyniku.|Zwraca ciągi z niezarządzanego kodu.|[Ciągi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|Przez odwołanie.|Przekazuje ciągi jako We/Wy przy użyciu parametrów <xref:System.Text.StringBuilder>.|[Bufory](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100))|  
|W strukturze przez wartość.|Przekazuje parametry to struktura, która jest parametrem In.|[Struktury](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100))|  
|W strukturze przez odwołanie **(char\*)**.|Przekazuje parametry to struktura, która jest parametrem we/wy. Niezarządzanej funkcji oczekuje wskaźnika do buforu znaków i rozmiar buforu jest elementem członkowskim struktury.|[Ciągi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|W strukturze przez odwołanie **(char[])**.|Przekazuje parametry to struktura, która jest parametrem we/wy. Niezarządzanej funkcji oczekuje osadzonego buforu znaku.|[OSInfo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|W klasie według wartości **(char\*)**.|Przekazuje parametry w klasie (klasy jest parametrem We/Wy). Niezarządzanej funkcji oczekuje wskaźnika do buforu znaków.|[OpenFileDlg](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w5tyztk9(v=vs.100))|  
|W klasie według wartości **(char[])**.|Przekazuje parametry w klasie (klasy jest parametrem We/Wy). Niezarządzanej funkcji oczekuje osadzonego buforu znaku.|[OSInfo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|Jako tablicę ciągów według wartości.|Tworzy tablicę ciągów, który jest przekazywany przez wartość.|[Tablice](marshaling-different-types-of-arrays.md)|  
|Jako tablica struktur, które zawierają ciągi według wartości.|Tworzy tablicę, struktur, które zawierają ciągi i tablicy jest przekazywany przez wartość.|[Tablice](marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Zobacz także
- [Marshaling danych w wywołaniu platformy](marshaling-data-with-platform-invoke.md)
- [Marshaling klas, struktur i unii](marshaling-classes-structures-and-unions.md)
- [Organizowanie różnych typów tablic](marshaling-different-types-of-arrays.md)
- [Różne przykłady organizowania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))
