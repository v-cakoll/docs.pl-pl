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
ms.openlocfilehash: 88b6342038f99bf06fa2986c43f422e63cffd31e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124379"
---
# <a name="marshaling-strings"></a>Organizowanie ciągów
Wywołanie platformy kopiuje parametry ciągu, konwertując je z formatu .NET Framework (Unicode) do formatu niezarządzanego (ANSI), w razie potrzeby. Ponieważ ciągi zarządzane są niezmienne, wywołanie platformy nie kopiuje ich z niezarządzanej pamięci do pamięci zarządzanej, gdy funkcja zwraca wartość.  
  
 W poniższej tabeli wymieniono opcje organizowania ciągów, opisuje ich użycie i zawiera link do odpowiedniego przykładu .NET Framework.  
  
|String|Opis|Przykład|  
|------------|-----------------|------------|  
|Według wartości.|Przekazuje ciągi jako parametry.|[MsgBox](msgbox-sample.md)|  
|W wyniku.|Zwraca ciągi z kodu niezarządzanego.|[Ciągi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|Przez odwołanie.|Przekazuje ciągi jako parametry wejściowe/out przy użyciu <xref:System.Text.StringBuilder>.|[Ręczny](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100))|  
|W strukturze według wartości.|Przekazuje ciągi w strukturze, która jest parametrem in.|[Struktury](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100))|  
|W strukturze przez odwołanie **(char\*)** .|Przekazuje ciągi w strukturze, która jest parametrem in/out. Funkcja niezarządzana oczekuje wskaźnika do buforu znaków, a rozmiar buforu to element członkowski struktury.|[Ciągi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|W strukturze przez odwołanie **(Char [])** .|Przekazuje ciągi w strukturze, która jest parametrem in/out. Funkcja niezarządzana oczekuje osadzonego buforu znaków.|[OSInfo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|W klasie według wartości **(char\*)** .|Przekazuje ciągi w klasie (Klasa jest parametrem typu "in/out"). Funkcja niezarządzana oczekuje wskaźnika do buforu znaków.|[Openfiledlg —](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w5tyztk9(v=vs.100))|  
|W klasie według wartości **(Char [])** .|Przekazuje ciągi w klasie (Klasa jest parametrem typu "in/out"). Funkcja niezarządzana oczekuje osadzonego buforu znaków.|[OSInfo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|Jako tablica ciągów według wartości.|Tworzy tablicę ciągów, która jest przenoszona przez wartość.|[Tablice](marshaling-different-types-of-arrays.md)|  
|Jako tablicę struktur, które zawierają ciągi według wartości.|Tworzy tablicę struktur, które zawierają ciągi, a tablica jest przenoszona przez wartość.|[Tablice](marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Zobacz także

- [Domyślny marshaling dla ciągów](default-marshaling-for-strings.md)
- [Marshaling danych w wywołaniu platformy](marshaling-data-with-platform-invoke.md)
- [Marshaling klas, struktur i unii](marshaling-classes-structures-and-unions.md)
- [Organizowanie różnych typów tablic](marshaling-different-types-of-arrays.md)
- [Różne przykłady organizowania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))
