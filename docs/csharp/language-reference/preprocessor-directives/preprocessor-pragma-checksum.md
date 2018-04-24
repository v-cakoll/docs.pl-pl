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
Generuje sumy kontrolne dla plików źródłowych, aby pomóc w debugowaniu stron [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]. 
  
## <a name="syntax"></a>Składnia  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### <a name="parameters"></a>Parametry  
 `"filename"`  
 Nazwa pliku, który wymaga monitorowania zmian lub aktualizacji.  
  
 `"{guid}"`  
 Globalnie unikatowy identyfikator (GUID) dla pliku.  
  
 `"checksum_bytes"`  
Ciąg cyfr szesnastkowych reprezentujący liczbę bajtów sumy kontrolnej. Musi być parzystą liczbą cyfr szesnastkowych. Nieparzysta liczba cyfr powoduje wygenerowanie ostrzeżenia podczas kompilacji i zignorowanie dyrektywy. 
  
## <a name="remarks"></a>Uwagi  
 Debuger programu Visual Studio używa sumy kontrolnej do sprawdzania, czy użyte zostało prawidłowe źródło. Kompilator oblicza sumę kontrolną pliku źródłowego, a następnie przesyła dane wyjściowe do pliku bazy danych programu (PDB). Następnie debuger używa pliku PDB do porównania sumy kontrolnej obliczanej dla pliku źródłowego.
  
 To rozwiązanie nie działa w przypadku projektów [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)], ponieważ obliczana suma kontrolna jest przeznaczona dla wygenerowanego pliku źródłowego, a nie pliku aspx. Aby rozwiązać ten problem, dyrektywa `#pragma checksum` zapewnia obsługę sumy kontrolnej dla stron [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].
  
 Po utworzeniu projektu [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] w języku [!INCLUDE[csprcs](~/includes/csprcs-md.md)], wygenerowany plik źródłowy zawiera sumę kontrolną dla pliku aspx, z którego jest generowany. Następnie kompilator zapisuje te informacje w pliku PDB. 
  
 Jeśli kompilator nie napotka w pliku dyrektywy `#pragma checksum`, oblicza jego sumę kontrolną i zapisuje jej wartość w pliku PDB.
  
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
