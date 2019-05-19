---
title: '#Suma kontrolna pragma - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 36e5602f0a0b872a4aa6cdac64b49b1d1c708795
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877526"
---
# <a name="pragma-checksum-c-reference"></a>#pragma checksum (odwołanie w C#)
Generuje sumy kontrolne dla plików źródłowych pomóc w debugowaniu strony ASP.NET.  
  
## <a name="syntax"></a>Składnia  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a>Parametry  
 `"filename"`  
 Nazwa pliku który wymaga monitorowania w celu zmiany lub aktualizacji.  
  
 `"{guid}"`  
 Globalnie unikatowy identyfikator (GUID) dla algorytmu wyznaczania wartości skrótu.  
  
 `"checksum_bytes"`  
 Ciąg cyfr szesnastkowych reprezentujący liczbę bajtów sumy kontrolnej. Musi być parzystą liczbą cyfr szesnastkowych. Nieparzysta liczba cyfr powoduje ostrzeżenie kompilacji i dyrektywy są ignorowane.  
  
## <a name="remarks"></a>Uwagi  
 Debuger programu Visual Studio używa sumy kontrolnej do sprawdzania, czy użyte zostało prawidłowe źródło. Kompilator oblicza sumę kontrolną pliku źródłowego, a następnie przesyła dane wyjściowe do pliku bazy danych programu (PDB). Następnie debuger używa pliku PDB do porównania sumy kontrolnej obliczanej dla pliku źródłowego.  
  
 To rozwiązanie nie działa dla projektów platformy ASP.NET, ponieważ obliczona suma kontrolna jest w wygenerowanym pliku źródłowym, a nie pliku aspx. Aby rozwiązać ten problem, `#pragma checksum` zapewnia obsługę sumy kontrolnej dla stron ASP.NET.  
  
 Po utworzeniu projektu programu ASP.NET w elemencie wizualnym C#, wygenerowanym pliku źródłowym zawiera sumę kontrolną dla pliku .aspx, z którego jest generowany źródła. Następnie kompilator zapisuje te informacje w pliku PDB.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)
