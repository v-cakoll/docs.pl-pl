---
title: '#pragma suma kontrolna - C# Odwołanie'
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 1bbb404e1183daa5e68e512e7439b6ae52abd605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712484"
---
# <a name="pragma-checksum-c-reference"></a>#pragma checksum (odwołanie w C#)
Generuje sumy kontrolne dla plików źródłowych, aby ułatwić debugowanie ASP.NET stron.  
  
## <a name="syntax"></a>Składnia  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a>Parametry  
 `"filename"`  
 Nazwa pliku, który wymaga monitorowania zmian lub aktualizacji.  
  
 `"{guid}"`  
 Globalnie unikatowy identyfikator (GUID) dla algorytmu mieszania.  
  
 `"checksum_bytes"`  
 Ciąg cyfr szesnastkowych reprezentujących bajty sumy kontrolnej. Musi być parzysta liczba cyfr szesnastkowych. Nieparzysta liczba cyfr powoduje ostrzeżenie w czasie kompilacji, a dyrektywa jest ignorowana.  
  
## <a name="remarks"></a>Uwagi  
 Debuger programu Visual Studio używa sumy kontrolnej, aby upewnić się, że zawsze znajdzie odpowiednie źródło. Kompilator oblicza sumę kontrolną dla pliku źródłowego, a następnie emituje dane wyjściowe do pliku bazy danych programu (PDB). Debuger następnie używa PDB do porównania z sumą kontrolną, która oblicza dla pliku źródłowego.  
  
 To rozwiązanie nie działa w przypadku projektów ASP.NET, ponieważ obliczona suma kontrolna jest dla wygenerowanego pliku źródłowego, a nie pliku .aspx. Aby rozwiązać ten `#pragma checksum` problem, zapewnia obsługę sumy kontrolnej dla ASP.NET stron.  
  
 Podczas tworzenia projektu ASP.NET w języku Visual C#, wygenerowany plik źródłowy zawiera sumę kontrolną dla pliku .aspx, z którego generowane jest źródło. Kompilator następnie zapisuje te informacje w pliku PDB.  
  
 Jeśli kompilator `#pragma checksum` nie napotka żadnej dyrektywy w pliku, oblicza sumę kontrolną i zapisuje wartość do pliku PDB.  
  
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

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Dyrektywy przedprocesorowe C#](./index.md)
