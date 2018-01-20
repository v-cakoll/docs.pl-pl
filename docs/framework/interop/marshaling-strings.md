---
title: "Marshaling ciągów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4d53cd4072ab3f9ff52729f122c0a0ecab400df
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="marshaling-strings"></a>Marshaling ciągów
Wywołanie platformy parametrów ciągu kopie, konwersję z formatu .NET Framework (Unicode) do formatu niezarządzane (ANSI), jeśli to konieczne. Ponieważ ciągi zarządzane są niezmienne, wywołanie platformy nie kopiuje je ponownie w pamięci niezarządzanej pamięci zarządzanej po powrocie z funkcji.  
  
 Poniższej tabeli wymieniono opcje marshaling dla ciągów, w tym artykule opisano sposób ich użycia i Link do odpowiedniego próbki .NET Framework.  
  
|String|Opis|Przykład|  
|------------|-----------------|------------|  
|Według wartości.|Przekazuje ciągów, tak jak parametry.|[MsgBox](../../../docs/framework/interop/msgbox-sample.md)|  
|W wyniku.|Zwraca ciągów z kodem niezarządzanym.|[Ciągi](http://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|Przez odwołanie.|Przekazuje ciągi jako We/Wy przy użyciu parametrów <xref:System.Text.StringBuilder>.|[Buforów](http://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5)|  
|W strukturze przez wartość.|Przekazuje ciągów w strukturze jest parametrem In.|[Struktury](http://msdn.microsoft.com/library/96a62265-dcf9-4608-bc0a-1f762ab9f48e)|  
|W strukturze przez odwołanie **(char\*)**.|Przekazuje ciągów w strukturze jest parametrem we/wy. Funkcji niezarządzanej oczekuje wskaźnika do buforu znaków, a rozmiar buforu jest elementem członkowskim struktury.|[Ciągi](http://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|W strukturze przez odwołanie **(char[])**.|Przekazuje ciągów w strukturze jest parametrem we/wy. Funkcji niezarządzanej oczekuje bufor osadzonych znaków.|[OSInfo](http://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455)|  
|W klasie przez wartość **(char\*)**.|Przekazuje ciągów w klasie (klasa jest parametrem We/Wy). Funkcji niezarządzanej oczekuje wskaźnika do buforu znaków.|[OpenFileDlg](http://msdn.microsoft.com/library/b7dea792-cb92-4baf-ac7b-6a24803e6c75)|  
|W klasie przez wartość **(char[])**.|Przekazuje ciągów w klasie (klasa jest parametrem We/Wy). Funkcji niezarządzanej oczekuje bufor osadzonych znaków.|[OSInfo](http://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455)|  
|Jako tablica ciągów przez wartość.|Tworzy tablicę ciągów, która jest przekazywany przez wartość.|[Tablice](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
|Jako tablica struktury zawierające ciągi przez wartość.|Tworzy tablicę struktur, które zawierają ciągi i tablicy jest przekazywany przez wartość.|[Tablice](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Zobacz też  
 [Marshaling danych w wywołaniu platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 [Typy danych wywołanie platformy](http://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [Marshaling klas, struktur i unii](../../../docs/framework/interop/marshaling-classes-structures-and-unions.md)  
 [Organizowanie tablice typów](http://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)  
 [Dodatkowe przykłady Marshalingu](http://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70)
