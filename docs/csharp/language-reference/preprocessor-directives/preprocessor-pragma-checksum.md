---
title: '#Suma kontrolna pragma (odwołanie w C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 37e06d97b082ba6de75d8efa81723442403e39be
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="pragma-checksum-c-reference"></a>#pragma checksum (odwołanie w C#)
Generuje sumy kontrolne dla plików źródłowych, aby pomóc w debugowaniu stron [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### <a name="parameters"></a>Parametry  
 `"filename"`  
 Nazwa pliku, który wymaga monitorowania na zmiany lub aktualizacji.  
  
 `"{guid}"`  
 Globalnie unikatowy identyfikator (GUID) dla algorytmu wyznaczania wartości skrótu.  
  
 `"checksum_bytes"`  
 Ciąg cyfr szesnastkowych reprezentujący liczbę bajtów sumy kontrolnej. Musi być parzystą liczbą cyfr szesnastkowych. Nieparzysta liczba cyfr powoduje ostrzeżenie kompilacji i dyrektywy są ignorowane.  
  
## <a name="remarks"></a>Uwagi  
 Debuger programu Visual Studio używa sumy kontrolnej do sprawdzania, czy użyte zostało prawidłowe źródło. Kompilator oblicza sumę kontrolną pliku źródłowego, a następnie przesyła dane wyjściowe do pliku bazy danych programu (PDB). Następnie debuger używa pliku PDB do porównania sumy kontrolnej obliczanej dla pliku źródłowego.  
  
 To rozwiązanie nie działa w przypadku projektów [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)], ponieważ obliczana suma kontrolna jest przeznaczona dla wygenerowanego pliku źródłowego, a nie pliku aspx.  Aby rozwiązać ten problem, dyrektywa `#pragma checksum` zapewnia obsługę sumy kontrolnej dla stron [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].  
  
 Po utworzeniu [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] sumy kontrolnej dla plików .aspx, z której źródłem jest generowany zawiera projekt języka Visual C#, wygenerowanym pliku źródłowym. Następnie kompilator zapisuje te informacje w pliku PDB.  
  
 Jeśli kompilator nie napotka w pliku dyrektywy `#pragma checksum`, oblicza jego sumę kontrolną i zapisuje jej wartość w pliku PDB.  
  
## <a name="example"></a>Przykład  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)
