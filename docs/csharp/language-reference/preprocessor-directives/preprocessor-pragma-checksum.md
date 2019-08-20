---
title: '#pragma — C# odwołanie'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 4103b6262fc5085c1204f423a36c9c5c2053b497
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605648"
---
# <a name="pragma-checksum-c-reference"></a>#pragma checksum (odwołanie w C#)
Generuje sumy kontrolne dla plików źródłowych, aby pomóc w debugowaniu stron ASP.NET.  
  
## <a name="syntax"></a>Składnia  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a>Parametry  
 `"filename"`  
 Nazwa pliku, który wymaga monitorowania pod kątem zmian lub aktualizacji.  
  
 `"{guid}"`  
 Unikatowy identyfikator globalny (GUID) algorytmu wyznaczania wartości skrótu.  
  
 `"checksum_bytes"`  
 Ciąg cyfr szesnastkowych reprezentujący liczbę bajtów sumy kontrolnej. Musi być parzystą liczbą cyfr szesnastkowych. Nieparzysta liczba cyfr skutkuje ostrzeżeniem w czasie kompilacji, a dyrektywa jest ignorowana.  
  
## <a name="remarks"></a>Uwagi  
 Debuger programu Visual Studio używa sumy kontrolnej do sprawdzania, czy użyte zostało prawidłowe źródło. Kompilator oblicza sumę kontrolną pliku źródłowego, a następnie przesyła dane wyjściowe do pliku bazy danych programu (PDB). Następnie debuger używa pliku PDB do porównania sumy kontrolnej obliczanej dla pliku źródłowego.  
  
 To rozwiązanie nie działa w przypadku projektów ASP.NET, ponieważ obliczona suma kontrolna jest dla wygenerowanego pliku źródłowego, a nie pliku. aspx. Aby rozwiązać ten problem, `#pragma checksum` program zapewnia obsługę sum kontrolnych dla stron ASP.NET.  
  
 Podczas tworzenia projektu ASP.NET w wizualizacji C#wygenerowany plik źródłowy zawiera sumę kontrolną dla pliku. aspx, z którego jest generowane źródło. Następnie kompilator zapisuje te informacje w pliku PDB.  
  
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

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Dyrektywy preprocesora C#](./index.md)
