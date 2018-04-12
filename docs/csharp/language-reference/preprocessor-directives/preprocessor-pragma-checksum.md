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
ms.openlocfilehash: 0604a559be25c300fcdc6041975306b465fc595f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-checksum-c-reference"></a>#pragma checksum (odwołanie w C#)
Generuje sumy kontrolne dla plików źródłowych pomóc w debugowaniu [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] stron.  
  
## <a name="syntax"></a>Składnia  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### <a name="parameters"></a>Parametry  
 `"filename"`  
 Nazwa pliku, który wymaga monitorowania na zmiany lub aktualizacji.  
  
 `"{guid}"`  
 Globalnie unikatowy identyfikator (GUID) dla pliku.  
  
 `"checksum_bytes"`  
 Ciąg reprezentujący liczbę bajtów sumy kontrolnej cyfr szesnastkowych. Musi być parzysta liczba cyfr szesnastkowych. Nieparzysta liczba cyfr powoduje ostrzeżenie kompilacji i dyrektywy są ignorowane.  
  
## <a name="remarks"></a>Uwagi  
 Debuger programu Visual Studio korzysta z sumy kontrolnej, upewnij się, że zawsze znajdzie prawo źródła. Kompilator oblicza sumę kontrolną pliku źródłowego, a następnie emituje dane wyjściowe do pliku programu (PDB) bazy danych. Debuger używa pliku PDB Aby porównać sumę kontrolną, która oblicza dla pliku źródłowego.  
  
 To rozwiązanie nie działa w przypadku [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projektów, ponieważ jest obliczana sumy kontrolnej wygenerowanym pliku źródłowym, a nie plik .aspx. Aby rozwiązać ten problem, `#pragma checksum` zapewnia obsługę sumy kontrolnej [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] stron.  
  
 Po utworzeniu [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projektu w [!INCLUDE[csprcs](~/includes/csprcs-md.md)], wygenerowanym pliku źródłowym zawiera sumę kontrolną dla plików .aspx, z którego jest generowany źródła. Kompilator następnie zapisuje te informacje w pliku PDB.  
  
 Jeśli nie wystąpi kompilator `#pragma checksum` dyrektywy w pliku, jego oblicza sumę kontrolną i zapisuje wartość w pliku PDB.  
  
## <a name="example"></a>Przykład  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{3673e4ca-6098-4ec1-890f-8fceb2a794a2}" "{012345678AB}" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)
