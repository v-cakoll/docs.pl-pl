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
ms.openlocfilehash: 52a78e0c3969e879bf2fd1b1f5c41b2caac2ba11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391124"
---
# <a name="marshaling-strings"></a>Marshaling ciągów
Wywołanie platformy parametrów ciągu kopie, konwersję z formatu .NET Framework (Unicode) do formatu niezarządzane (ANSI), jeśli to konieczne. Ponieważ ciągi zarządzane są niezmienne, wywołanie platformy nie kopiuje je ponownie w pamięci niezarządzanej pamięci zarządzanej po powrocie z funkcji.  
  
 Poniższej tabeli wymieniono opcje marshaling dla ciągów, w tym artykule opisano sposób ich użycia i Link do odpowiedniego próbki .NET Framework.  
  
|String|Opis|Przykład|  
|------------|-----------------|------------|  
|Według wartości.|Przekazuje ciągów, tak jak parametry.|[MsgBox](msgbox-sample.md)|  
|W wyniku.|Zwraca ciągów z kodem niezarządzanym.|[Ciągi](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))|  
|Przez odwołanie.|Przekazuje ciągi jako We/Wy przy użyciu parametrów <xref:System.Text.StringBuilder>.|[Buforów](https://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100))|  
|W strukturze przez wartość.|Przekazuje ciągów w strukturze jest parametrem In.|[Struktury](https://msdn.microsoft.com/library/96a62265-dcf9-4608-bc0a-1f762ab9f48e(v=vs.100))|  
|W strukturze przez odwołanie **(char\*)**.|Przekazuje ciągów w strukturze jest parametrem we/wy. Funkcji niezarządzanej oczekuje wskaźnika do buforu znaków, a rozmiar buforu jest elementem członkowskim struktury.|[Ciągi](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))|  
|W strukturze przez odwołanie **(char[])**.|Przekazuje ciągów w strukturze jest parametrem we/wy. Funkcji niezarządzanej oczekuje bufor osadzonych znaków.|[OSInfo](https://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455(v=vs.100))|  
|W klasie przez wartość **(char\*)**.|Przekazuje ciągów w klasie (klasa jest parametrem We/Wy). Funkcji niezarządzanej oczekuje wskaźnika do buforu znaków.|[OpenFileDlg](https://msdn.microsoft.com/library/b7dea792-cb92-4baf-ac7b-6a24803e6c75(v=vs.100))|  
|W klasie przez wartość **(char[])**.|Przekazuje ciągów w klasie (klasa jest parametrem We/Wy). Funkcji niezarządzanej oczekuje bufor osadzonych znaków.|[OSInfo](https://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455(v=vs.100))|  
|Jako tablica ciągów przez wartość.|Tworzy tablicę ciągów, która jest przekazywany przez wartość.|[Tablice](marshaling-different-types-of-arrays.md)|  
|Jako tablica struktury zawierające ciągi przez wartość.|Tworzy tablicę struktur, które zawierają ciągi i tablicy jest przekazywany przez wartość.|[Tablice](marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Zobacz też  
 [Marshaling danych w wywołaniu platformy](marshaling-data-with-platform-invoke.md)  
 [Typy danych wywołanie platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [Marshaling klas, struktur i unii](marshaling-classes-structures-and-unions.md)  
 [Organizowanie tablice typów](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))  
 [Dodatkowe przykłady Marshalingu](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))
